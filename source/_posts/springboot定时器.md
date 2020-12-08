---
title: springboot定时器
date: 2018-09-18 16:04:57
tags:
    - 定时器
    - springboot
    - Java
categories:
	- springboot
---
<center>![](schedule-web-orig_orig.png)</center>
#### 描述
在日常的项目开发过程中会遇到各种使用定时任务的需求，实现定时任务需求的方式也是多种多样。

* Quartz     
Quartz的使用相当广泛，它是一个功能强大的调度器，但是使用起来会非常繁琐
* Timer    
java.util包里的Timer，它同样也可以实现定时任务，但是功能过于单一
* Schedule     
Schedule是spring自带的定时任务组件,可以把它看成一个轻量级、简化版的Quartz
    
#### 实现定时任务
##### 开启定时任务

```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.scheduling.annotation.EnableScheduling;

/**
 * @author wangjunfeng
 * @date 2018-09-13
 */
@SpringBootApplication
@EnableScheduling
public class TimerApplication {

    public static void main(String[] args) {
        SpringApplication.run(TimerApplication.class, args);
    }
}
```
##### 单线程

```java
import com.kiwi.timer.util.DateTimeUtil;
import lombok.extern.log4j.Log4j2;
import org.springframework.scheduling.annotation.Scheduled;
import org.springframework.stereotype.Component;

import java.util.Date;

/**
 * 单线程定时器demo
 *
 * @author wangjunfeng
 * @date 2018-09-13
 */
@Log4j2
@Component
public class SingleDemo {
    public final static long ONE_Minute = 60 * 1000;

    @Scheduled(fixedDelay = ONE_Minute)
    public void fixedDelayJob() {
        log.info(DateTimeUtil.toDateTimeStr(new Date()) + " >>fixedDelay执行....");
    }

    @Scheduled(fixedRate = ONE_Minute)
    public void fixedRateJob() {
        log.info(DateTimeUtil.toDateTimeStr(new Date()) + " >>fixedRate执行....");
    }

    @Scheduled(cron = "0/5 * * * * ?")
    public void cronJob() {
        log.info("----" + DateTimeUtil.toDateTimeStr(new Date()) + " >>cron执行....");
    }
}
```



```log
s.a.ScheduledAnnotationBeanPostProcessor : No TaskScheduler/ScheduledExecutorService bean found for scheduled processing
2018-09-18 16:25:47.279  INFO 23151 --- [pool-1-thread-1] com.kiwi.timer.single.SingleDemo         : 2018-09-18 16:25:47 >>fixedRate执行....
2018-09-18 16:25:47.280  INFO 23151 --- [pool-1-thread-1] com.kiwi.timer.single.SingleDemo         : 2018-09-18 16:25:47 >>fixedDelay执行....
2018-09-18 16:25:47.324  INFO 23151 --- [           main] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat started on port(s): 8080 (http) with context path ''
2018-09-18 16:25:47.331  INFO 23151 --- [           main] com.kiwi.timer.TimerApplication          : Started TimerApplication in 3.646 seconds (JVM running for 4.643)
2018-09-18 16:25:50.006  INFO 23151 --- [pool-1-thread-1] com.kiwi.timer.single.SingleDemo         : ----2018-09-18 16:25:50 >>cron执行....

```
从上述控制台日志可以看出所有的定时任务都是由同一个线程来处理的，当定时任务过多的时候会造成任务队列的堆积

##### 多线程
```java
import lombok.extern.log4j.Log4j2;
import org.springframework.aop.interceptor.AsyncUncaughtExceptionHandler;
import org.springframework.aop.interceptor.SimpleAsyncUncaughtExceptionHandler;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.scheduling.TaskScheduler;
import org.springframework.scheduling.annotation.AsyncConfigurer;
import org.springframework.scheduling.annotation.EnableAsync;
import org.springframework.scheduling.annotation.SchedulingConfigurer;
import org.springframework.scheduling.concurrent.ThreadPoolTaskScheduler;
import org.springframework.scheduling.config.ScheduledTaskRegistrar;

import java.util.concurrent.Executor;

/**
 *
 */
@Configuration
@EnableAsync
@Log4j2
public class MultiConfig implements SchedulingConfigurer, AsyncConfigurer {
    @Override
    public void configureTasks(ScheduledTaskRegistrar scheduledTaskRegistrar) {
        TaskScheduler taskScheduler = taskScheduler();
        scheduledTaskRegistrar.setTaskScheduler(taskScheduler);
    }

    @Bean(destroyMethod = "shutdown")
    public ThreadPoolTaskScheduler taskScheduler() {
        ThreadPoolTaskScheduler scheduler = new ThreadPoolTaskScheduler();
        scheduler.setPoolSize(20);
        // 设置线程名前缀
        scheduler.setThreadNamePrefix("multiTask-");
        // 线程内容执行完后60秒停在
        scheduler.setAwaitTerminationSeconds(60);
        // 等待所有线程执行完
        scheduler.setWaitForTasksToCompleteOnShutdown(true);
        return scheduler;
    }

    @Override
    public Executor getAsyncExecutor() {
        Executor executor = taskScheduler();
        return executor;
    }

    @Override
    public AsyncUncaughtExceptionHandler getAsyncUncaughtExceptionHandler() {
        return new SimpleAsyncUncaughtExceptionHandler();
    }
}
```

```log
2018-09-18 16:33:15.219  INFO 23197 --- [    multiTask-1] com.kiwi.timer.single.SingleDemo         : 2018-09-18 16:33:15 >>fixedRate执行....
2018-09-18 16:33:15.219  INFO 23197 --- [    multiTask-2] com.kiwi.timer.single.SingleDemo         : 2018-09-18 16:33:15 >>fixedDelay执行....
2018-09-18 16:33:15.247  INFO 23197 --- [           main] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat started on port(s): 8080 (http) with context path ''
2018-09-18 16:33:15.251  INFO 23197 --- [           main] com.kiwi.timer.TimerApplication          : Started TimerApplication in 2.313 seconds (JVM running for 3.046)
2018-09-18 16:33:20.001  INFO 23197 --- [    multiTask-3] com.kiwi.timer.single.SingleDemo         : ----2018-09-18 16:33:20 >>cron执行....
2018-09-18 16:33:25.001  INFO 23197 --- [    multiTask-2] com.kiwi.timer.single.SingleDemo         : ----2018-09-18 16:33:25 >>cron执行....
```
从上述日志可以看出已有线程池中的多个线程来实现定时任务

参考资料

* [github示例代码](https://github.com/junfengwang11/timer)
* [Cron表达式详解](https://www.jianshu.com/p/f03b1497122a)
* [SpringBoot定时器#Schedule](https://blog.csdn.net/qq_28988969/article/details/78250357)






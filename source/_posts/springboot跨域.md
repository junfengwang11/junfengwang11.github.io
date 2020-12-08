---
title: springboot跨域
date: 2019-03-25 14:21:39
tags:
    - Java
    - springboot
categories:
    - springboot
    - Java
---
<center>![cross](cross.jpg)</center>
#### 什么是跨域
跨域，按照字面意思是跨到了另外的域；域不仅指的是不同的域名网站，也可以是同一个域名不同的端口号也算不同的域；以浏览器的角度来看，只要协议、域名、端口有任何一个不同，都被当作是不同的域。
#### CORS
cors全称是`Cross-Origin Resource Sharing`,`跨域资源共享`，这是浏览器的标准，基本上现在市面上的浏览器都支持。
#### 跨域支持
目前有两种主流的跨域支持方式，一种是在反向代理层配置（如nginx），另一种是直接在后端（如Java）代码中支持。关于nginx层面的反向代理层配置详见[Nginx配置跨域请求 Access-Control-Allow-Origin *](https://segmentfault.com/a/1190000012550346)，本文章主要介绍在后端如何配置对跨域的支持，代码如下
```java
import org.springframework.boot.web.servlet.FilterRegistrationBean;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.web.cors.CorsConfiguration;
import org.springframework.web.cors.UrlBasedCorsConfigurationSource;
import org.springframework.web.filter.CorsFilter;

/**
 * 全局跨域设置
 *
 * @author wangjunfeng
 * @date 2019-03-21
 */
@Configuration
public class GlobalCorsConfig {
    @Bean
    public FilterRegistrationBean corsFilter() {
        UrlBasedCorsConfigurationSource source = new UrlBasedCorsConfigurationSource();
        CorsConfiguration corsConfiguration = new CorsConfiguration();
        corsConfiguration.setAllowCredentials(true);
        corsConfiguration.addAllowedHeader("origin");
        corsConfiguration.addAllowedHeader("content-type");
        corsConfiguration.addAllowedHeader("token");
        corsConfiguration.addAllowedHeader("text/plain charset=UTF-8");
        corsConfiguration.addAllowedOrigin("*");
        corsConfiguration.addAllowedMethod("POST");
        corsConfiguration.addAllowedMethod("GET");
        corsConfiguration.addAllowedMethod("OPTIONS");
        corsConfiguration.addAllowedMethod("DELETE");
        corsConfiguration.addAllowedMethod("PUT");
        corsConfiguration.addAllowedMethod("HEAD");
        corsConfiguration.addAllowedMethod("TRACE");
        corsConfiguration.addAllowedMethod("PATCH");
        source.registerCorsConfiguration("/**", corsConfiguration);
        FilterRegistrationBean bean = new FilterRegistrationBean(new CorsFilter(source));
        // 这个顺序很重要哦，为避免麻烦请设置在最前
        bean.setOrder(0);
        return bean;
    }
}
```


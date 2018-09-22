# layering-cache
# 简介

[![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.github.xiaolyuh/layering-cache/badge.svg)](https://search.maven.org/artifact/com.github.xiaolyuh/layering-cache/)
[![License](https://img.shields.io/badge/license-Apache%202-4EB1BA.svg)](https://www.apache.org/licenses/LICENSE-2.0.html)

layering-cache是在Spring Cache基础上扩展而来的一个缓存框架，主要目的是在使用注解的时候支持配置过期时间。layering-cache其实是一个两级缓存，一级缓存使用Caffeine作为本地缓存，二级缓存使用redis作为集中式缓存。并且基于redis的Pub/Sub做缓存的删除，所以它是一个适用于分布式环境下的一个缓存系统。

# 支持
- 支持缓存监控统计
- 支持缓存过期时间在注解上直接配置
- 支持二级缓存的自动刷新（当缓存命中并发现缓存将要过期时会开启一个异步线程刷新缓存）
- 刷新缓存分为强刷新和软刷新，强刷新直接调用缓存方法，软刷新直接改缓存的时间 
- 缓存Key支持SpEL表达式
- 新增FastJsonRedisSerializer，KryoRedisSerializer序列化，重写String序列化。
- 支持同一个缓存名称设置不同的过期时间

# 文档

[中文文档](https://github.com/xiaolyuh/layering-cache/wiki/%E6%B3%A8%E8%A7%A3%E6%96%87%E6%A1%A3)
# 打开监控统计功能

[打开监控统计功能](https://github.com/xiaolyuh/layering-cache/wiki/%E6%89%93%E5%BC%80%E7%9B%91%E6%8E%A7%E7%BB%9F%E8%AE%A1%E5%8A%9F%E8%83%BD)
# 打开内置的监控页面

[打开内置的监控页面](https://github.com/xiaolyuh/layering-cache/wiki/%E6%89%93%E5%BC%80%E5%86%85%E7%BD%AE%E7%9A%84%E7%9B%91%E6%8E%A7%E9%A1%B5%E9%9D%A2)

# 更新日志

[更新日志](https://github.com/xiaolyuh/layering-cache/wiki/%E6%9B%B4%E6%96%B0%E6%97%A5%E5%BF%97)

# 重要提示
- layering-cache支持同一个缓存名称设置不同的过期时间，但是一定要保证key唯一，否则会出现缓存过期时间错乱的情况
- 删除缓存的时候会将同一个缓存名称的不同的过期时间的缓存都删掉
- 在集成layering-cache之前还需要添加以下的依赖，主要是为了减少jar包冲突。
```xml  
<dependency>
	<groupId>org.springframework.data</groupId>
	<artifactId>spring-data-redis</artifactId>
	<version>1.8.3.RELEASE</version>
</dependency>

<dependency>
	<groupId>redis.clients</groupId>
	<artifactId>jedis</artifactId>
	<version>2.9.0</version>
</dependency>

<dependency>
	<groupId>org.springframework</groupId>
	<artifactId>spring-core</artifactId>
	<version>4.3.18.RELEASE</version>
</dependency>

<dependency>
	<groupId>org.springframework</groupId>
	<artifactId>spring-aop</artifactId>
	<version>4.3.18.RELEASE</version>
</dependency>

<dependency>
	<groupId>org.springframework</groupId>
	<artifactId>spring-context</artifactId>
	<version>4.3.18.RELEASE</version>
</dependency>

<dependency>
	<groupId>com.alibaba</groupId>
	<artifactId>fastjson</artifactId>
	<version>1.2.31</version>
</dependency>

<dependency>
	<groupId>com.esotericsoftware</groupId>
	<artifactId>kryo-shaded</artifactId>
	<version>3.0.3</version>
</dependency>

<dependency>
	<groupId>org.aspectj</groupId>
	<artifactId>aspectjweaver</artifactId>
	<version>1.8.10</version>
</dependency>
```  

# 实现原理
https://github.com/xiaolyuh/layering-cache/wiki

# 作者信息

作者博客：https://www.jianshu.com/u/4e6e80b98daa

作者邮箱： xiaolyuh@163.com  

github 地址：https://github.com/wyh-chenfeng/layering-cache


# 捐赠
项目的发展离不开你的支持，请作者喝杯咖啡吧！

![微信.png](https://upload-images.jianshu.io/upload_images/6464086-553feada56e87976.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![支付宝.png](https://upload-images.jianshu.io/upload_images/6464086-b5931fed21a137c6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![扫描领支付宝红包.png](https://upload-images.jianshu.io/upload_images/6464086-4c07fc47862dab24.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


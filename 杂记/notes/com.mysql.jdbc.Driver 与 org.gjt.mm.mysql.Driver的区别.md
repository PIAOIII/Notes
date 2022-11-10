[TOC]

# com.mysql.jdbc.Driver 与 org.gjt.mm.mysql.Driver的区别

在填写配置文件时：

```yml
spring:
  application:
    name: cloud-payment-service
    datasource:
      # 当前数据源操作类型
      type: com.alibaba.druid.pool.DruidDataSource
      # mysql驱动包 com.mysql.jdbc.Driver org.gjt.mm.mysql.Driver
      driver-class-name: org.gjt.mm.mysql.Driver
      url: jdbc:mysql://localhost:3306/cloud2020?useUnicode=true&characterEncoding=utf-8&useSSL=false
      username: root
      password: 1112
```

com.mysql.jdbc.Driver的前身是org.gjt.mm.mysql.Driver，现在主要用com.mysql.jdbc.Driver，但为了保持兼容性保留了org.gjt.mm.mysql.Driver这个路径的引用。
org.gjt.mm.mysql.Driver 是早期的驱动名称，后来就改名为com.mysql.jdbc.Driver，现在一般都推荐使用com.mysql.jdbc.Driver。
在某些版本的mysql jdbc驱动中，为了保持对老版本的兼容，仍然保留了org.gjt.mm.mysql.Driver，但是实际上 org.gjt.mm.mysql.Driver中调用了com.mysql.jdbc.Driver，因此现在这两个驱动没有什么区别。

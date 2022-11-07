[TOC]

## 版本说明

`spring boot` 使用数字对版本进行编号；
`Spring Cloud` 以前使用伦敦地铁站名按首字母顺序对版本进行编号。现在使用了全新的 “日历化” 版本命名方式

- SpringCloud是一个由许多子项目组成的综合项目，各子项目有不同的发布节奏。为了**管理SpringCloud与各子项目的版本依赖关系**，发布了一个**清单**，其中**包括了某个SpringCloud版本对应的子项目版本**。为了避免SpringCloud版本号与子项目版本号混淆，SpringCloud版本采用了名称而非版本号的命名，这些版本的名字采用了伦敦地铁站的名字，根据字母表的顺序来对应版本时间顺序。例如Angel是第一个版本, Brixton是第二个版本。

- 当SpringCloud的发布内容积累到临界点或者一个重大BUG被解决后，会发布一个"`service releases`"版本，简称**SRX版本**，比如Greenwich.SR2就是SpringCloud发布的Greenwich版本的第2个SRX版本。

- 从 Spring Cloud 2020.0.0-M1 开始，Spring Cloud将不再使用英国伦敦地铁站的命名方式，而使用了全新的 “日历化”（Calendar Versioning或简称CalVer） 版本命名方式。参见: https://spring.io/blog/2020/04/17/spring-cloud-2020-0-0-m1-released
- Spring Cloud版本号将使用了 YYYY.MINOR.MICRO 的命名规则，其中：
  - YYYY：代表4 位年份；
  - MINOR：表示一个每年以 0 开始递增的数字；
  - MICRO：表示版本号的后缀， .0 类似于 .RELEASE 一样，.2 类似于 .SR2。
- 预发布版本的后缀分隔符也由 `.` 变为 `-`，如：2020.0.0-M1 和 2020.0.0-RC2 命名所示。同时，Spring Cloud 将停止给快照版本添加 BUILD- 前缀，如：2020.0.0-SNAPSHOT 命名所示。
- 但是，英国伦敦地铁站的命名没有彻底废除，Spring Cloud 将继续使用它作为版本代号，当前代号：Ilford，只是发布到 Maven 仓库的版本将不再使用这些名称。
最后附上Maven和Gradle获取包方式对比：
    Maven获取旧版本：
    ```xml
    <dependency>
        <groupId>org.springframework.cloud</groupId>
        <artifactId>spring-cloud-dependencies</artifactId>
        <version>Hoxton.SR6</version>
        <type>pom</type>
        <scope>import</scope>
    </dependency>
    ```
    Maven获取新版本：
    ```xml
    <dependency>
        <groupId>org.springframework.cloud</groupId>
        <artifactId>spring-cloud-dependencies</artifactId>
        <version>2020.0 0-M2</version>
        <type>pom</type>
        <scope>import</scope>
    </dependency>
    ```

## Spring boot 与 Spring Cloud的制约关系与版本选择

### 查看各版本
Spring boot 官网:
- https://github.com/spring-projects/spring-boot/releases

Spring Cloud 官网:
- NEW: https://spring.io/projects/spring-cloud#overview
- OLD: https://github.com/spring-projects/spring-cloud/wiki

### Spring boot 与 Spring Cloud的制约关系
查看网址: https://spring.io/projects/spring-cloud
![图 5](../statics/SPringboot%E4%B8%8ESpring%20Cloud%E7%89%88%E6%9C%AC%E9%80%89%E6%8B%A9-Spring%20boot%20%E4%B8%8E%20Spring%20Cloud%E7%9A%84%E5%88%B6%E7%BA%A6%E5%85%B3%E7%B3%BB.png)  

#### 更详细的版本对应查看方法

网址: https://start.spring.io/actuator/info

![图 6](../statics/SPringboot%E4%B8%8ESpring%20Cloud%E7%89%88%E6%9C%AC%E9%80%89%E6%8B%A9-%E6%9B%B4%E8%AF%A6%E7%BB%86%E7%9A%84%E7%89%88%E6%9C%AC%E5%AF%B9%E5%BA%94%E6%9F%A5%E7%9C%8B%E6%96%B9%E6%B3%95.png)  

```json
{
  "git": {
    "branch": "f5360b578faa5e3530069e319097acbe5b609af8",
    "commit": {
      "id": "f5360b5",
      "time": "2022-11-01T16:47:02Z"
    }
  },
  "build": {
    "version": "0.0.1-SNAPSHOT",
    "artifact": "start-site",
    "versions": {
      "spring-boot": "2.7.5",
      "initializr": "0.13.0"
    },
    "name": "start.spring.io website",
    "time": "2022-11-01T16:50:14.056Z",
    "group": "io.spring.start"
  },
  "bom-ranges": {
    "codecentric-spring-boot-admin": {
      "2.4.3": "Spring Boot >=2.3.0.M1 and <2.5.0-M1",
      "2.5.6": "Spring Boot >=2.5.0.M1 and <2.6.0-M1",
      "2.6.8": "Spring Boot >=2.6.0.M1 and <2.7.0-M1",
      "2.7.4": "Spring Boot >=2.7.0.M1 and <3.0.0-M1",
      "3.0.0-M4": "Spring Boot >=3.0.0-M1 and <3.1.0-M1"
    },
    "solace-spring-boot": {
      "1.1.0": "Spring Boot >=2.3.0.M1 and <2.6.0-M1",
      "1.2.2": "Spring Boot >=2.6.0.M1 and <3.0.0-M1"
    },
    "solace-spring-cloud": {
      "1.1.1": "Spring Boot >=2.3.0.M1 and <2.4.0-M1",
      "2.1.0": "Spring Boot >=2.4.0.M1 and <2.6.0-M1",
      "2.3.2": "Spring Boot >=2.6.0.M1 and <3.0.0-M1"
    },
    "spring-cloud": {
      "Hoxton.SR12": "Spring Boot >=2.2.0.RELEASE and <2.4.0.M1",
      "2020.0.6": "Spring Boot >=2.4.0.M1 and <2.6.0-M1",
      "2021.0.0-M1": "Spring Boot >=2.6.0-M1 and <2.6.0-M3",
      "2021.0.0-M3": "Spring Boot >=2.6.0-M3 and <2.6.0-RC1",
      "2021.0.0-RC1": "Spring Boot >=2.6.0-RC1 and <2.6.1",
      "2021.0.4": "Spring Boot >=2.6.1 and <3.0.0-M1",
      "2022.0.0-M1": "Spring Boot >=3.0.0-M1 and <3.0.0-M2",
      "2022.0.0-M2": "Spring Boot >=3.0.0-M2 and <3.0.0-M3",
      "2022.0.0-M3": "Spring Boot >=3.0.0-M3 and <3.0.0-M4",
      "2022.0.0-M4": "Spring Boot >=3.0.0-M4 and <3.0.0-M5",
      "2022.0.0-M5": "Spring Boot >=3.0.0-M5 and <3.1.0-M1"
    },
    "spring-cloud-azure": {
      "4.3.0": "Spring Boot >=2.5.0.M1 and <2.7.0-M1",
      "4.4.1": "Spring Boot >=2.7.0-M1 and <3.0.0-M1"
    },
    "spring-cloud-gcp": {
      "2.0.11": "Spring Boot >=2.4.0-M1 and <2.6.0-M1",
      "3.4.0": "Spring Boot >=2.6.0-M1 and <3.0.0-M1"
    },
    "spring-cloud-services": {
      "2.3.0.RELEASE": "Spring Boot >=2.3.0.RELEASE and <2.4.0-M1",
      "2.4.1": "Spring Boot >=2.4.0-M1 and <2.5.0-M1",
      "3.3.0": "Spring Boot >=2.5.0-M1 and <2.6.0-M1",
      "3.4.0": "Spring Boot >=2.6.0-M1 and <2.7.0-M1",
      "3.5.0": "Spring Boot >=2.7.0-M1 and <3.0.0-M1"
    },
    "spring-geode": {
      "1.3.12.RELEASE": "Spring Boot >=2.3.0.M1 and <2.4.0-M1",
      "1.4.13": "Spring Boot >=2.4.0-M1 and <2.5.0-M1",
      "1.5.14": "Spring Boot >=2.5.0-M1 and <2.6.0-M1",
      "1.6.12": "Spring Boot >=2.6.0-M1 and <2.7.0-M1",
      "1.7.4": "Spring Boot >=2.7.0-M1 and <3.0.0-M1",
      "2.0.0-M5": "Spring Boot >=3.0.0-M1 and <3.1.0-M1"
    },
    "spring-shell": {
      "2.1.3": "Spring Boot >=2.7.0 and <3.0.0-M1",
      "3.0.0-M2": "Spring Boot >=3.0.0-M1 and <3.1.0-M1"
    },
    "vaadin": {
      "14.8.20": "Spring Boot >=2.1.0.RELEASE and <2.6.0-M1",
      "23.2.6": "Spring Boot >=2.6.0-M1 and <2.8.0-M1"
    },
    "wavefront": {
      "2.0.2": "Spring Boot >=2.1.0.RELEASE and <2.4.0-M1",
      "2.1.1": "Spring Boot >=2.4.0-M1 and <2.5.0-M1",
      "2.2.2": "Spring Boot >=2.5.0-M1 and <2.7.0-M1",
      "2.3.0": "Spring Boot >=2.7.0-M1 and <3.0.0-M1"
    }
  },
  "dependency-ranges": {
    "native": {
      "0.9.0": "Spring Boot >=2.4.3 and <2.4.4",
      "0.9.1": "Spring Boot >=2.4.4 and <2.4.5",
      "0.9.2": "Spring Boot >=2.4.5 and <2.5.0-M1",
      "0.10.0": "Spring Boot >=2.5.0-M1 and <2.5.2",
      "0.10.1": "Spring Boot >=2.5.2 and <2.5.3",
      "0.10.2": "Spring Boot >=2.5.3 and <2.5.4",
      "0.10.3": "Spring Boot >=2.5.4 and <2.5.5",
      "0.10.4": "Spring Boot >=2.5.5 and <2.5.6",
      "0.10.5": "Spring Boot >=2.5.6 and <2.5.9",
      "0.10.6": "Spring Boot >=2.5.9 and <2.6.0-M1",
      "0.11.0-M1": "Spring Boot >=2.6.0-M1 and <2.6.0-RC1",
      "0.11.0-M2": "Spring Boot >=2.6.0-RC1 and <2.6.0",
      "0.11.0-RC1": "Spring Boot >=2.6.0 and <2.6.1",
      "0.11.0": "Spring Boot >=2.6.1 and <2.6.2",
      "0.11.1": "Spring Boot >=2.6.2 and <2.6.3",
      "0.11.2": "Spring Boot >=2.6.3 and <2.6.4",
      "0.11.3": "Spring Boot >=2.6.4 and <2.6.6",
      "0.11.5": "Spring Boot >=2.6.6 and <2.7.0-M1",
      "0.12.0": "Spring Boot >=2.7.0-M1 and <2.7.1",
      "0.12.1": "Spring Boot >=2.7.1 and <3.0.0-M1"
    },
    "okta": {
      "1.4.0": "Spring Boot >=2.2.0.RELEASE and <2.4.0-M1",
      "1.5.1": "Spring Boot >=2.4.0-M1 and <2.4.1",
      "2.0.1": "Spring Boot >=2.4.1 and <2.5.0-M1",
      "2.1.6": "Spring Boot >=2.5.0-M1 and <3.0.0-M1"
    },
    "mybatis": {
      "2.1.4": "Spring Boot >=2.1.0.RELEASE and <2.5.0-M1",
      "2.2.2": "Spring Boot >=2.5.0-M1"
    },
    "camel": {
      "3.5.0": "Spring Boot >=2.3.0.M1 and <2.4.0-M1",
      "3.10.0": "Spring Boot >=2.4.0.M1 and <2.5.0-M1",
      "3.13.0": "Spring Boot >=2.5.0.M1 and <2.6.0-M1",
      "3.17.0": "Spring Boot >=2.6.0.M1 and <2.7.0-M1",
      "3.19.0": "Spring Boot >=2.7.0.M1 and <3.0.0-M1"
    },
    "picocli": {
      "4.6.3": "Spring Boot >=2.4.0.RELEASE and <3.0.0-M1"
    },
    "open-service-broker": {
      "3.2.0": "Spring Boot >=2.3.0.M1 and <2.4.0-M1",
      "3.3.1": "Spring Boot >=2.4.0-M1 and <2.5.0-M1",
      "3.4.1": "Spring Boot >=2.5.0-M1 and <2.6.0-M1",
      "3.5.0": "Spring Boot >=2.6.0-M1 and <2.7.0-M1"
    }
  }
}
```




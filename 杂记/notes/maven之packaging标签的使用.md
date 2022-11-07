[TOC]

首先maven作为一种XML标记语言，标签通常成对存在，目前packaging标签有3种配置：
```xml
<packaging>pom</packaging>
<packaging>jar</packaging>
<packaging>war</packaging>
```
1. <packaging>pom</packaging>
   
    在父级项目中的pom.xml文件使用的packaging配置一定为pom。父级的pom文件只作项目的子模块的整合，在maven install时不会生成jar/war压缩包。
    一定有童鞋会问：为什么需要一个父级pom文件呢？
    好处如下：
    - 可以通过<modules>标签来整合子模块的编译顺序（Maven引入依赖使用最短路径原则，例如a<–b<–c1.0 ，d<–e<–f<–c1.1，由于路径最短，最终引入的为c1.0；但路径长度相同时，则会引入先申明的依赖）。因此尽量将更加底层的service放在更先的位置优先加载依赖较为合适。
    - 可以将一些子项目中共用的依赖或将其版本统一写到父级配置中，以便统一管理。
    - groupId, artifactId, version能直接从父级继承，减少子项目的pom配置。
  
2. <packaging>jar</packaging>

Jar包是最为常见的打包方式，当pom文件中没有设置packaging参数时，默认使用jar方式打包。
这种打包方式意味着在maven build时会将这个项目中的所有java文件都进行编译形成.class文件，且按照原来的java文件层级结构放置，最终压缩为一个jar文件。
当我们使用mvn install命令的时候，能够发现在项目中与src文件夹同级新生成了一个target文件夹，这个文件夹内的classes文件夹即为刚才提到的编译后形成的文件夹。

3. <packaging>war</packaging>

war包与jar包非常相似，同样是编译后的.class文件按层级结构形成文件树后打包形成的压缩包。不同的是，它会将项目中依赖的所有jar包都放在WEB-INF/lib这个文件夹下。
WEB-INF/classes文件夹仍然放置我们自己代码的编译后形成的内容。
可想而知，war包非常适合部署时使用，不再需要下载其他的依赖包，能够使用户拿到war包直接使用，因此它经常使用于微服务项目群中的入口项目的pom配置中。
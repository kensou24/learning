# start spring boot
##  1.简介
- 简化了spring应用开发的框架
- 整个spring技术栈的一个大整合
- J2EE开发的一站式解决方案
## 2.微服务
- 单体应用进化到微服务
- 2014 martin flowler 提出的架构风格
- 一个应用应该是一组小型服务，可以使用HTTP的方式进行互通
- 每一个功能元素都是一个可独立替换和独立升级的软件单元
- 详细 https://www.cnblogs.com/liuning8023/p/4493156.html
## 3.Hello world

### pom 文件解析

#### 父项目

```
<!-- Spring Boot 启动父依赖 -->
<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>1.5.1.RELEASE</version>
</parent>
```

####  导入的依赖

```
<!-- Spring Boot web依赖 -->
<dependency>
<groupId>org.springframework.boot</groupId>
<artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

spring-boot将基本的功能场景进行了抽取，形成了一个个starter，只需在项目中导入即可。

### 主程序入口

```
// Spring Boot 应用的标识
@SpringBootApplication
public class Application {

    public static void main(String[] args) {
        // 程序启动入口
        // 启动嵌入式的 Tomcat 并初始化 Spring 环境及其各 Spring 组件
        SpringApplication.run(Application.class,args);
    }
}
```

run传递的必须是 springboot应用类

## 4.配置文件

### 初始的配置文件 application.proertities

### 使用配置文件进行注入

- 配置文件YML等之类的设置配置文件值

- 使用注释 @Componet @ConfigurationPropertities(prefix = "XXX")

- 导入处理器dependence [ process]

- 其他：使用@value

  ### 注入值进行数据校验

  @validated

  ​

  ​

  ​

  ​
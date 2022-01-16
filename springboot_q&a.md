#### 1. Q:为什么要用springboot，他好在哪里？
A: 简化spring的配置  

#### 2. Q:为什么要用spring，他好在哪里？
A: 方便解耦，简化开发 

#### 3. 在创建第一个springboot（spring web）中产生的问题
[参考资料](https://www.jetbrains.com/help/idea/your-first-spring-application.html)

在如下的java代码中：  @后面这些分别有什么作用，哪里调用了sayHello这个方法
```java
package com.example.demo1;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@SpringBootApplication
@RestController
public class Demo1Application {

    public static void main(String[] args) {
        SpringApplication.run(Demo1Application.class, args);
    }

    @GetMapping("/hello")
    public String sayHello(@RequestParam(value = "myName", defaultValue = "World") String name) {
        return String.format("Hello %s!", name);
    }

}

```

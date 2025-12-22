# JavaWeb企业开发全流程

# Web网站的工作流程：

![image-20241218192636477](img/image-20241218192636477.png)

问题：按照视频教程教的第四步就是浏览器做的。到底是浏览器做的还是前端服务器做的。

# 一、SpringBootWeb入门

## 一、SpringBootWeb入门

### 1、启动类

启动类用来启动SpringBoot工程的

### 2、@RestController注解与@Controller注解

#### （1）@RestController注解

是一个组合注解，它组合了@Controller注解和@ResponseBody注解的功能。@Controller是用于定义控制器的注解，**@ResponseBody用于方法上**，用此注解的方法将方法的返回值直接作为响应数据响应给浏览器客户端，如果返回值的类型是实体对象或集合，则将其转换为json格式再返回给前端。

#### （2）@Controller注解

其标记的类则为传统的控制器类，控制器类用来处理客户端发起的请求，并负责返回适当的视图作为响应。在使用@Controller注解的类中，通常需要在方法上使用@ResponseBody注解来表明该方法的返回值要作为响应的主体内容，而不是解析为视图。

#### （3）两者区别：

@ResponseBody适用于构建RESTful风格的API，其中每个方法的返回值都会直接序列化为JSON或xml数据并发送给客户端。而@Controller适用于传统的MVC架构，它负责处理请求并返回相应的视图。（@RestController下的方法默认返回的是数据格式，@Controller注解标注的类下面的方法默认返回的就是以视图为格式。）

#### （4）什么时候需要返回数据，什么时候需要返回视图

当设计RESTful风格的程序时，一般原则是

如果客户端希望获取数据（例如JSON、XML），则返回数据。

如果客户端需要展示数据（例如html页面），则返回视图。

#### （5）以实例说明更通俗易懂：

需要返回视图的实例：假设正在开发一个博客网站，有一个页面希望显示所有文章的列表，并且希望以HTML形式展示，这时候后端需要返回一个包含所有文章数据的视图，让前端直接显示这个页面。这时候需要后端渲染整个HTML页面。

只需要返回数据的实例：假设开发一个购物网站，前端使用Vue等框架构建。在购物车界面上，需要获取当前用户的购物车数据以便展示，前端会通过Ajax请求获取数据，此时后端只需返回数据，因为前端会通过JavaScript来处理和展示数据，不需要后端渲染页面。

**传统的springMVC一般就需要直接返回视图，而现在新兴的前端技术vue在项目中为前后端分离的架构，前端框架负责处理数据和渲染页面，而后端 API 则负责提供数据即可，所以对返回视图的要求也就比较少了**

有关这个知识点的CSDN文章：[【SpringBoot】带你一文彻底搞懂RestController和Controller的关系与区别-CSDN博客](https://blog.csdn.net/miles067/article/details/132567377)

#### （6）不懂的地方：

方法返回值以JSON或XML的形式直接写入HTTP响应体中     模板引擎  Ajax请求  JavaScript动态更新界面   RESTful风格的API   视图解析

### 3、@RequestMapping

## 二、HTTP协议

### 1、HTTP概述

#### 1、概念

Hyper Text Transfer Protocol,超文本传输协议，规定了浏览器和服务器之间数据传递的规则、格式。浏览器向服务器发送请求，服务器向浏览器做出响应。浏览器发送的请求需要携带请求数据，告诉服务器它要什么数据。服务器需要解析这个请求，从而搞清楚浏览器要什么数据，那么解析请求当然需要了解这个请求的格式了，数据的每一项代表什么含义，才能解析。服务器向浏览器响应数据，响应数据也有格式，浏览器也要按这种格式来解析响应数据。HTTP就是数据传输的规则数据传输的格式。

#### 2、特点

1、基于TCP协议：面向连接，安全

2、基于请求-响应模型的：一次请求对应一次响应

3、HTTP协议是无状态的协议：对于事物处理没有记忆能力。每次请求-响应都是独立的。

​		缺点：多次请求间不能共享数据。

​		优点：速度快

### 2、HTTP请求协议

HTTP请求协议其实就是请求数据的格式

请求行：请求数据格式的第一行：请求方式 资源路径 协议

请求头：第二行开始，格式key:value

![屏幕截图 2024-11-15 203317](D:\l1503\Pictures\Screenshots\屏幕截图 2024-11-15 203317.png)

请求体：POST请求特有的，存放请求参数

#### get请求与post请求的区别

请求方式-GET：请求参数在请求行中，没有请求体，get请求大小是有限制的。

请求方式-POST：请求参数在请求体中，POST请求大小是没有限制的。

### 3、HTTP响应协议

HTTP响应协议其实就是响应数据的格式

响应行：响应数据第一行：协议 状态码 描述

响应头：从第二行开始，key:value形式

响应体：最后一部分，存放响应数据。

响应状态码具体请看B站视频。

302：指示所请求的资源已移到由Location响应头给定的URL，浏览器会自动重新访问这个界面。

305：告诉浏览器，你请求的这个资源自上次取得后，服务端并未更改，你直接用你本地缓存吧隐藏重定向。

200：客户端请求成功

404：请求资源不存在，一般是URL书写错误，或服务器端资源被删除了。

500：服务器端发生了不可预期的错误。

### 4、HTTP协议解析

解析HTTP协议就是根据HTTP请求协议和响应协议解析请求数据和响应数据，服务器端解析请求数据，浏览器解析响应数据，各大浏览器以及集成了解析响应数据的程序，我们不用管，我们只需要在服务器端解析请求数据即可。但是各大公司已经创造出了很多web服务器（其实就是软件程序，用来解析请求数据的）封装了对HTTP协议的解析和操作处理。例如Apache Tomcat不需要我们自己在服务器端写解析请求数据的程序了。

## 三、Web服务器

web服务器是一个软件程序，对HTTP协议的操作进行封装，使得程序员不必直接对协议进行操作，让web开发更加便捷。

我们只需要在我们的服务器上安装好web服务器，然后把程序部署到web服务器上。然后我们启动服务器，输入对应url地址就可以直接访问到部署在web服务器上的程序了。

### 1、Tomcat

Tomcat是apache基金会的一个核心项目，是一个开源免费的轻量级Web服务器，支持Servlet/JSP少量JavaEE规范。

## 四、SpringBoot起步依赖的原理和其内嵌Tomcat服务器

1、起步依赖：利用了Maven的依赖传递，实现了起步依赖，比如只需要引入一个spring-boot-starter-web就包含了几乎所有web开发需要的依赖了。

SpringBoot内嵌tomcat服务器，在启动启动类时，内嵌的tomcat服务器会自动启动，并占用8080端口。不需要再用外部的tomcat了。

# 二、Web后端开发

## 一、Web后端开发

### 一、请求响应概述

其实我们开发的Controller程序tomcat服务器是不识别的，那不识别的话，服务器和客户端浏览器是怎么交互的呢？那是因为SpringBoot底层写了一个Servlet类，叫做DispatcherServlet类，这个类继承了Servlet接口，所以tomcat是识别这个类的。所以从浏览器发来的请求，tomcat把他解析后会把解析后的数据封装成一个HttpServletRequest对象，然后这些对象都会经过这个DispatcherServlet类，然后DispatcherServlet类把请求对象传给对应的Controller类，然后Controller类处理完请求后再把响应的数据传给DispatcherServlet类，DispatcherServlet类把响应的数据封装成HttpServletRespone对象，然后tomcat服务器根据我们在HttpServletRespone对象中设置的响应数据，把响应数据给浏览器。DispatcherServlet类我们叫前端核心控制器，HttpServletRequest对象我们叫请求对象，用来获取请求数据。HttpServletRespone对象我们叫响应对象。用来设置响应数据。

还需仔细了解：Servlet

### 二、请求

#### 1、简单参数的接收与封装

（1）传统方式：已过时

（2）SpringBoot中的接收方式：

参数名与处理这个请求的方法的形参参数名相同，即可接收到请求参数。但形参参数名与请求参数名不一致将无法接收到请求参数，此时可以用注解@RequestParam完成映射。用@RequestParam注解的name属性或value属性来指定请求参数名即可。传回来的请求参数都是字符串类型，SpringBoot可以帮我们转换类型，不用我们管。如下代码所示：

get请求：

```url
http://localhost:8080/simpleParam?name=Tom&age=10
```



post请求：

![image-20241218094406611](img/image-20241218094406611.png)



```java
@RequestMapping("/simpleParam")
public String simpleParam(@RequestParam(name="name")String username, Integer age){
    System.out.println(username + ":" + age);
    return "OK";
}
```



**注意：**@RequestParam注解中的required属性默认为true,代表该请求参数必须传递，如果不传递将报错。如果该参数是可选的，可以将required属性设置为false。

#### 2、简单实体参数的接收与封装

当请求参数很多时，用简单参数的方式就有些繁琐了，这时我们可以把所有的请求参数封装到一个实体对象中，就方便很多。

简单实体对象：请求参数名与处理这个请求的方法的形参对象的属性名相同即可，然后定义POJO接收即可。

POJO类：

```java
package com.it.POJO;

public class User {
    private String name;
    private int age;
  

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "User{" +
                "name='" + name + '\'' +
                ", age=" + age +
                
                '}';
    }
}
```



controller类：

```java
package com.it.Controller;

import com.it.POJO.User;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class RequestController {
    //简单实体参数
    @RequestMapping("/simplePojo")
    public String simplePojo(User user) {
        System.out.println(user);
        return "OK";
    }
    
}
```



如果实体类中的属性比传入的参数多，那没有传入那部分就继续保持属性的默认值，比如属性是引用类型的，它的默认值是null，那就继续保持null值。

#### 3、复杂实体参数的接收与封装

同简单实体参数一样，只不过需要按层次结构对应起来即可。

URL这样写：http://localhost:8080/comeplexPojo?name=ITCAST&age=20&address.province=北京&address.city=北京

POJO类：

User类：

```java
package com.it.POJO;

public class User {
    private String name;
    private int age;
    private Address address;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public Address getAddress() {
        return address;
    }

    public void setAddress(Address address) {
        this.address = address;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "User{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", address=" + address +
                '}';
    }
}
```



Address类：

```java
package com.it.POJO;

public class Address {
    private String province;
    private String city;

    public String getProvince() {
        return province;
    }

    public void setProvince(String province) {
        this.province = province;
    }

    public String getCity() {
        return city;
    }

    public void setCity(String city) {
        this.city = city;
    }

    @Override
    public String toString() {
        return "Address{" +
                "province='" + province + '\'' +
                ", city='" + city + '\'' +
                '}';
    }
}
```



#### 4、数组集合参数的接收与封装

（1）数组参数：请求参数名与形参数组名相同且请求参数为多个时，定义数组类型形参即可接收参数。

url地址：http://localhost:8080/arrayParam?hobby=java&hobby=game&hobby=sing

```java
@RequestMapping("/arrayParam")
    public String arrayParam(String[] hobby){
        System.out.println(Arrays.toString(hobby));
        return "OK";
    }
```



（2）集合参数：请求参数名与形参集合名相同且请求参数为多个时，定义集合类型形参，@RequestParam注解绑定参数关系，即可接收封装请求参数。因为默认情况下，一个请求参数有多个值时是会封装到数组中的，所以前面要加上@RequestParam来绑定参数关系，才可以封装在集合中。

url地址：http://localhost:8080/listParam?hobby=java&hobby=game&hobby=sing

```java
@RequestMapping("/listParam")
    public String listParam(@RequestParam List<String> hobby){
        System.out.println(hobby);
        return "OK";
    }
```



#### 5、日期时间参数的接收与封装

使用@DataTimeFormat注解来规定前端传来的日期参数的格式。

url地址：http://localhost:8080/dataParam?updateTime=2023-09-09 10:10:10

```java
@RequestMapping("/dataParam")
    public String dataParam(@DateTimeFormat(pattern = "yyyy-MM-dd HH:mm:ss") LocalDateTime updateTime){
        System.out.println(updateTime);
        return "OK";
    }
```



#### 6、Json参数

Json类型请求参数一般通过实体类来接收封装。Json数据键名与形参中的实体类对象属性名相同，且在形参中的实体类对象前加上@RequestBody注解，该注解的作用是将Json请求参数绑定在实体对象上。

```java
package com.it.Controller;

import com.it.POJO.User;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class RequestController {
    @RequestMapping("/jsonParam")
    public String jsonParam(@RequestBody User user) {
        System.out.println(user);
        return "OK";
    }
}
```



```java
package com.it.POJO;

public class User {
    private String name;
    private int age;
    private Address address;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public Address getAddress() {
        return address;
    }

    public void setAddress(Address address) {
        this.address = address;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "User{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", address=" + address +
                '}';
    }
}
```



```java
package com.it.POJO;

public class Address {
    private String province;
    private String city;

    public String getProvince() {
        return province;
    }

    public void setProvince(String province) {
        this.province = province;
    }

    public String getCity() {
        return city;
    }

    public void setCity(String city) {
        this.city = city;
    }

    @Override
    public String toString() {
        return "Address{" +
                "province='" + province + '\'' +
                ", city='" + city + '\'' +
                '}';
    }
}
```



**问题**：在实际开发中前端浏览器怎么传递json类型的参数

#### 7、路径参数

路径参数指该参数既是请求路径的一部分又是请求参数，接受这样的请求参数需要在@RequestMapping()的请求路径后以{...}这样的方式来表示路径参数，且路径参数名需要与处理请求的方法的中的形参的名字保持一致，且须在对应的形参前加上@PathVariable注解。

```java
http://localhost:8080/path/100/tomcate
```



```java
//路径参数
    @RequestMapping("/path/{id}")
    public String pathParam(@PathVariable Integer id){
        System.out.println(id);
        return "OK";
    }

    //多个路径参数
    @RequestMapping("/path/{id}/{name}")
    public String pathParam2(@PathVariable Integer id, @PathVariable String name){
        System.out.println(id + " " + name);
        return "OK";
    }
```



### 三、响应

#### 1、响应数据

##### @ResponseBody注解

类型：类注解、方法注解

位置：Controller方法上/类上

作用：将方法的返回值直接作为响应数据响应给浏览器客户端，如果返回值的类型是**实体**对象或是集合，则将其转换为json格式数据再响应给浏览器。

集合会转换成json类型的数组。

说明：@RestController = @Controller + @ResponseBody

```java
package com.it.Controller;

import com.it.POJO.Address;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import java.util.ArrayList;
import java.util.List;

@RestController
public class ResponseController {
    @RequestMapping("/hello")
    public String hello() {
        System.out.println("hello");
        return "hello";
    }
    @RequestMapping("/getAddress")
    public Address getAddress() {
        Address address = new Address();
        address.setProvince("广东");
        address.setCity("深圳");
        return address;
    }
    @RequestMapping("/getAddressList")
    public List<Address> getAddressList() {
        List<Address> list = new ArrayList<>();
        Address address = new Address();
        address.setProvince("广东");
        address.setCity("深圳");
        list.add(address);
        Address address1 = new Address();
        address1.setProvince("陕西");
        address1.setCity("西安");
        list.add(address1);
        return list;
    }
}
```



![image-20241117093634991](img/image-20241117093634991.png)

![image-20241117093710019](img/image-20241117093710019.png)

![image-20241117093741261](img/image-20241117093741261.png)



#### 2、统一响应结果

一般在项目中，我们都会为每个功能接口定义一个统一的响应结果格式，这个统一的响应结果一般定义为Result。这个统一的响应结果通用性比较强，基本可以满足所有的业务场景。最终前端拿到的就是这样一个统一的响应结果格式，处理方便。

```java
package com.it.POJO;

public class Result {
    //响应码 1表示成功 0表示失败
    private Integer code;
    //提示信息
    private String msg;
    //响应的主体数据
    private Object data;
    public Result(Integer code, String msg, Object data) {
        this.code = code;
        this.msg = msg;
        this.data = data;
    }
    public Result(){

    }

    public Integer getCode() {
        return code;
    }

    public void setCode(Integer code) {
        this.code = code;
    }

    public String getMsg() {
        return msg;
    }

    public void setMsg(String msg) {
        this.msg = msg;
    }

    public Object getData() {
        return data;
    }

    public void setData(Object data) {
        this.data = data;
    }
    public static Result success(Object data) {
        return new Result(1, "success", data);
    }
    public static Result success() {
        return new Result(1, "success", null);
    }
    public static Result error(String msg) {
        return new Result(0, msg, null);
    }

    @Override
    public String toString() {
        return "Result{" +
                "code=" + code +
                ", msg='" + msg + '\'' +
                ", data=" + data +
                '}';
    }
}
```



#### 3、响应案例

需要学dom4j，自己看着视频写前后端代码。

弄懂这个是什么意思：empList.stream().forEach(emp->{})

### 四、分层解耦

将数据操作和逻辑处理的代码都放到一个类中（传统开发方法）会导致代码复用性差，不易于维护和扩展。通过程序的分层解耦就可以解决这些问题。

#### 1、web开发的三层架构

满足单一职责原则。

controller: 控制层，只负责接受请求，响应数据。接受前端发送来的请求，对请求进行处理，并响应数据。

service:业务逻辑层，负责业务逻辑的处理。

Dao:数据访问层（Data Access Object）(持久层)，负责数据访问操作，例如数据的增、删、改、查。

前端发起请求后web程序的整体工作流程：前端发起请求，Controller层接收请求，对请求进行处理，然后访问service层，service层要进行逻辑处理，逻辑处理的前提是拿到数据，所一service层会先去访问dao层，dao层访问数据源，拿到原始数据后将其返回给service层，service层对数据进行逻辑处理，然后将处理后的数据返回给controller层，Controller层将其作为响应数据响应给前端。

![image-20241117163737915](img/image-20241117163737915.png)

其中要使用面向接口编程，比如dao层，它可能从文件中获取数据，也可能从数据库获取数据，也可能从别人给我们的接口中获取数据，所以我们可以采用面向接口编程，定义一个dao层的接口，再定义多个实现类。

web开发的三层架构优点：易于复用、易于维护、易于扩展。

问题：面向接口编程。多态。箭头函数。

采用面向接口编程的好处？

#### 2、分层解耦

像上面这样，controller类要用service实现类的对象时就new这个对象，这样这两个类之间就是耦合的。比如如果后续service实现类的名字变了，或者是controller类要用service类的另一个实现类，就需要改变controller类中的代码。所以我们就需要解耦。

springboot中的解耦思想依靠的是两个重要的机制：控制反转、依赖注入。

控制反转：（Inversion Of Control）简称IOC。对象的创建控制权由程序自身转移到容器，这种思想称为控制反转。

依赖注入：Dependency Injection,简称DI，容器为应用程序提供运行时所需要的资源，称为依赖注入。

Bean对象：IOC容器中创建、管理的对象。

#### 3、IOC与DI的入门

（1）在Service层和Dao层的实现类上加上@Component注解，该注解的作用是将该实现类交给IOC容器管理，且IOC容器会创建对应的Bean对象。这是控制反转。

（2）为Controller层和Service层注入运行时所依赖的Bean对象：在需要注入Bean对象的成员变量上加上@Autowired注解，该注解的作用是，IOC容器会在**运行时**自动为加了该注解的成员变量提供其对应类型的Bean对象，并将该Bean对象赋值给这个变量。这是依赖注入。

**这样就实现了解耦**，如果改了service实现类的名字我们也不需要改动controller类的代码。如果要在controller类中换一个service类的实现类使用，直接将原来用的实现类上的@Component注解去掉，在新换的实现类上加上@Component注解即可，也不用改动controller层的代码。

#### 4、IOC详解

控制反转就是把对象的控制权交给容器，由容器进行对象的创建和管理。这些对象也被称为Bean对象。IOC容器控制管理的对象称为Bean对象。

1、**Bean对象的声明**：

要把某个对象交给IOC容器进行管理，需要在对应的类上加上如下注解：

@Component：声明Bean的基础注解  不属于以下三类时用此注解。

@Controller：@Component的衍生注解，标注在控制器类上

@Service：@Component的衍生注解，标注在业务类上。

@Repository：@Component的衍生注解，标注在数据访问类上（由于与Mybatis整合，用的少）

**2、注意**：

每个Bean对象都有一个名字作为Bean对象的标识，默认名字Bean对应类的名字首字母小写。也可以通过上述注解中的value属性来设置名字。

使用以上四个注解都可以声明Bean对象，但是在springboot集成web开发时，声明控制器bean只能用@Controller注解。

3、bean组件扫描

前面声明Bean的四个组件要想生效，需要被组件扫描注解@ComponentScan扫描。

@ComponentScan注解虽然没有显示配置，但是实际上已经包含在启动类声明注解@SpringBootApplication中，默认扫描的范围是启动类所在的包，及其子包。

#### 5、DI详解

DI是依赖注入的缩写，依赖注入就是指程序在运行中IOC容器会自动为程序提供它所需要的资源。但是如果程序在运行中需要某一类型的Bean对象，在IOC容器中有多个此类型的Bean对象，如果我们采用的是@Autowired注解进行的依赖注入，那么IOC容器就会不知道该注入哪个Bean对象。那么怎么解决这个问题呢？

（1）在需要注入的Bean对象上加上@Primary注解。

（2）使用@Autowired与@Qualifier("Bean对象的名字")注解。

（3）使用Resource(name="Bean对象的名字")注解。@Autowired注解是根据类型注入IOC容器的注解。而@Resource注解是根据名字注入的注解。

##### 面试题

@Autowired注解和@Resource注解的区别

（1）@Autowired注解是spring框架提供的，而@Resource注解是JDK提供的。

（2）@Autowired注解是按照类型注入的，而@Resource注解是按照名称注入的。

## 二、MySQL数据库

### 一、什么是数据库

数据库：DataBase(DB)，是存储和管理数据的仓库。

数据库管理系统：DataBase Management System(DBMS)，操纵和管理数据库的大型软件。

SQL语言：Structured Query Language，是操作关系型数据库的编程语言，它告诉数据库管理系统我们操作哪个数据，要进行怎样的操作。定义了一套操作关系型数据库的**统一标注**。所有的关系型数据库都用SQL操作。

### 二、MySQL概述

#### 1、连接MySQL

客户端命令：mysql -u用户名 -p密码 [-h数据库服务器IP地址 -P端口号]

MySQL企业开发使用方式

在企业开发中MySQL数据库不是部署在我们自己的电脑上的，是部署在服务上的，我们要连接远程部署在服务器上的MySQL数据库只需要通过MySQL客户端通过以上命令连接即可。

我们在自己学习中如果想体验一下企业级开发，就可以安装一个虚拟机软件VMware，虚拟出一台服务器，在虚拟出来的这台服务器上面就可以安装我们开发需要的各种软件了比如MySQL、redis、tomcat等。

#### 2、MySQL数据模型

![image-20241119114733307](img/image-20241119114733307.png)

客户端通过输入相应的客户端命令连接数据库服务器，数据库服务器中内置了数据库管理系统DBMS，客户端通过SQL告诉DBMS要怎样操作数据库，DBMS按SQL的要求操作数据库。一个数据库服务器中可以有多个数据库，他们之间互不干扰。

#### 3、SQL简介

SQL：一门操作关系型数据库的编程语言，定义操作所有关系型数据库的统一标准。

**通用语法**：

（1）SQL语句可以单行或多行书写，以分号结尾。

（2）SQL语句可以使用空格/缩进来增强语句的可读性。

（3）**MySQL**数据库的SQL语句不区分大小写。

4、SQL分类

SQL语句通常被分为四大类

DDL（Data definition Language）:数据定义语言,用来定义数据库中的对象的（数据库，表，字段）

DML（Data Manipulation Language）:数据操作语言，用来对数据库表中的数据进行增删改查。

DQL（Data Query Language）:数据查询语言，用来查询数据库表中的数据的。

DCL（Data Control Language）:数据控制语言，用来创建数据库用户，控制数据库的访问权限。

数据库设计、数据库操作、数据库优化。当程序性能遇到瓶颈时可以通过优化数据库来提高。

### 三、数据库设计-DDL（数据库操作）

查询：
查询所有数据库：show databases

查询现在正在使用的数据库：select database();

创建数据库：create database db01;

create database if not exists db01;

使用数据库：use 数据库名

删除数据库：drop database db01;

drop database if exists db01;

上述语句中database可以替换成schema；

### 四、DDL(表操作)

#### 1、语法见下面代码：

```sql
create table tb_user (
    id int primary key auto_increment comment '主键，唯一标识',
    username varchar(20) not null unique comment '用户名',
    name varchar(20) not null comment '姓名',
    age int comment '年龄',
    gender char default '男' comment '性别'
)comment '用户表';
```



#### 2、约束：

概念：约束是作用于表中字段上的规则，用于限制存储在表中的数据。

目的：保证数据库中数据的有效性，正确性、完整性。

|   约束   |                             描述                             |   关键字    |
| :------: | :----------------------------------------------------------: | :---------: |
| 非空约束 |                  限制该字段的值不能为null值                  |  not null   |
| 唯一约束 |            保证字段的所有数据都是唯一的，不重复的            |   unique    |
| 主键约束 |           主键是一行数据的唯一标识，要求非空且唯一           | primary key |
| 默认约束 | 为字段设置默认值，如果保存数据时没有为该字段指定值，那么就采用默认值 |   default   |
| 外键约束 |        让两张表的数据建立连接，保证数据的一致性完整性        | foreign key |

#### 3、数据类型

MySQL中的数据类型有很多，主要分为三类：数值类型、字符串类型、日期时间类型。

数值类型

|   类型    | 大小(byte) |     有符号(signed)范围      | 无符号(unsigned)范围 |       描述       |                             备注                             |
| :-------: | :--------: | :-------------------------: | :------------------: | :--------------: | :----------------------------------------------------------: |
|  tinyint  |     1      |        （-128，127）        |      （0，255）      |     小整数值     |                                                              |
| smallint  |     2      |      （-32768，32767）      |     （0，65535）     |     大整数值     |                                                              |
| mediumint |     3      |    （-8388608，8388607）    |   （0，16777215）    |     大整数值     |                                                              |
|    int    |     4      | （-2147483648，2147483647） |  （0，4294967295）   |     大整数值     |                                                              |
|  bigint   |     8      |                             |                      |    极大整数值    |                                                              |
|   float   |     4      |                             |                      |  单精度浮点数值  |         float(5,2)5表示整个数字长度，2表示小数位个数         |
|  double   |     8      |                             |                      |  双精度浮点数值  |        double(5,2)5表示整个数字长度，2表示小数位个数         |
|  decimal  |            |                             |                      | 小数值(精度更高) | 表示同上，如果涉及金融等一点偏差都不能有的数值，就用这个类型。 |

在开发中，在实际情况允许的情况下，尽量使用小的类型，够用就行了，节省空间。

对于 int 类型的一些基础知识其实上图已经说的很明白了，在这里想讨论下常用的 int(11) 代表什么意思，很长时间以来我都以为这代表着限制 int 的长度为 11 位，直到有天看到篇文章才明白，11 代表的并不是长度，而是`字符的显示宽度`，在字段类型为 int 时，无论你显示宽度设置为多少，int 类型能存储的最大值和最小值永远都是固定的。

那么这个显示宽度到底有什么用呢？**当 int 字段类型设置为无符号且填充零**（UNSIGNED ZEROFILL）时，当数值位数未达到设置的显示宽度时，会在数值前面补充零直到满足设定的显示宽度。

总结：只有加上**当 int 字段类型设置为无符号且填充零**（UNSIGNED ZEROFILL）约束时int(11)才会生效，且只对不足11位**显示长度**的数字生效——补零，对于够11为或者超出11为的数字都没有任何影响。

字符串类型：

|  类型   |    大小     |                             备注                             |
| :-----: | :---------: | :----------------------------------------------------------: |
|  char   |  0-255byte  | 定长字符串，char(10)：最多只能存10个字符，如果不足10个字符也占用10个字符的空间。 |
| varchar | 0-65535byte | 变长字符串，varchar(10)：最多只能存10个字符，如果不足10个字符，按照实际长度存储。 |
|  text   | 0-65535byte |                          长文本数据                          |
|         |             |                                                              |
|         |             |                                                              |
|         |             |                                                              |
|         |             |                                                              |
|         |             |                                                              |
|         |             |                                                              |
|         |             |                                                              |

如果编码为UTF-8：1character=3bytes, 1汉字=1character  也就是说一个字段定义成 varchar(200)，则它可以存储200个汉字或者200个字母。

如果编码为gbk：1character=2bytes,1汉字=1character 也就是说一个字段定义成 varchar(200)，则它可以存储200个汉字或者200个字母。

日期类型：

|   类型    | 大小  |                   范围                   |        格式         |        描述        |
| :-------: | :---: | :--------------------------------------: | :-----------------: | :----------------: |
|   date    | 3byte |           1000-1-1至9999-12-31           |     YYYY-MM-DD      |       日期值       |
|   time    |   3   |          -838:59:59至838-59-59           |      HH:MM:SS       |  时间值或持续时间  |
|   year    |   1   |                1901至2155                |        YYYY         |       年份值       |
| datetime  |   8   | 1000-01-01 00:00:00至9999-12-31 23:59:59 | YYYY-MM-DD HH:MM:SS | 混合日期值和时间值 |
| timestamp |       |                                          |                     |                    |

#### 4、案例

创建表案例：

**实际开发经验：**

（1）创建一张表，一上来就创建一个id。

（2）实际开发中，创建表时一定要认真仔细阅读原型文件、接口文件或者是需求文档。

（3）在实际开发中大多都是用图形化界面的方式创建表的。所以把这个掌握了就行。

（4）在实际开发中创建性别字段时一般把数据类型创建为数字tinyint。因为后续在前端页面显示时可能显示男女或男性女性或英文，这样设置比较灵活。

（5）在实际开发中数据库中存储图片存储的是图片的访问地址url。真实的图片视频等在实际开发中都是存储在专门的文件服务器上的。

（6）在实际开发中，如果开发的是后台管理系统，那么一般会在表结构中设置俩个字段create_time、update_time。

设计表结构的基本流程：认真阅读需求文档、原型文档、接口文档。——>找出原型字段，并确定其数据类型和约束。——>在创建基础字段（id、create_time、update_time）

![image-20241120142106211](img/image-20241120142106211.png)

掌握通过图形化界面的方式创建表结构。

#### 5、DDL查看表结构

```sql
-- 查看当前数据库下的所有表
show tables ;
-- 查看指定表结构
desc tb_emp;
-- 查看数据库的建表语句
show create table tb_emp;
```



idea查看表sql语句：右键表，点击Edit Source

#### 5、DDL修改表结构

```sql
-- 添加字段
alter table tb_emp add qq varchar(11) comment 'QQ';
-- 修改字段类型
alter table tb_emp modify qq varchar(13) comment 'QQ';
-- 修改字段名
alter table tb_emp change qq qq_name varchar(13) comment 'QQ';
-- 删除字段
alter table tb_emp drop column qq;
```



#### 6、总结

数据库定义语句DDL语句

数据库——创建、查询、使用、删除。

数据表——创建（语法、约束、数据类型、设计）、查询、修改、删除

### 五、数据库操作-DML

1、在SQL语句中，字符串和日期类型数据必须用引号引起来，单引号双引号都可以。

2、想要在SQL中引入当前系统的时间可以用函数now()。

#### 1、添加数据inster

语法：

```sql
-- DML：数据操作语言
-- DML：插入数据 -inster
-- 1、为指定字段插入值
insert into tb_emp (username, name, gender, create_time, update_time) values ('wuji', '张无忌', 1, now(), now());
-- 2、为所有字段插入值
insert into tb_emp (id, username, name, password, gender, image, job, entrydata, create_time, update_time)
values (null, 'zhiruo', '周芷若', '123', 2, '1.jpg', 1, '2010-01-01', now(), now());

insert into tb_emp values (null, 'zhiruo2', '周芷若', '123', 2, '1.jpg', 1, '2010-01-01', now(), now());
-- 批量插入数据
insert into tb_emp (username, name, gender, create_time, update_time)
values ('weifuwang', '韦一笑', 1, now(), now()), ('xieshiwang', '谢逊', 1, now(), now());
```



#### 2、修改数据updata

语法：

```sql
-- DML: 更新数据 - updata
-- 1、有条件的更新
update tb_emp set username = 'wuji', name = '张三', update_time = now() where id = 1;
-- 2、无条件更新，更新所有
update tb_emp set entrydata = '2010-01-01', update_time = now();
```



更新语句的条件可以有也可以没有，如果没有，则更新整张表的所有数据。

3、删除数据delete

语法：

```sql
-- DML:删除数据 - delete
-- 1、有条件的删除
delete from tb_emp where id = 1;
-- 2、删除整张表的数据
delete from tb_emp;
```



**注意**：

（1）delete语句中的条件可以有也可以没有，如果没有就删除整张表的所有数据。

（2）delete语句不能删除某一个字段的值，如果要删除可以采用update语句，将该字段的值设置为null。

### 六、数据库查询-DQL

DQL，Data Query Language(数据查询语言)，用来查询数据库表中的记录。

关键字：SELECT

![image-20241122093039688](img/image-20241122093039688.png)

#### 1、DQL-基本查询

```sql
-- DQL:基本查询
-- 1、查询指定字段name entrydate并返回
select name, entrydate from tb_emp;
-- 2、查询返回所有字段
-- 推荐使用这种方法，性能高
select id,username,password,name,gender,image,job,entrydate,create_time,update_time from tb_emp;
-- 不推荐使用这种方法，性能低
select * from tb_emp;
-- 查询所有员工的name entrydate，并起别名姓名和入职日期
select name as 姓名, entrydate as 入职日期 from tb_emp;
-- as可以省略
select name  姓名, entrydate  入职日期 from tb_emp;
-- 如果别名中有特殊符号，必须加引号
select name as "姓 名", entrydate as '入职_日期' from tb_emp;
-- 查询已有的员工关联了哪几种职位，不要重复
select distinct job from  tb_emp;
```



**注意**：
（1）在用DQL语句查询返回所有字段的数据时，推荐用把所有字段罗列出来的方式，不推荐使用通配符*的方式，因为性能低。

（2）查询某个字段的数据并起别名时，as可以省略。如果别名中有特殊字符或空格，需要给别名加上引号，单引号双引号都可以。

**问题**：

使用distinct关键字去除重复记录时，distinct写在字段列表前面，那如果这个字段列表中一个字段的值存在重复，但是另一个不重复，那到底是去除呢还是不去除？

答：好像是distinct只允许操作一个字段。

#### 2、DQL-条件查询

语法：

```sql
-- DQL：条件查询
-- 1、查询姓名为杨逍的员工
select id,username,password,name,gender,image,job,entrydate,create_time,update_time from tb_emp where name = '杨逍';
-- 查询id小于等于5的员工信息
select id,username,password,name,gender,image,job,entrydate,create_time,update_time from tb_emp where id <= 5;
-- 查询没有分配职位的员工信息
select id,username,password,name,gender,image,job,entrydate,create_time,update_time from tb_emp where job is null;
-- 查询有职位的员工信息
select id,username,password,name,gender,image,job,entrydate,create_time,update_time from tb_emp where job is not null;
-- 查询密码不等于'123456'的员工信息
select id,username,password,name,gender,image,job,entrydate,create_time,update_time from tb_emp where password = '123456';
-- 查询入职日期在2001-01-01（包含）到2010-01-01（包含）之间的员工信息
select id,username,password,name,gender,image,job,entrydate,create_time,update_time from tb_emp where entrydate between '2001-01-01' and '2010-01-01';
-- 查询入职日期在2001-01-01（包含）到2010-01-01（包含）之间，且性别为女的员工信息
select id,username,password,name,gender,image,job,entrydate,create_time,update_time from tb_emp where entrydate between '2001-01-01' and '2010-01-01' and gender = '2';
-- 查询职位是2， 3， 4，的员工信息
select id,username,password,name,gender,image,job,entrydate,create_time,update_time from tb_emp where job in (2, 3, 4);
select id,username,password,name,gender,image,job,entrydate,create_time,update_time from tb_emp where job = 2 or job = 3 or job = 4;
-- 查询姓名为两个字的员工信息
select id,username,password,name,gender,image,job,entrydate,create_time,update_time from tb_emp where name like '__';
-- 查询姓张的员工信息
select id,username,password,name,gender,image,job,entrydate,create_time,update_time from tb_emp where name like '张%';
```

构建条件查询中条件的运算符一共有两类。

|    比较运算符    |                         功能                         |
| :--------------: | :--------------------------------------------------: |
|        >         |                         大于                         |
|        >=        |                       大于等于                       |
|        <         |                         小于                         |
|        <=        |                       小于等于                       |
|        =         |                         等于                         |
|     != / <>      |                        不等于                        |
| between...and... |            在某个范围之内，含最大值最小值            |
|     in(...)      |             在in之后的列表中的值，多选一             |
|   like 占位符    | 模糊查询，'_'代表匹配单个字符，'%'代表匹配任意个字符 |
|     is null      |                    判断是不是null                    |



| 逻辑运算符 | 功能 |
| :--------: | :--: |
| and 或 &&  |  与  |
| or 或 \|\| |  或  |
|  not 或 !  |  非  |

#### 3、DQL-分组查询

##### 1、聚合函数

介绍：将一列数据作为一个整体，进行纵向计算。

语法：select 聚合函数（字段列表）from 表名

|  函数   |   功能   |
| :-----: | :------: |
| count() | 统计数量 |
|  max()  |  最大值  |
|  min()  |  最小值  |
|  avg()  |  平均值  |
|  sum()  |   求和   |

```sql
-- DQL：分组查询
-- 聚合函数
-- 1、统计该企业员工数量 -- count()
-- A count(任一字段)
select count(id) from tb_emp;
-- B count(任意不为null的常量)
select count(0) from tb_emp;
-- C count(*) -- 推荐
select count(*) from tb_emp;
-- 统计该企业最早入职的员工
select min(entrydate) from tb_emp;
-- 统计该企业最迟入职的员工
select max(entrydate) from tb_emp;
-- 统计该企业员工id的平均值
select avg(id) from tb_emp;
-- 统计该企业员工的id之和
select sum(id) from tb_emp;
```



**注意**：

（1）聚合函数count()在统计总数时是不算空值的，也就是不算null，所以如果要采用count(字段)这样的方式统计总数的话一定要填入一个不运行为空的字段。

（2）在实际开发中推荐使用count(*)的方式进行统计总数，因为MySQL数据库底层对此做了专门的优化处理。

（3）null值不参与任何聚合函数运算。

（5）看上面代码聚合函数可以进行时间的运算。

##### 2、分组查询

分组查询后select后面可以返回的字段主要包含两类：分组字段、聚合函数。

语法：

```sql
-- 分组
-- 根据性别分组，统计男性和女性员工的数量
select gender,count(*) from tb_emp group by gender;
-- 先查询入职时间在2015-01-01（包含）以前的员工，并对结果根据职位分组，获取员工数量大于等于2的职位。
select job,count(*) from tb_emp where entrydate <= '2015-01-01' group by job having count(*) >= 2;
```



**面试题**：where和have区别

1、执行时机不同：where是分组之前执行过滤，不满足where条件，不参与分组；而having是分组之后对结果进行过滤。

2、判断条件不同：where不能对聚合函数进行判断，而having可以。

**注意**：

1、分组之后，查询的字段一般为聚合函数和分组字段，查询其他字段无任何意义。

2、执行顺序：where>分组操作>聚合函数>having。

#### 4、DQL-排序查询

语法：

```sql
-- 排序查询
-- 根据入职时间对员工进行升序排序
select id,username,password,name,gender,image,job,entrydate,create_time,update_time from tb_emp order by entrydate;
-- 根据入职时间，对员工进行降序排序
select id,username,password,name,gender,image,job,entrydate,create_time,update_time from tb_emp order by entrydate desc;
-- 根据入职时间对员工进行升序排序,如果入职时间相同，再按照更新时间进行降序排序。
select id,username,password,name,gender,image,job,entrydate,create_time,update_time from tb_emp order by entrydate, update_time desc;
```



排序方式：asc升序（默认），desc降序

**注意**：

如果是多字段排序，当一个字段相同时，才会根据第二个字段进行排序。

#### 5、DQL-分页查询

语法：select 字段列表 from 表名 limite 起始索引，每页显示几条

```sql
-- 分页查询
-- 1、从起使索引0开始查询员工数据，每页展示5条。
select id,username,password,name,gender,image,job,entrydate,create_time,update_time from tb_emp limit 0, 5;
-- 查询第一页员工数据，每页展示5条。
select id,username,password,name,gender,image,job,entrydate,create_time,update_time from tb_emp limit 0, 5;
-- 查询第2页员工数据，每页展示5条。
select id,username,password,name,gender,image,job,entrydate,create_time,update_time from tb_emp limit 5, 5;
-- 查询第3页员工数据，每页展示5条。
select id,username,password,name,gender,image,job,entrydate,create_time,update_time from tb_emp limit 10, 5;
```



**注意**：

（1）起始索引从0开始，起始索引=（查询页码 - 1）* 每页条数

（2）分页查询是数据库的方言，MySQL采用的是limite。

（3）如果查询的是第一页数据，起始索引可以省略。

#### 6、案例

案例1：

```sql
-- 案例1 按需求完成员工管理的条件分页查询 - 根据输入条件，查询第一页数据，每页展示10条
-- 输入条件
    -- 姓名：张
    -- 性别：男
    -- 入职时间：2000-01-01到2015-12-31
select id,
       username,
       password,
       name,
       gender,
       image,
       job,
       entrydate,
       create_time,
       update_time
from tb_emp
where name like '张%'
  and gender = '1'
  and entrydate between '2000-01-01' and '2015-12-31'
order by update_time desc
limit 10,10;
```



案例2：

```sql
-- 案例2-1:根据需求完成员工性别信息的统计
select if(gender=1, '男性员工', '女性员工') 性别,count(*) 人数 from tb_emp group by gender ;
-- 案例2-2：根据需求完成员工职位信息的统计
select
    case job when 1 then '班主任' when 2 then '讲师' when 3 then '学工主管' when 4 then '教研主管' else '未分配职位' end 职位,
    count(*) 人数
from tb_emp
group by job;
```



这里借助了MySQL提供的流程控制函数if(条件判断，为真取值，为假取值)

流程控制函数 case 表达式 when 值1 then 结果1 when 值2 then 结果2 else ...ehd；

### 七、多表设计

#### 1、一对多（多对一）

1、在一对多的关系中我们把多的一方的表叫做子表，把一的一方的表叫做父表。

2、一对多关系在数据表结构层面是实现：在多的一方的数据表中增加一个字段，用来关联一的一方的主键。

##### （1）外键约束

在多表关联中如何保证数据的一致性与完整性。

**物理外键**

概念：使用foreign key定义外键关联另一张表。

缺点：（1）影响增删改的效率（需要检查外键关系）

（2）仅用于单节点数据库，对于分布式、集群场景不适合。

（3）容易引发数据库的死锁问题，消耗性能。

**问题：**为什么容易引发数据库的死锁，数据库的死锁是什么？

**逻辑外键**

概念：在业务逻辑中通过代码来保证数据的一致性完整性，解决外键关联。

通过逻辑外键就可以很方便的解决上述问题。

#### 2、一对一

案例：用户与身份证信息的关系。

实践：一对一关系，多用于单表拆分，将一张表中查询频率比较高的基础字段放在一样表中，其他字段放在另一张表中。以提升操作效率。

比如：在一张表中既有用户的基本信息，又有用户的身份信息，但是对于基本信息的查询频率非常高，对于身份信息的查询频率非常低，那么我们就可以将这张表拆分成两张表，以提高查询效率。

实现：在任意一方加入外键，关联另外一方的主键，并且设置外键为唯一的（unique）

#### 3、多对多

实现：建立第三张中间表，中间表至少包含两个外键，分别关联两方主键。

#### 4、多表设计案例

**实际开发经验**：

1、中间表不需要设计create_time和updata_time字段。

2、多表设计的流程

（1）阅读页面原型和需求文档，分析各个模块涉及到的表，以及各个表之间的关系。

（2）根据页面原型和需求文档，分析每个表应该有哪些字段，这些字段应该有哪些约束，并创建表。

![image-20241128110042879](img/image-20241128110042879.png)

### 八、多表查询

#### 1、概述

多表查询：指从多张表中查询数据

笛卡尔积：是指在数学中两个集合的所有组合情况。（**在多表查询中需要通过条件去掉无效的笛卡尔积**）

#### 2、分类

连接查询

（1）内连接：相当于查询AB两个表中交集部分的数据。

（2）外连接

​	左外连接：查询左表的所有数据，包括两个表交集部分的数据。

​	右外连接：查询右表所有数据，包括两张表交集部分数据。

子查询

**这里的交集指的是有交集有联系的数据。**

#### 3、内连接

1、隐式内连接

```sql
-- ==============内连接=============
-- 查询员工的姓名，及所属的部门名称（隐式内连接实现）
select tb_emp.name, tb_dept.name from tb_emp, tb_dept where tb_emp.dept_id = tb_dept.id;
```



2、显示内连接

```sql
-- 查询员工的姓名，及所属的部门名称（显式内连接实现）
select tb_emp.name, tb_dept.name from tb_emp inner join tb_dept on tb_emp.dept_id = tb_dept.id;
```



inner可以省略

3、起别名

```sql
-- 给表起别名
select 员工表.name, 部门表.name from tb_emp as 员工表, tb_dept as 部门表 where 员工表.dept_id = 部门表.id;
```



**注意**：内连接只能查询出两个表中相互有关联的数据，如下：员工表里有17条数据，但只查出了16条，因为员工表中的陈友谅的部门是空值，它与部门表没有交集。

![image-20241128153617621](img/image-20241128153617621.png)

![image-20241128153754360](img/image-20241128153754360.png)

#### 4、外连接

1、左外连接

```sql
-- =============外连接============
-- 查询员工表所有员工的姓名，和对应的部门名称(左外连接)
select tb_emp.name, tb_dept.name from tb_emp left join tb_dept on tb_emp.dept_id = tb_dept.id;
```



2、右外连接

```sql
-- 查询部门表所有部门的名称，和对应的员工名称（右外连接）
select tb_emp.name, tb_dept.name from tb_emp right join tb_dept on tb_emp.dept_id = tb_dept.id;
```



注意：外连接可以查询出主查询表的所有数据，即使它与另外的表没有交集。

#### 5、子查询

1、**开发经验**：在子查询中一定要注意步骤的分解。

2、概述：

介绍：SQL语句中嵌套select语句，称为嵌套查询又称子查询。

子查询外部的语句可以是inster/update/delete/select中的任何一个。最常见的是select。

2、分类：

根据子查询返回的结果不同，将子查询分为4类。

标量子查询：子查询返回的结果为单个值（数字、字符串、日期等），最简单的形式。

常用的操作符：= <> > >= <= < 

```sql
-- ================子查询===============
-- 标量子查询
-- A。查询教研部的所有员工信息
select * from tb_emp where dept_id = (select id from tb_dept where name = '教研部');
-- B:查询在东方白入职之后的所有员工信息。
select * from tb_emp where entrydate > (select entrydate from tb_emp where name = '方东白');
```



列子查询：子查询返回的结果是一列。

常用的操作符in，not in等。

```sql
-- 列子查询
-- A：查询教研部和咨询部的所有员工信息

select * from tb_emp where dept_id in (select id from tb_dept where name in ('教研部','咨询部'));
```



这样也查不出那个dept_id为空的员工陈友谅的信息。

```sql
-- 列子查询
-- A：查询非教研部和咨询部的所有员工信息

select * from tb_emp where dept_id not in (select id from tb_dept where name in ('教研部','咨询部'));
```



#### 6、行子查询

子查询返回的结果是一行

常用的操作符：= <> in not in

#### 7、案例

内连接查询:

内连接查询where后面不仅可以写连接的条件，还可以写查询的条件。

```sql
-- 需求：
-- 1、查询价格低于10元的菜品的名称、价格及其菜品的分类名称。
select d.菜品名称, d.price, d.所属分类 from (select dish.name 菜品名称, price, category.name 所属分类 from dish, category where dish.category_id = category.id) d where d.price < 10;
select dish.name, dish.price, category.name
from dish,
     category
where dish.category_id = category.id
  and dish.price < 10;
```



外连接查询：

外连接查询时，on后面写连接的条件，where后面写查询的条件。

```sql
-- 查询所有价格在10元（含）到50元（含）之间，且 状态为起售的菜品，展示出菜品的名称、价格及其菜品的分类名称（即使菜品没有分类，也需要将菜品查询出来）
select dish.name, dish.price, category.name
from dish
         left join category on dish.category_id = category.id
where dish.price between 10 and 50
  and dish.status = 1;
```



内连接查询+分组查询

```sql
-- 3、查询出每个分类下最贵的菜品，展示出分类的名称、最贵的菜品的价格。
select category.name, max(dish.price)
from dish,
     category
where dish.category_id = category.id
group by category.name;
```



```sql
-- 4、查询各个分类下 菜品状态为起售，且该分类下菜品总数量大于等于3的分类名称。
select category.name
from dish,
     category
where dish.category_id = category.id and dish.status = 1
group by category.name
having count(*) >= 3;
```



多表连接查询：

多表连接查询写多个表的名字，用逗号分隔就行。

```sql
-- 5、查询出商务套餐A中包含了哪些菜品（展示出套餐名称、价格，包含的菜品名称、价格、份数）
select setmeal.name, setmeal.price, dish.name, dish.price, setmeal_dish.copies
from setmeal,
     dish,
     setmeal_dish
where dish.id = setmeal_dish.dish_id
  and setmeal.id = setmeal_dish.setmeal_id
  and setmeal.name = '商务套餐A';
```



子查询

```sql
-- 6、查询出低于菜品平均价格的菜品信息,展示出菜品名称，菜品价格。
select name, price from dish where price < (select avg(price) from dish);
```

**实际开发经验：**

在实际开发中能用连接查询就用连接查询，子查询效率不高。

### 九、事务

现有一个业务：解散学工部，所以该部门和部门下的员工都需要删除。

但是，如果部门删除成功了，而删除该部门的员工时失败了，就造成了数据的不一致问题。**怎么解决这个问题呢？用事务**

#### 一、概念

1、概念：事务是一组操作的集合，它是一个不可分割的工作单位。事务会把所有的操作作为一个整体一起向系统提交或撤销工作请求，即这些操作要么同时成功，要么同时失败。

一个事务中的所有SQL语句都执行成功时，执行commit操作，没都成功就执行rollback操作。

**注意**：默认MySQL的事务是自动提交的，也就是说当执行一条DML语句时，MySQL会自动隐式的提交事务。

2、操作

开启事务：start transaction;

提交事务：commit ;

回滚事务：rollback ;

```sql
-- ==================事务===================
-- 开启事务
start transaction;
-- 删除部门
delete from tb_dept where id = 1;
-- 删除部门下的员工
delete from tb_emp where dept_id = 1;
-- 提交事务
commit ;
-- 回滚事务
rollback ;
```



#### 二、事务四大特性（ACID）

1、原子性：事务是不可分割的原子单元，要么全部成功，要么全部失败。

2、一致性：事务完成时（完成提交或回滚），必须使所有的数据都保持一致状态。（所以即使有的操作没有执行成功也提交事务的玩儿法是不符合原则的，不要这么干！没意义）

3、隔离性：数据库系统提供的隔离机制，保证事务在不受外部并行操作影响的独立环境下运行。（提交或回滚事务后，事务会对整个数据库产生影响，否则只对自己的独立运行环境有影响。）

4、持久性：事务一旦提交或回滚，它对数据库当中数据的改变是永久的。

### 十、提升查询效率最有效的方式——索引

数据量越大，查询效率越慢，提高查询效率的有效方法是添加索引，索引可以将查询效率提升几百倍。

#### 一、数据库优化包括：

索引，SQL优化、分库分表

#### 二、概念

1、概念：索引是帮助数据库高效获取数据的**数据结构**（它是一种二叉搜索树的数据结构，每个节点中的值都和它对应的数据库的实际值相同，比该节点小的值放在左边，大的值放在右边。）

2、优缺点：

优点：

- 提高数据查询的效率，降低数据库的IO成本。
- 通过索引列对数据库进行排序，可以降低排序成本，降低CPU消耗。

IO成本：mysql的innodb存储引擎会把数据存储到磁盘上，这时候无论怎么优化SQL，都是需要从磁盘中读取数据到内存，就是IO成本，每次读取磁盘，至少读一页。

CPU成本：从磁盘读到数据后要放到内存中处理数据的过程，这是CPU成本。

缺点：

索引会占用存储空间

索引大大提高了查询效率，同时也降低了insert、delete、updata的效率。

#### 三、MySQL中索引的数据结构

MySQL数据库支持的索引结构有很多，如Hash索引、B+Tree索引、Full-Text索引等。我们平常所说的索引如果没有特别指明，一般指的是默认的B+Tree结构组织的索引。

1、默认是B+Tree树（多路平衡搜索树）

- B+Tree树的三个特点：
  一个节点中可以有n个key，有n个key就有n个指针，也就意味着这个节点会有n个子节点，多个子节点也就是所谓的多路。
- 非叶子节点只起到索引数据的作用，并不保存具体的节点。所有的节点都保存在叶子节点里。并且所有的key都会出现在叶子节点中，且在叶子节点中会保存这个key对应的数据。
- 叶子节点是按key的值进行由小到大排序的，并且在叶子节点形成了一个双向列表。

![image-20241205114524989](img/image-20241205114524989.png)

页是数据库管理磁盘的最小单位，一页是16KB。

#### 四、索引的操作语法

为一个表创建主键后，数据库或自动为该主键字段创建主键索引，主键索引的效率是最高的。

唯一性约束本身其实就是一个唯一索引。

```sql
-- ================索引操作================
-- 为tb_emp表的name字段创建一个索引
CREATE INDEX idx_emp_name ON tb_emp(name);
-- 查询tb表的索引信息
show index from tb_emp;
-- 删除tb_emp表的name的索引
drop index idx_emp_name on tb_emp;
```



如果一个数据表没有索引那么查询的时候就是全表扫描查询，如果查询的字段不是唯一的，那么会把整个表都扫描一遍。

**问题**：1、主键索引的效率是最高的，所以以后查询时尽量使用主键查询是不是？2、使用模糊匹配时索引就失效了，不过好像有解决方案。

## 三、Mabatis

Mybatis是一款优秀的持久层框架，用于简化JDBC的开发。

### 一、Mabatis入门

#### 一、快速入门

1、Mybatis操作数据库的底层逻辑和图形化界面操作数据库的底层逻辑是一样的。只不过图形化界面操作数据库，数据库将结果返回给图形化界面，图形化界面将其以二维表的形式呈现给我们。而Mybatis是在java程序中操作数据库，所以Mybatis会将数据库返回的结果自动封装在对应的实体类中。

2、要想实现自动封装，数据库表的字段名必须和实体类的属性名一样，如果数据库采用的是下划线命名，那实体类的属性就采用驼峰命名。

**3、SpringBoot整合MyBatis的步骤：**

**案例查询所有用户数据：**

（1）准备工作（创建SpringBoot项目，创建数据库表，创建对应实体类）

```sql
create table user(
                     id int unsigned primary key auto_increment comment 'ID',
                     name varchar(100) comment '姓名',
                     age tinyint unsigned comment '年龄',
                     gender tinyint unsigned comment '性别, 1:男, 2:女',
                     phone varchar(11) comment '手机号'
) comment '用户表';

insert into user(id, name, age, gender, phone) VALUES (null,'白眉鹰王',55,'1','18800000000');
insert into user(id, name, age, gender, phone) VALUES (null,'金毛狮王',45,'1','18800000001');
insert into user(id, name, age, gender, phone) VALUES (null,'青翼蝠王',38,'1','18800000002');
insert into user(id, name, age, gender, phone) VALUES (null,'紫衫龙王',42,'2','18800000003');
insert into user(id, name, age, gender, phone) VALUES (null,'光明左使',37,'1','18800000004');
insert into user(id, name, age, gender, phone) VALUES (null,'光明右使',48,'1','18800000005');

```



```java
package com.it.pojo;

public class User {
    private Integer id;
    private String name;
    private Short age;
    private Short gender;
    private String phone;

    public User(Integer id, String name, Short age, Short gender, String phone) {
        this.id = id;
        this.name = name;
        this.age = age;
        this.gender = gender;
        this.phone = phone;
    }

    public User() {
    }

    public Integer getId() {
        return id;
    }

    public void setId(Integer id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public Short getAge() {
        return age;
    }

    public void setAge(Short age) {
        this.age = age;
    }

    public Short getGender() {
        return gender;
    }

    public void setGender(Short gender) {
        this.gender = gender;
    }

    public String getPhone() {
        return phone;
    }

    public void setPhone(String phone) {
        this.phone = phone;
    }

    @Override
    public String toString() {
        return "User{" +
                "id=" + id +
                ", name='" + name + '\'' +
                ", age=" + age +
                ", gender=" + gender +
                ", phone='" + phone + '\'' +
                '}';
    }
}

```



注意：在实体类定义当中推荐使用包装类型。

（2）引入Mybatis依赖，配置Mybatis（配置数据库连接信息）

这是springboot整合mybatis整个的pom文件

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>3.4.0</version>
        <relativePath/> <!-- lookup parent from repository -->
    </parent>
    <groupId>com.it</groupId>
    <artifactId>springboot-mybatis-quickstart</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <name>springboot-mybatis-quickstart</name>
    <description>springboot-mybatis-quickstart</description>
    <url/>
    <licenses>
        <license/>
    </licenses>
    <developers>
        <developer/>
    </developers>
    <scm>
        <connection/>
        <developerConnection/>
        <tag/>
        <url/>
    </scm>
    <properties>
        <java.version>17</java.version>
    </properties>
    <dependencies>
<!--mybatis的起步依赖-->
        <dependency>
            <groupId>org.mybatis.spring.boot</groupId>
            <artifactId>mybatis-spring-boot-starter</artifactId>
            <version>3.0.4</version>
        </dependency>
<!--mysql官方发布的最新版本的驱动包-->
        <dependency>
            <groupId>com.mysql</groupId>
            <artifactId>mysql-connector-j</artifactId>
            <scope>runtime</scope>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>org.mybatis.spring.boot</groupId>
            <artifactId>mybatis-spring-boot-starter-test</artifactId>
            <version>3.0.4</version>
            <scope>test</scope>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>

</project>
```



```sql
spring.application.name=springboot-mybatis-quickstart

spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

spring.datasource.url=jdbc:mysql://localhost:3306/mybatis

spring.datasource.username=root

spring.datasource.password=BBMM197309130304
```

（3）编写SQL语句（注解/XML）

采用注解的方式编写SQL语句，需要按照Mybatis规范定义一个Mapper接口，在这个接口上写上一个@Mapper注解，在接口里面定义一个方法，在方法上写上要执行的SQL操作的注解，注解的（）中写上要执行的SQL语句，SQL操作的返回值会自动封装在方法的返回值中。想执行这个SQL语句就调用它对应的方法就可以。

**注意：**不需要为这个Mapper接口写实现类，因为在程序运行时会自动在Mybatis底层生成这个实现类的。

```java
package com.it.mapper;

import com.it.pojo.User;
import org.apache.ibatis.annotations.Mapper;
import org.apache.ibatis.annotations.Select;

import java.util.List;

@Mapper //在运行时会自动生成该接口的实现类对象（代理对象），并注入IOC容器中
public interface UserMapper {

    @Select("select * from user")
    public List<User> list();
}
```



（4）进行单元测试一下

```java
package com.it;

import com.it.mapper.UserMapper;
import com.it.pojo.User;
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;

import java.util.List;

@SpringBootTest //springboot整合单元测试的注解
class SpringbootMybatisQuickstartApplicationTests {

    @Autowired
    private UserMapper userMapper;
    @Test
    public void testListUser(){
        List<User> list = userMapper.list();
        list.stream().forEach(user -> {
            System.out.println(user);
        });
    }

}
```



4、配置数据库连接信息中的那四条连接信息通常称为数据库连接四要素。

问题：什么是javaSE中的动态代理技术。

#### 二、JDBC介绍

1、JDBC介绍：JDBC（Java DataBase Connectivty）是Sun公司提供的使用java语言操作数据库的一套API。

2、本质：

Sun公司定义的一套使用java语言操作所有关系型数据库的规范，即接口。

各个数据库厂商去实现这套接口，提供数据库驱动java包。

我们可以使用这套接口（JDBC）编程，真正执行的代码是数据库驱动包中的实现类。

#### 三、数据库连接池

1、数据库连接池：

- 数据库连接池是一个容器，负责管理和分配数据库连接（connection）。
- 它允许应用程序重复使用一个现有的数据库连接，而不是重新建立一个。
- 释放空闲时间超过最大空闲时间的连接，来避免因为没有释放连接而引起的数据库连接泄露。

2、数据库连接池的优点：

资源重用、提升系统响应速度、避免数据库连接遗漏问题。

3、DataSource接口：

它是Sun公司提供的数据库连接池统一接口，所有的第三方连接池必须实现该接口，且必须重写其中的getConnetion方法。

常用的连接池有：C3P0、DBCP（这两个有些过时）、Druid(阿里提供的，是效率最好的连接池之一)、Hikari(追光者 是SpringBoor默认的)

在springboot项目中怎么把默认的追光者连接池换成Druid连接池。

#### 四、Lombok

![image-20241205204329911](img/image-20241205204329911.png)

**lombok原理：**在编译时根据注解自动生成对应的方法。

**注意：**如果使用的idea版本比较低的话需要自己先下载lombok插件。

### 二、Mybatis基础操作

#### 一、环境准备

（1）准备数据库表，准备对应的实体类

```java
package com.it.pojo;

import lombok.AllArgsConstructor;
import lombok.Data;
import lombok.NoArgsConstructor;

import java.time.LocalDate;
import java.time.LocalDateTime;

@Data
@AllArgsConstructor
@NoArgsConstructor
public class Emp {
    private Integer id;
    private String username;
    private String password;
    private String name;
    private Short gender;
    private String image;
    private Short job;
    private LocalDate entrydate;
    private Integer deptId;
    private LocalDateTime createTime;
    private LocalDateTime updateTime;
}

```



（2）引入mybatis依赖，配置数据库连接信息

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>3.4.0</version>
        <relativePath/> <!-- lookup parent from repository -->
    </parent>
    <groupId>com.it</groupId>
    <artifactId>spring-mybatis-cdus</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <name>spring-mybatis-cdus</name>
    <description>spring-mybatis-cdus</description>
    <url/>
    <licenses>
        <license/>
    </licenses>
    <developers>
        <developer/>
    </developers>
    <scm>
        <connection/>
        <developerConnection/>
        <tag/>
        <url/>
    </scm>
    <properties>
        <java.version>17</java.version>
    </properties>
    <dependencies>
        <dependency>
            <groupId>org.mybatis.spring.boot</groupId>
            <artifactId>mybatis-spring-boot-starter</artifactId>
            <version>3.0.4</version>
        </dependency>

        <dependency>
            <groupId>com.mysql</groupId>
            <artifactId>mysql-connector-j</artifactId>
            <scope>runtime</scope>
        </dependency>
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <optional>true</optional>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>org.mybatis.spring.boot</groupId>
            <artifactId>mybatis-spring-boot-starter-test</artifactId>
            <version>3.0.4</version>
            <scope>test</scope>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <configuration>
                    <annotationProcessorPaths>
                        <path>
                            <groupId>org.projectlombok</groupId>
                            <artifactId>lombok</artifactId>
                        </path>
                    </annotationProcessorPaths>
                </configuration>
            </plugin>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
                <configuration>
                    <excludes>
                        <exclude>
                            <groupId>org.projectlombok</groupId>
                            <artifactId>lombok</artifactId>
                        </exclude>
                    </excludes>
                </configuration>
            </plugin>
        </plugins>
    </build>

</project>

```





```properties
spring.application.name=spring-mybatis-cdus

spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

spring.datasource.url=jdbc:mysql://localhost:3306/mybatis

spring.datasource.username=root

spring.datasource.password=BBMM197309130304
```



#### 二、删除

（1）创建mapper层接口

```java
package com.it.mapper;

import org.apache.ibatis.annotations.Delete;
import org.apache.ibatis.annotations.Mapper;
@Mapper
public interface EmpMapper {
    //根据Id删除数据
    @Delete("delete from emp where id = #{id}")
    public void delete(Integer id);
}
```



(4)测试类

```java
package com.it;

import com.it.mapper.EmpMapper;
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;

@SpringBootTest
class SpringMybatisCdusApplicationTests {

    @Autowired
    private EmpMapper empMapper;
    @Test
    public void testDelete(){
        empMapper.delete(17);
    }
}
```



#### 三、预编译SQL

![image-20241206002452122](img/image-20241206002452122.png)

SQL注入：通过操作输入的数据来修改事先定义好的SQL语句，以达到执行代码对服务器进行攻击的方法。

如何在Mybatis中使用预编译的SQL语句：只需要在写SQL语句时用#{}占位符即可。

预编译sql为什么性能高：因为数据库管理系统会将已经执行过SQL缓存起来，如果下次相同的SQL再来执行就不用重新编译了，直接执行就行。

**面试题：**

参数占位符：
#{}：

- 执行SQL时会将#{}替换为？，生成预编译SQL，会自动设置参数值。
- 使用时机：参数传递，都使用#{}。

${}:

- 拼接SQL，直接将参数拼接到SQL语句中，存在SQL注入问题。
- 使用时机：对表名、字段名进行动态设置时使用。

#### 四、Mybatis日志输出

可以在application.properties中打开mybatis的日志，并指定输出到控制台。

```xml
spring.application.name=spring-mybatis-cdus

spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

spring.datasource.url=jdbc:mysql://localhost:3306/mybatis

spring.datasource.username=root

spring.datasource.password=BBMM197309130304

mybatis.configuration.log-impl=org.apache.ibatis.logging.stdout.StdOutImpl
mybatis.configuration.map-underscore-to-camel-case=true
```



#### 五、新增

```java
package com.it.mapper;

import com.it.pojo.Emp;
import org.apache.ibatis.annotations.Delete;
import org.apache.ibatis.annotations.Insert;
import org.apache.ibatis.annotations.Mapper;
@Mapper
public interface EmpMapper {
    //新增员工
    @Insert("insert into emp (username, name, gender, image, job, entrydate, dept_id, create_time, update_time)" +
            "values (#{username},#{name},#{gender},#{image},#{job},#{entrydate},#{deptId},#{createTime},#{updateTime});")
    public void insert(Emp emp);
}
```



如果参数过多时可以用一个实体对象封装这个参数，在SQL语句中用#{}占位符接收参数，#{}中的名字是实体对象属性的名字。

```java
package com.it;

import com.it.mapper.EmpMapper;
import com.it.pojo.Emp;
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;

import java.time.LocalDate;
import java.time.LocalDateTime;

@SpringBootTest
class SpringMybatisCdusApplicationTests {

    @Autowired
    private EmpMapper empMapper;
    @Test
    public void testInsert(){
        Emp emp = new Emp();
        emp.setUsername("Tom");
        emp.setName("汤姆");
        emp.setGender((short)1);
        emp.setImage("i.jpg");
        emp.setJob((short)1);
        emp.setEntrydate(LocalDate.of(2000,1,1));
        emp.setCreateTime(LocalDateTime.now());
        emp.setUpdateTime(LocalDateTime.now());
        emp.setDeptId(1);
        //执行新增员工信息操作
        empMapper.insert(emp);
    }
}

```

##### 主键返回：

1、描述：在数据添加成功后，需要获取插入数据库数据的主键。如：添加套餐数据时，需要维护套餐菜品表这张中间表。需要先保存套餐信息，并获取套餐ID，然后将套餐id记录在中间表中。

2、实现：

```sql
package com.it.mapper;

import com.it.pojo.Emp;
import org.apache.ibatis.annotations.Delete;
import org.apache.ibatis.annotations.Insert;
import org.apache.ibatis.annotations.Mapper;
import org.apache.ibatis.annotations.Options;

@Mapper
public interface EmpMapper {
    //新增员工
    @Options(useGeneratedKeys = true, keyProperty = "id") //会将生成的主键值自动赋值给emp对象的id属性
    @Insert("insert into emp (username, name, gender, image, job, entrydate, dept_id, create_time, update_time)" +
            "values (#{username},#{name},#{gender},#{image},#{job},#{entrydate},#{deptId},#{createTime},#{updateTime});")
    public void insert(Emp emp);
}
```



#### 六、更新

```java
package com.it.mapper;

import com.it.pojo.Emp;
import org.apache.ibatis.annotations.*;

@Mapper
public interface EmpMapper {
   
    //更新数据
    @Update("update emp set username = #{username}, name = #{name}, gender = #{gender}, image = #{image}," +
            "job = #{job}, entrydate = #{entrydate}, dept_id = #{deptId}, update_time = #{updateTime} where id = #{id};")
    public void update(Emp emp);
}
```



```java
package com.it;

import com.it.mapper.EmpMapper;
import com.it.pojo.Emp;
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;

import java.time.LocalDate;
import java.time.LocalDateTime;

@SpringBootTest
class SpringMybatisCdusApplicationTests {

    @Autowired
    private EmpMapper empMapper;
    
    @Test
    public void testUpdate(){
        Emp emp = new Emp();
        emp.setId(18);
        emp.setUsername("Tom1");
        emp.setName("汤姆1");
        emp.setGender((short)1);
        emp.setImage("1.jpg");
        emp.setJob((short)1);
        emp.setEntrydate(LocalDate.of(2000,1,1));
        emp.setUpdateTime(LocalDateTime.now());
        emp.setDeptId(1);
        //执行更新员工信息操作
        empMapper.update(emp);
    }
}
```



#### 七、查询（根据id查询）

1、Mybatis数据封装

实体类属性名和数据库表**查询**返回的字段名一致，mybatis会自动封装。

如果实体类属性名和数据库表**查询**返回的字段名不一致，不能自动封装。

解决方案1：

```java
package com.it.mapper;

import com.it.pojo.Emp;
import org.apache.ibatis.annotations.*;

@Mapper
public interface EmpMapper {
   
    //根据id查询员工
    //方案1：给字段起别名，让字段名与实体类属性名一致
    @Select("select id, username, password, name, gender, image, job, entrydate," +
            "dept_id as deptId, create_time as createTime, update_time as updateTime from emp where id = #{id};")
    public Emp getById(Integer id);

   
}
```



```java
package com.it;

import com.it.mapper.EmpMapper;
import com.it.pojo.Emp;
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;

import java.time.LocalDate;
import java.time.LocalDateTime;

@SpringBootTest
class SpringMybatisCdusApplicationTests {

    @Autowired
    private EmpMapper empMapper;
    
    //根据id查询员工
    @Test
    public void testGetById(){
        Emp emp = empMapper.getById(20);
        System.out.println(emp);
    }
}
```

解决方案2：

```java
package com.it.mapper;

import com.it.pojo.Emp;
import org.apache.ibatis.annotations.*;

@Mapper
public interface EmpMapper {
    
    //方案2：通过@Results @Result注解手动映射封装
    @Results({
            @Result(column = "dept_id", property = "deptId"),
            @Result(column = "create_time", property = "createTime"),
            @Result(column = "update_time", property = "updateTime")
    })
    @Select("select * from emp where id = #{id};")
    public Emp getById(Integer id);
}
```



解决方案3：开启mybatis的驼峰命名自动映射开关

```properties
spring.application.name=spring-mybatis-cdus

spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

spring.datasource.url=jdbc:mysql://localhost:3306/mybatis

spring.datasource.username=root

spring.datasource.password=BBMM197309130304

mybatis.configuration.log-impl=org.apache.ibatis.logging.stdout.StdOutImpl
mybatis.configuration.map-underscore-to-camel-case=true
```



```java
package com.it.mapper;

import com.it.pojo.Emp;
import org.apache.ibatis.annotations.*;

import java.time.LocalDate;
import java.util.List;

@Mapper
public interface EmpMapper {
    
    //解决方案3：开启mybatis的驼峰命名自动配置开关
    @Select("select * from emp where id = #{id};")
    public Emp getById(Integer id);
   
}
```

#### 八、查询（条件查询）

```java
package com.it.mapper;

import com.it.pojo.Emp;
import org.apache.ibatis.annotations.*;

import java.time.LocalDate;
import java.util.List;

@Mapper
public interface EmpMapper {
   
    //条件查询员工信息
    @Select("select * from emp where name like concat('%', #{name}, '%') and gender = #{gender} and " +
            "entrydate between #{star} and #{end} order by update_time desc;")
    public List<Emp> list(String name, Short gender, LocalDate star, LocalDate end);
}
```



注意：因为？不能在''里面，所以使用SQL的一个函数concat()，这是一个字符串拼接函数。当然也可以使用${}，但是不安全、性能低，因为不是预编译的SQL，所以不推荐使用。

### 三、XML映射文件

#### 一、定义mybatis的XML映射文件的规范

1、xml映射文件的名字与mapper接口的名字一致，并且将xml映射文件与Mapper接口放置在同一包下（创建包时用/分级，别用.）。

2、xml映射文件的namespace属性值与Mapper接口的全限定名一致。

3、xml映射文件中sql语句的id属性的值与mapper接口的方法名一致，并保持返回类型一致（类型是单挑记录所封装的类型）。

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.it.mapper.EmpMapper">
<!--resultType单条记录所封装的类型-->
    <select id="list" resultType="com.it.pojo.Emp">
        select * from emp where name like concat('%', #{name}, '%') and gender = #{gender} and
                                entrydate between #{star} and #{end} order by update_time desc;
    </select>
</mapper>
```



```java
package com.it.mapper;

import com.it.pojo.Emp;
import org.apache.ibatis.annotations.*;

import java.time.LocalDate;
import java.util.List;

@Mapper
public interface EmpMapper {
    
    public List<Emp> list(String name, Short gender, LocalDate star, LocalDate end);
    
}
```



MybatisX是一款基于IDEA的快速开发Mybatis的插件，为效率而生。

#### 二、使用时机

使用mybatis的注解主要来完成一些简单的增删改查的功能。如果需要实现复杂的SQL功能，建议使用XML来配置映射语句。

#### 四、Mybatis动态SQL

##### 一、if标签和where标签

if标签用来判断条件是否成立，使用test属性进行条件判断，如果判断结果为true，则拼接标签里的SQL。

where标签只会在子元素有内容的情况下才插入where,而且会自动去除句子中多余的and或or。

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.it.mapper.EmpMapper">
<!--resultType单条记录所封装的类型-->
    <select id="list" resultType="com.it.pojo.Emp">
        select *
        from emp
        <where>
          <if test="name != null">
            name like concat('%', #{name}, '%')
          </if>
          <if test="gender != null">
            and gender = #{gender}
          </if>
          <if test="star != null and end != null">
            and entrydate between #{star} and #{end}
          </if>
        order by update_time desc;
        </where>
    </select>
</mapper>
```



```java
package com.it.mapper;

import com.it.pojo.Emp;
import org.apache.ibatis.annotations.*;

import java.time.LocalDate;
import java.util.List;

@Mapper
public interface EmpMapper {
   
    //条件查询员工信息
    /*@Select("select * from emp where name like concat('%', #{name}, '%') and gender = #{gender} and " +
            "entrydate between #{star} and #{end} order by update_time desc;")
    public List<Emp> list(String name, Short gender, LocalDate star, LocalDate end);*/
    public List<Emp> list(String name, Short gender, LocalDate star, LocalDate end);

}
```



##### 二、案例(set标签)

完善更新员工功能，修改为动态更新员工数据信息

1、需求：动态更新员工信息，更新时如果传递有值则更新，如果传递没值则不更新。

2、解决方案：动态SQL。

3、set标签：用在update更新语句中，它有set关键字的作用，并且可以删除多余的，号。

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.it.mapper.EmpMapper">
    <update id="update2">
        update emp
        <set>
            <if test="username != null"> username = #{username},</if>
            <if test="name != null">name     = #{name},</if>
            <if test="gender != null">gender   = #{gender},</if>
            <if test="image != null">image    = #{image},</if>
            <if test="job != null">job = #{job},</if>
            <if test="entrydate != null">entrydate = #{entrydate},</if>
            <if test="deptId != null">dept_id = #{deptId},</if>
            <if test="updateTime != null">update_time = #{updateTime}</if>
        </set>
        where id = #{id};
    </update>
</mapper>
```

##### 三、foreach标签

属性：

collection：要遍历集合名称

item：集合遍历出来的元素

separator：遍历时用的分割符

open：遍历开始前拼接的片段

close：遍历结束后拼接的片段

**实践开发经验：**foreach标签主要是用于这种批量操作的时候的。

```java
package com.it.mapper;

import com.it.pojo.Emp;
import org.apache.ibatis.annotations.*;

import java.time.LocalDate;
import java.util.List;

@Mapper
public interface EmpMapper {
    //批量删除员工数据
    public void deleteByIds(List<Integer> ids);
}
```



```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.it.mapper.EmpMapper">
    <delete id="deleteByIds">
        delete
        from emp
        where id in
              <foreach collection="ids" item="id" separator="," open="(" close=")">
                #{id}
              </foreach>
    </delete>
</mapper>
```



```java
package com.it;

import com.it.mapper.EmpMapper;
import com.it.pojo.Emp;
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;

import java.time.LocalDate;
import java.time.LocalDateTime;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

@SpringBootTest
class SpringMybatisCdusApplicationTests {

    @Autowired
    private EmpMapper empMapper;
    @Test
    public void testDeleteByIds(){
        List<Integer> list = Arrays.asList(13, 14, 15);
        empMapper.deleteByIds(list);
    }
}
```



##### 四、`<sql>`和 `<include>`

如果在mybatis的xml配置文件中存在很多重复的sql片段，那我们就可以将其抽取出来，然后在需要用到的地方引入。这样有利于维护。

`<sql>` ：定义可重用的sql片段。通过属性id指定该片段的唯一标识。

`<include>` :通过属性refid，指定包含的SQL片段。

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.it.mapper.EmpMapper">
    <sql id="commenSelect">
        select id, username, password, name, gender, image, job, entrydate, dept_id, create_time, 			 		 update_time
        from emp
    </sql>
    
    <!--resultType单条记录所封装的类型-->
    <select id="list" resultType="com.it.pojo.Emp">
        <include refid="commenSelect"/>
        <where>
          <if test="name != null">
            name like concat('%', #{name}, '%')
          </if>
          <if test="gender != null">
            and gender = #{gender}
          </if>
          <if test="star != null and end != null">
            and entrydate between #{star} and #{end}
          </if>
        order by update_time desc;
        </where>
    </select>
</mapper>
```



# 三、Web前端开发

## 一、初识Web前端

1、web网页有哪些组车部分：文字、图片、音频、视频、超链接。

2、前端的代码是如何转换成用户眼中看到的网页的：通过浏览器内核解析渲染成用户看到的网页。浏览器中对代码进行解析渲染的部分称为浏览器内核。

3、每种浏览器的内核都是不一样的，怎么规范他们解析渲染出同一个前端代码得到的页面是一样的呢，需要他们遵守web标准。

### 一、web标准

1、web标准也称为网页标准，有一系列的标准组成，大部分由W3C（万维网联盟）负责制定。

2、web前端的三个组成部分：

HTML:负责网页的结构（页面元素和内容）

CSS：负责页面的样式（页面元素的外观、位置等页面样式，如颜色、大小等）

JavaScript：负责页面的动态交互。

## 二、HTML、CSS

### 一、什么是HTML、CSS

1、HTML：超文本标记语言

超文本：超越了普通文本的限制，比普通文本更强大。除了文字信息，还可以定义图片、视频、音频等。

标记语言：由标签构成的语言。

HTML语言直接在浏览器中运行，HTML标签由浏览器解析。

2、CSS：层叠样式表

用于控制页面的样式。

### 二、HTML快速入门

1、HTML结构标签

```html
<html>
    <head>
        <title>HTML入门</title>
    </head>
    <body>
        <h1>
            HTML快速入门
        </h1>
        <img src='1.jpg/'>
    </body>
</html>
```



2、HTML的特点：

（1）HTML不区分大小写

（2）HTML的语法比较松散

（3）HTML的属性值可以被单引号括起来，也可以被双引号括起来。

### 三、HTML基础标签CSS基本样式

#### 1、图片标签：`<img>`

src：指定图像的url（绝对路径/相对路径）

width：图像的宽度（像素/相对于父元素的百分比）

height：图像的高度（像素/相对于父元素的百分比）

路径书写方式：

绝对路径：绝对磁盘路径、绝对网络路径

相对路径：./表示当前目录  ../表示上一级目录

一般我们在设置图片的宽度和高度时只设置一个，另一个会等比例缩放。

```html
<!-- 表明文档类型是html类型 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <!-- 字符集为UTF-8 -->
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>焦点访谈：中国底气 新思想夯实大国粮仓</title>
</head>
<body>
    <img src="https://i2.sinaimg.cn/dy/deco/2012/0613/yocc20120613img01/news_logo.png">新浪政务>正文
    <h1>焦点访谈：中国底气 新思想夯实大国粮仓</h1>
    <hr>
    2023年03月02日 21:50 央视网
    <hr>
</body>
</html>
```



#### 2、标题标签：`<h1>-<h6>`

#### 3、水平线标签：`<hr>`

#### 4、在html中引入css的方式

行内样式：写在标签的style属性中（不推荐）。

- style属性将覆盖任何全局的样式设定，例如在 `<style>` 标签或在外部样式表中规定的样式。
- style属性可用于任何 HTML 元素（将验证任何 HTML 元素上，然而未必有用）。

内嵌样式：写在head标签中的style标签中。（可以写在页面的任何地方，但通常约定写在head标签中）

外联样式：写在一个单独的.css文件中，需要通过link标签引入。

```html
<!-- 表明文档类型是html类型 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <!-- 字符集为UTF-8 -->
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>焦点访谈：中国底气 新思想夯实大国粮仓</title>
    <!-- 方式二：内嵌样式 -->
     <style>
        h1 {
            color: #4d4f53;
        }
     </style>
     <!-- 方式三：外联样式 -->
      <!-- <link rel="stylesheet" href="./css/news.css"> -->
</head>
<body>
    <img src="https://i2.sinaimg.cn/dy/deco/2012/0613/yocc20120613img01/news_logo.png">新浪政务>正文
    <!-- 方式一：行内样式 -->
    <!-- <h1 style="color: red;">焦点访谈：中国底气 新思想夯实大国粮仓</h1> -->
    <h1>焦点访谈：中国底气 新思想夯实大国粮仓</h1>
    <hr>
    2023年03月02日 21:50 央视网
    <hr>
</body>
</html>
```



news.css

```css
h1 {
    color: red;
}
```



#### 5、css常用属性

（1）color：设置文本的颜色。

（2）font-size：设置字体大小(记得加px)

（3）text-decoration：规定添加到文本的修饰。如加下划线、上划线、串线。如果后代元素没有自己的装饰，祖先元素上设置的装饰会“延伸”到后代元素中。不要求用户代理支持 blink。

（4）text-indent 属性：规定文本块中首行文本的缩进。用于定义块级元素中第一个内容行的缩进。

（5）ine-height 属性：设置行间的距离（行高）。该属性会影响行框的布局。在应用到一个块级元素时，它定义了该元素中基线之间的最小距离而不是最大距离。line-height 与 font-size 的计算值之差（在 CSS 中成为“行间距”）分为两半，分别加到一个文本行内容的顶部和底部。可以包含这些内容的最小框就是行框。

（6）text-align 属性：规定元素中的文本的水平对齐方式。该属性通过指定行框与哪个点对齐，从而设置块级元素内文本的水平对齐方式。

#### 6、css选择器

优先级：id选择器>类选择器>元素选择器

类名可以重复，id名不能重复，是唯一的。

```html
<!-- 表明文档类型是html类型 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <!-- 字符集为UTF-8 -->
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>焦点访谈：中国底气 新思想夯实大国粮仓</title>
    <!-- 方式二：内嵌样式 -->
     <style>
        h1 {
            color: #4d4f53;
        }
        /* 元素选择器 */
        /* span {
            color: #968D92;
        } */
        /* 类选择器 */
        /* .cla {
            color: #968D92;
        } */
        #time {
            color: #968D92;
            font-size: 13px;
        }
     </style>
     <!-- 方式三：外联样式 -->
      <!-- <link rel="stylesheet" href="./css/news.css"> -->
</head>
<body>
    <img src="https://i2.sinaimg.cn/dy/deco/2012/0613/yocc20120613img01/news_logo.png">新浪政务>正文
    <!-- 方式一：行内样式 -->
    <!-- <h1 style="color: red;">焦点访谈：中国底气 新思想夯实大国粮仓</h1> -->
    <h1>焦点访谈：中国底气 新思想夯实大国粮仓</h1>
    <hr>
    <span class="cla" id="time">2023年03月02日 21:50 </span><span class="cla">央视网</span>
    <hr>
</body>
</html>
```



#### 7、`<span>` 标签：

是一个会在开发中大量用到的没有语意的布局标签，一行可以显示多个（用来组织行内元素），宽度和高度由其中的内容撑开。

#### 8、超链接

```html
<a href="https://news.cctv.com/2023/03/02/ARTIUCKFf9kE9eXgYE46ugx3230302.shtml" target="_blank">央视网</a>
```



属性：

href：指定要访问的资源的url。

target：指定要在此页面打卡资源页面还是要在新页面打开。

​	_self：在此页面打开（默认值）

​	_blank：在新页面打开。

```html
<span class="cla"> <a href="https://news.cctv.com/2023/03/02/ARTIUCKFf9kE9eXgYE46ugx3230302.shtml" target="_blank">央视网</a> </span>
```



上述情况如果同时用css的元素选择器为span标签和a标签设置了样式，央视网这三个字会采取a标签的样式，我认为是因为a标签离它近。

```html
<!-- 表明文档类型是html类型 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <!-- 字符集为UTF-8 -->
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>焦点访谈：中国底气 新思想夯实大国粮仓</title>
    
     <style>
        h1 {
            color: #4d4f53;
        }
        
        #time {
            color: #968D92;
            font-size: 13px;
        }
        a {
            color: black;
            text-decoration: none;
        }
        
     </style>
     
</head>
<body>
    <img src="https://i2.sinaimg.cn/dy/deco/2012/0613/yocc20120613img01/news_logo.png"> <a href="https://gov.sina.com.cn/">新浪政务</a> > 正文
    <h1>焦点访谈：中国底气 新思想夯实大国粮仓</h1>
    <hr>
    <span class="cla" id="time">2023年03月02日 21:50 </span> <span class="cla"> <a href="https://news.cctv.com/2023/03/02/ARTIUCKFf9kE9eXgYE46ugx3230302.shtml" target="_blank">央视网</a> </span>
    <hr>
</body>
</html>
```



#### 9、视频标签：`<video>` 

src：规定视频的url。

controls：写上这个属性就显示播放控件。因为其属性名和属性值是相同的，所以可以把属性值省略不写，只写属性名。

width：设置视频播放器的宽度

height：设置视频播放器的高度

#### 10、音频播放器：`<audio>` 

src：规定音频的url。

controls：写上这个属性就显示播放控件。因为其属性名和属性值是相同的，所以可以把属性值省略不写，只写属性名。

注意：在html中，如果属性名和属性值相同，那么可以省略属性值。

#### 11、段落标签：`<p>` 

#### 12、文本加粗标签：`<b>` 和 `<strong>` 

`<strong>` 标签是有语义的。

```html
<!-- 表明文档类型是html类型 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <!-- 字符集为UTF-8 -->
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>焦点访谈：中国底气 新思想夯实大国粮仓</title>
    
     <style>
        h1 {
            color: #4d4f53;
        }
        
        #time {
            color: #968D92;
            font-size: 13px;
        }
        a {
            color: black;
            text-decoration: none;
        }
        p {
            text-indent: 35px;
            line-height: 40px;
        }
        #plast {
            text-align: right;
        }
     </style>
     
</head>
<body>
    <img src="https://i2.sinaimg.cn/dy/deco/2012/0613/yocc20120613img01/news_logo.png"> <a href="https://gov.sina.com.cn/">新浪政务</a> > 正文
    <h1>焦点访谈：中国底气 新思想夯实大国粮仓</h1>
    <hr>
    <span class="cla" id="time">2023年03月02日 21:50 </span> <span class="cla"> <a href="https://news.cctv.com/2023/03/02/ARTIUCKFf9kE9eXgYE46ugx3230302.shtml" target="_blank">央视网</a> </span>
    <hr>
    <!-- 正文部分 -->
     <video src="./video/1.mp4" controls width="950px"></video>
     <p>
        <strong>央视网消息</strong>（焦点访谈）：党的十八大以来，以习近平同志为核心的党中央始终把解决粮食安全问题作为治国理政的头等大事，
        重农抓粮一系列政策举措有力有效，我国粮食产量站稳1.3万亿斤台阶，实现谷物基本自给、口粮绝对安全。我们把饭碗牢牢端在自己手中，
        为保障经济社会发展提供了坚实支撑，为应对各种风险挑战赢得了主动。连续八年1.3万亿斤，这个沉甸甸的数据是如何取得的呢？
    </p>
    <p>人勤春来早，春耕农事忙。立春之后，由南到北，我国春耕春管工作陆续展开，春天的田野处处生机盎然。</p>
    <img src="./img/1.jpg">
    <p>今年，我国启动了新一轮千亿斤粮食产能提升行动，这是一个新的起点。2015年以来，我国粮食产量连续8年稳定在1.3万亿斤以上，
        人均粮食占有量始终稳稳高于国际公认的400公斤粮食安全线。从十年前的约12200亿斤到2022年的约13700亿斤，粮食产量提高了1500亿斤。
    </p>
    <p>
        中国式现代化一个重要的中国特色是人口规模巨大的现代化。我们粮食生产的发展，意味着我们要立足国内，解决14亿多人吃饭的问题。仓廪实，天下安。保障粮食安全是一个永恒的课题，任何时候都不能放松。在以习近平同志为核心的党中央坚强领导下，亿万中国人民辛勤耕耘、不懈奋斗，我们就一定能够牢牢守住粮食安全这一“国之大者”，把中国人的饭碗牢牢端在自己手中，夯实中国式现代化基础。
    </p>
    <p id="plast">责任编辑：王树淼SN242</p>
</body>
</html>
```



注意：在html中无论输入多少个空格，只会显示一个空格，可以使用空格占位符：&nbsp。

#### 13、css中一个重要的内容——盒子模型

1、盒子：页面中所有的元素（标签）都可以看作是一个盒子。由盒子将页面的各个组成内容包裹在一个矩形区域内，通过盒子的视角更方便的进行页面布局。

2、盒子模型组成

![image-20241219164249344](img/image-20241219164249344.png)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        div {
            width: 200px;
            height: 200px;
            border: 10px solid transparent;
            box-sizing: border-box;
            padding: 20px;
            margin: 30px;
            background-color: aquamarine;
        }
    </style>
</head>
<body>
    <div>
        这是一个盒子
    </div>
</body>
</html>
```



设置了box-sizing：border-box后，width和height设置的都是border及其包裹部分的样式。不设置box-sizing：border-box，width和height设置的就是内容（content）部分的样式。不管设置不设置box-sizing，background-color设置的都是content部分+padding部分+border部分的背景色。

**技巧**：想让盒子模型居中展示可以通过margin来设置。

#### 14、布局标签

1、布局标签：`<div>` `和` `<spen>` 是两个没有语义的布局标签。

2、div标签：

- ​	一行只显示一个。
- ​	宽度默认是父元素的宽度，高度默认由内容撑开。
- ​	可设置宽高（width、height,一般就指定一个，另一个会自动等比例缩放）

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>盒子模型</title>
    <style>
        div {
            width: 200px;
            height: 200px;
            box-sizing: border-box; /* 指定width height为盒子的高宽 如果不指定这个，上面设置的宽高默认是为content区域设置的*/
            background-color: aquamarine; /* 背景色 */
            
            padding: 20px; /* 内边距, 上 右 下 左 */
            border: 10px solid red; /* 边框, 宽度 线条类型 颜色 */
            margin: 30px; /* 外边距, 上 右 下 左 */
        }
    </style>
</head>

<body>
    
    <div>
        A A A A A A A A A A A A A A A A A A A A A A A A A A A A A A A A A A 
    </div>

</body>
</html>
```

2、spen标签

​	一行可以显示多个。

​	宽度和高度由内容撑开。

​	不可以设置宽高。

### 四、表格标签

1、场景：在网页中以表格（行、列）形式整齐展示数据。

2、标签：

![image-20241224210511567](img/image-20241224210511567.png)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        table {
            text-align: center;
        }
    </style>
</head>
<body>
    <table border="1px" width="600px" cellspacing="0">
        <tr>
            <th>序号</th>
            <th>品牌Logo</th>
            <th>品牌名称</th>
            <th>企业名称</th>
        </tr>
        <tr>
            <td>1</td>
            <td><img src="./img/huawei.jpg" width="100px"></td>
            <td>华为</td>
            <td>华为技术有限公司</td>
        </tr>
        <tr>
            <td>2</td>
            <td><img src="./img/alibaba.jpg" width="100px"></td>
            <td>阿里</td>
            <td>阿里巴巴集团控股有限公司</td>
        </tr>
    </table>
</body>
</html>
```



width设置表格的宽，其中将border的宽囊括进去了，比如上述代码中，实际表格内容部分的宽为580px。th标签中的内容默认就是居中的。

### 五、表单标签

1、场景：主要负责数据采集功能，如登录和注册等的数据采集。

2、标签：`<form>` 

3、表单项：不同类型的input元素、下拉列表、文本域。

（1）`<input>`  可以定义很多类型的表单项，通过type属性可定义不同类型的表单项。

（2）`<select>` 定义下拉列表

（3）`<textarea>` 定义文本域

4、属性

- action：规定当提交表单时向何处发送表单数据，URL。不指定默认提交到当前页面，开发时写要提交到的后端的地址。
- method：规定用于发送表单数据的方式。

​	get：在url后面拼接提交的表单数据，由于url长度是有限的，所有能提交的数据量也是有限的。

​	post：在请求体中传递数据，能提交的数据量不限。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HTML表单标签</title>
</head>
<body>
    <form action="" method="get">
        用户名：<input type="text" name="username">
        年龄：<input type="text" name="age">
        <input type="submit" value="提交">
    </form>
</body>
</html>
```



注意：表单中的数据要想成功的采集并提交，name属性是必须要有的。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>表单项标签</title>
</head>
<body>
    <form action="" method="post">
        姓名：<input type="text" name="username"> <br><br>
        密码：<input type="password" name="password"><br><br>
        性别：<label><input type="radio" name="gender" value="1">男</label>
             <label><input type="radio" name="gender" value="2">女</label><br><br>
        爱好：<label><input type="checkbox" name="hobby" value="java">java</label>
             <label><input type="checkbox" name="hobby" value="game">game</label>
             <label><input type="checkbox" name="hobby" value="sing">sing</label><br><br>
        图像：<input type="file" name="image"> <br><br>
        生日：<input type="date" name="date"> <br><br>
        日期：<input type="time" name="time"> <br><br>
        日期时间：<input type="datetime-local" name="datetime-local"><br><br>
        邮箱：<input type="email" name="email"><br><br>
        年龄：<input type="number" name="age"><br><br>
        学历：<select name="degree">
            <option value="">-----------请选择-----------</option>
            <option value="1">大专</option>
            <option value="2">本科</option>
            <option value="3">硕士</option>
            <option value="4">博士</option>
        </select> <br><br>
        描述：<textarea name="description" cols="30" rows="10"></textarea> <br><br>
        <input type="hidden" name="id" value="1"> 
        <!-- 表单常见按钮  -->
         <input type="button" value="按钮">
         <input type="submit" value="提交">
         <input type="reset" value="重置">
         <br>
    </form>
</body>
</html>
```



![image-20241225192704664](img/image-20241225192704664.png)

单选框和复选框标签中的value属性中的值就是要提交的值。还有下拉列表 `<sekect>`标签的子标签 `<option>` 中的value属性，也是提交表单时真正提交到后端的值。

**`<lable>` 标签**：该标签为input元素定义标注（标记）

lable元素不会向用户呈现任何特殊效果。不过，它改进了鼠标的使用。如果你在lable包裹的区域内点击其包裹的文本区域，那么浏览器就会自动将焦点转移到此lable包裹的表单控件上。

## 三、JavaScript

### 一、JavaScript介绍

JavaScript是一门跨平台、面向对象的脚本语言。是用来控制网页行为的，用来使网页可交互。

JavaScript和java是完全不同的语言，不论是概念还是设计。但是基础语法类似。

JavaScript在1995年由BrendanEich发明，并于1997年成为ECMA标准。

ECMAScript(ES6)是最新版本的javaScripte版本(发布于2015年)。

ECMA国际：制定了标准化的脚本程序设计语言ECMAScript,这种语言得到了广泛的应用，而JavaScript是遵循ECMAScript标准的。

JavaScript是由浏览器解释执行的。

### 二、JS的引入方式（JS代码与HTML代码的结合方式）

#### 1、内部脚本

将JS代码定义在html页面代码中。

- JS代码必须写在 `<script></script>` 中。
- 在html代码中，可以在任意地方放置任意数量的 `<script>` 
- 一般会将`<script>` 标签放到body标签的下面，这样可以提高页面的显示速度。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
<!-- 内部脚本 -->
<script>
    alert("holle js")
</script>
</html>
```



#### 2、外部脚本

将js代码写在一个单独的.js文件中，然后在html代码中在 `<script>` 标签中引入对应的这个js文件。

- 外部js文件中，只包含js代码，不包含script标签。
- 引入用的script标签不能自闭和。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
<!-- 内部脚本 -->
<!-- <script>
    alert("holle js")
</script> -->
<script src="../js/demo.js"></script>
</html>
```



demo.js

```js
alert("hello js")
```



### 三、JS基础语法

#### 一、书写语法

- 区分大小写
- 每行结尾；可有可无。

#### 二、输出语句

在javaScript中有三种输出方式：

使用window.alert("hello js")弹出警告框

使用document.write("hello js")写入浏览器页面中。

使用console.log("hello js")写入浏览器控制台中

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
<script>
    // 方式一：弹出警告框
    window.alert("hello js");
    // 方式二：写入浏览器页面中。
    document.write("hello js");
    // 方式三：写入浏览器控制台中
    console.log("hello js");
</script>
</html>
```



#### 三、变量

1、JavaScript中用var关键字来声明变量。

2、JavaScript是弱类型语言，一个变量可以存放不同类型的值。

用var关键字定义变量的特点：

（1）变量的作用域是全局作用域。如下代码，在代码块中和代码块外都可以访问到a变量。

（2）变量可以重复定义，后定义的同名变量会覆盖先定义的同名变量。（我觉得是因为它是脚本语言）

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
<script>
    {
        var a = 20;
        alert(a);
    }
    alert(a);
</script>
</html>
```

**注意：**

（1）ECMAScript6新增了let关键字来定义变量，它的用法和var一样，但是用let关键字定义的变量的作用域是局部作用域，且不允许重复。

（2）ECMAScript6新增了count关键字，用来定义一个只读的常量，一旦用count关键字声明并赋值常量后，常量的值就不能修改值了。用const关键字定义常量时必须声明和初始化同时进行，否则会标红。

#### 四、数据类型与运算符

##### 一、数据类型

JavaScript中的数据类型分为：原始数据类型和引用数据类型。引用数据类型指JavaScript中的对象。

1、**原始数据类型**

number ：整数、小数、NaN（not a number）

string：字符串，用单引号双引号包裹都可以。

boolean：布尔类型

null：对象为空

undefined：当声明的变量未初始化时，该变量的默认值是undefined。

问题：undefined到底是个值还是一个数据类型。string不是引用类型吗（对象类型）？

##### 二、运算符

1、其他的都与java一样，只有一个不一样就是==和===

**2、==与===**

在比较两个量是否相同时，==会先进行类型转换再比较，而===不会进行类型转换，直接比较，类型不一样那肯定不一样。

```java
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
<script>
    var age = 20;
    var _age = "20";
    var $age = 20;
    alert(age == _age);//true
    alert(age === _age);//flase
    alert(age === $age);//true
</script>
</html>
```



##### 三、类型转换

**1、字符串转数字**

使用preseInt()将字符串字面值转为数字，如果字符串字面值一开始就不是一个数字那么就转为NaN类型，如果字符串的字面值一开始有数字，那么就转换这个数字部分，一直到碰到非数字，停止转换。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
<script>
    
    // 类型转换，字符串转数字
    alert(parseInt("12"));//12
    alert(parseInt("12A45"));//12
    alert(parseInt("A12"))//NaN
</script>
</html>
```



**2、其他类型转换为boolean类型**

number转boolean：0和NaN转为false，其他均转为true。

string转boolean：空字符串转为false，其他均转为true。

Null和undefined转boolean：均转为false。

```java
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
<script>
    // var age = 20;
    // var _age = "20";
    // var $age = 20;
    // alert(age == _age);//true
    // alert(age === _age);//flase
    // alert(age === $age);//true

    // 类型转换，字符串转数字
    // alert(parseInt("12"));//12
    // alert(parseInt("12A45"));//12
    // alert(parseInt("A12"))//NaN

    //其他类型转boolean类型
    if (0){
        alert("0转换为false");
    }
    if (NaN){
        alert("NaN转换为false");
    }
    if(-1){
        alert("除了0和NaN外，其他数字都转换为true");
    }

    if(""){
        alert("只有空字符串会转换为false")
    }

    if(null){
        alert("null转换为false");
    }
    if(undefined){
        alert("undefined转换为false")
    }
</script>
</html>
```



### 四、函数

**1、介绍**

- 函数是被设计为执行特定任务的代码块
- 定义：通过function关键字进行定义，语法如下：

```js
function funcationName(参数1，参数2){
	//要执行的代码
}
```



- 注意：

形参不需要类型，因为javaScript是弱类型语言。

返回值也不需要定义类型，可以在函数内部直接使用return返回即可。

- 调用：函数名（实际参数列表）

**2、定义方式二**

```js
var funcationName = funcation(参数1，参数2，...){
    //要执行的代码
}
```



```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
<script>
    //函数定义方式1：
    function add(a , b){
        return a + b;
    }
    //函数定义方式2：
    var add = function(a, b){
        return a + b;
    }
    var result = add(10, 20);
    alert(result);
</script>
</html>
```



### 五、对象

#### 一、基础对象

##### 一、Array对象

**1、定义：**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
<script>
    //定义数组方式1
    var arr = new Array(1, 2, 3);
    //定义数组方式2
    var arr = [1, 2, 3, 4, 5];
    for(var i = 0; i < arr.length; i ++){
        console.log(arr[i]);
    }
</script>
</html>
```



2、**特点**

js中的数组长度可变，且定义一个数组，里面可以放任意类型的值。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
<script>
    
    //js数组特点:长度可变，且定义一个数组，里面可以放任意类型的值。
    var arr = [1, 2, 3, 4, 5];
    arr[10] = 20;
    arr[8] = 'A';
    arr[9] = true;
    console.log(arr);
    
    </script>
</html>
```



3、**数组对象的属性方法**

属性：

length：设置或返回数组中元素的数量。

方法：

forEach()：遍历数组中每个有值的元素，并调用一次传入的参数。

push（）：将新元素添加到数组的末尾，并返回新的长度。

splice()：从数组中删除元素。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
<script>
    
    var arr = [1, 2, 3, 4, 5];
    arr[10] = 20;
    arr[8] = 'A';
    arr[9] = true;
    
    //箭头函数形式
    arr.forEach((e) => {
        console.log(e);
    });
    //普通形式
    arr.forEach(function(e){
        console.log(e);
    })

    arr.push(7, 8, 9);
    console.log(arr);
    //第一个参数指定从哪个位置删，第二个指定删几个。
    arr.splice(2, 2);
    console.log(arr);
    </script>
</html>
```



5、ES6箭头函数

是用来简化函数定义语法的，具体形式为（参数列表）=> {...}，如果需要给箭头函数起名字，var 变量名 = （参数列表）=> {...}

问题：java中的lamad表达式。

##### 二、String字符串

1、创建

2、属性

length：获取字符串的长度。

3、方法

charAt()：返回在指定位置的字符。

indexOf()：检索字符串。

trim()：去除字符串两边的空格。

substring()：提取字符串中两个指定的索引号之间的字符。含头不含尾。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
<script>
    //创建字符串
    var str = "   Hello world   ";
    //charAt()
    console.log(str.charAt(7));
    //indexOf()
    console.log(str.indexOf("lo"));
    //trim()
    var s = str.trim();
    console.log(s);
    console.log(s.substring(0, 5));
</script>
</html>
```



##### 三、javaScript自定义对象

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
<script>
    //js中的自定义对象
    var user = {
        name: "Tom",
        age: 10,
        gender: "male",
        eat: function() {
            alert("请用膳");
        }
    }
    alert(user.name);
    user.eat();
</script>
</html>
```



##### 五、JSON

1、JSON介绍

- 概念：JavaScript Object Notation，javaScript对象标记法。

- JSON格式数据是通过javaScript对象标记法书写的文本。

- 由于其语法简单，层次结构鲜明，现多用于作为数据载体，在网络中进行数据传输。

- json格式的数据本质就是一个字符串
- json格式数据中，键值必须用双引号包裹。
- 前后端传递特别复杂的数据时用json格式数据。
- value的数据类型

​	（1）数字（整数、浮点数）（2）字符串（在双引号中）（3）逻辑值（true或false）（4）数组（在方括号中）（5）对象（在大括号中）（6）null。

JSON字符串转为JS对象

```js
var jsObject = JSON.parse(userStr);
```



JS对象转为JSON字符串

```js
var jsonStr = JSON.stringify(jsObject);
```



```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
<script>
    //js中的自定义对象
    var user = {
        name: "Tom",
        age: 10,
        gender: "male",
        eat: function() {
            alert("请用膳");
        }
    }
    /* alert(user.name);
    user.eat(); */

    var jsonStr = '{"name": "Tom", "age": 18, "add": ["北京", "上海", "西安"]}';
    //json字符串--js对象
    var obj = JSON.parse(jsonStr);
    console.log(obj);
    //js对象--json字符串
    var jsStr = JSON.stringify(user);
    console.log(jsStr);
</script>
</html>
```



**注意**：（1）将js对象转换为json格式数据时，只转对象中的属性，方法转不了。（2）

#### 二、BOM对象

**1、BOM**

Browser Object Model 浏览器对象模型，允许js与浏览器对话，js将浏览器的各个组成部分封装成了对应的对象。

BOM的组成：

- window:浏览器窗口对象。
- Navigator：浏览器对象（里面包括浏览器的名称、版本号、内核之类的）
- Screen：屏幕对象
- History：历史记录对象。
- Location:地址栏对象。

**2、window对象**

（1）获取：直接使用window获取，其中window.可以省略。

（2）属性：

- history：对history对象的只读引用

- location：用于窗口或框架的location对象。（说的好复杂，窗口和框架是啥）

- navigator：对navigator对象的只读引用。

（3）方法：

- alert（）：显示带有一段提示消息和一个确认按钮的警告框。

- confirm（）：显示带有一段提示信息和一个确认按钮、一个取按钮的对话框。该方法有返回值，如果点确认返回true点取消返回false。
- setInterval（）：按照指定的周期（按毫秒计）来调用函数或者计算表达式。
- setTimeout（）：在指定的毫秒数后调用函数或计算表达式。

**3、location对象**

（1）获取：使用window.location获取，其中window可以省略。

（2）属性：href:设置或者返回完整的URL。

#### 三、DOM对象

**1、概念**

Document Object Model文档对象模型。

将标记语言的各个组成部分封装为对应的对象。

- document：整个文档对象
- element：元素对象
- Attribute：属性对象
- Text：文本对象
- Comment：注释对象

**2、js通过dom，能够对html进行的操作**

- 改变html元素的内容
- 改变html的样式
- 对事件做出反映
- 添加和删除html元素

**3、组成**

DOM是W3C的标准，定义了访问HTML和XML文档的标准，共包括三个部分。

（1）Core DOM 所有文档类型的标准模型，无论是哪种标记语言，都包含这五种标准DOM对象

- document：整个文档对象
- element：元素对象
- Attribute：属性对象
- Text：文本对象
- Comment：注释对象

（2）XML DOM XML文档的标准模型

是标准模型的子集。

（3）HTML DOM HTML文档的标模型

将HTML中的所有标签都封装成了一个dom对象。

**4、html中获取element对象**

- 浏览器加载并解析完html页面后，会把html页面的各个组成部分封装成对应的对象，并在浏览器的内存中形成一个dom树。

![image-20241226164741773](img/image-20241226164741773.png)

HTML中的Element对象可以通过Document对象来获取，而Document对象是通过window对象来获取的。

Document对象中提供了以下获取Element元素对象的函数。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <img src="./img/off.gif" id="h1"> <br><br>
    <div class="cls">传智教育</div> <br>
    <div class="cls">黑马程序员</div> <br>
    <input type="checkbox" name="hobby">电影
    <input type="checkbox" name="hobby">旅游
    <input type="checkbox" name="hobby">游戏
</body>
<script>
    //获取element元素对象
    //根据id获取 返回单个element元素
    var img = window.document.getElementById("h1");
    //alert(img);
    //根据标签获取 返回element对象数组
    var divs = window.document.getElementsByTagName("div");
    /* for (let i = 0; i < divs.length; i++) {
        alert(divs[i]);
        
    } */
   //根据name获取 返回element对象数组
    var hobbys = window.document.getElementsByName("hobby");
    /* for (let i = 0; i < hobbys.length; i++) {
        alert(hobbys[i]);
        
    } */
    //根据类名获取 返回element对象数组
    var cls = window.document.getElementsByClassName("cls");
    for (let i = 0; i < cls.length; i++) {
        //alert(cls[i]);
        console.log(cls[i]);
    }
</script>
</html>
```



5、案例

![image-20241226174137377](img/image-20241226174137377.png)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <img src="./img/off.gif" id="h1"> <br><br>
    <div class="cls">传智教育</div> <br>
    <div class="cls">黑马程序员</div> <br>
    <input type="checkbox" name="hobby">电影
    <input type="checkbox" name="hobby">旅游
    <input type="checkbox" name="hobby">游戏
    
</body>
<script>
    //1、点亮灯泡
    var img = document.getElementById("h1");
    img.src = "./img/on.gif";
    
    var divs = document.getElementsByTagName("div");
    for (let i = 0; i < divs.length; i++) {
        const element = divs[i];
        element.innerHTML += "<font color='red'>vary good!</font>";
    }
    
    var ins = document.getElementsByName("hobby");
    for (let i = 0; i < ins.length; i++) {
        const element = ins[i];
        element.checked = true;
    }
</script>
</html>
```



### 六、JS事件监听

- 事件：指发生的事情，HTML事件是指发生在HTML元素上的事情。
- 事件监听：当事件发生时JS可以检测到，并执行指定代码。

#### 一、事件绑定

1、方式一：通过HTML标签中的事件属性进行绑定。

2、方式二：通过DOM元素的事件属性去绑定

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <input type="button" value="事件绑定1" id="but1" onclick="on()">
    <input type="button" value="事件绑定2" id="but2">
</body>
<script>
    function on(){
        alert("按钮1被点击了！");
    }
    document.getElementById("but2").onclick = function () {
        alert("按钮2被点击了！");
    }
</script>
</html>
```



#### 二、常见事件

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body onload="load()">
    <form action="" method="get" style="text-align: center;" onsubmit="subfn()">
        <input type="text" onblur="bfn()" onfocus="ffn()" onkeydown="kfn()">
        <input type="submit" value="提交" id="bl">
        <input type="button" value="单击事件" id="bl" onclick="fn1()">
    </form>
    <br><br><br>

    <table border="1px" cellspacing="0" width="800px" align="center" onmousemove="over()" onmouseout="out()">
        <tr>
            <th>学号</th>
            <th>姓名</th>
            <th>分数</th>
            <th>评语</th>
        </tr>
        <tr>
            <td>001</td>
            <td>张三</td>
            <td>90</td>
            <td>很优秀</td>
        </tr>
        <tr>
            <td>002</td>
            <td>李四</td>
            <td>92</td>
            <td>优秀</td>
        </tr>
    </table>
</body>
<script>
    //onload：页面或者元素加载完成后触发
    function load(){
        console.log("页面加载完成...");
    }
    //onclick：鼠标点击事件
    function fn1(){
        console.log("我被点击了...");
    }
    //onblur：失去焦点事件
    function bfn(){
        console.log("失去焦点...");
    }
    //onfocus：元素获得焦点
    function  ffn(){
        console.log("获得焦点...");
    }
    //onkeydown:某个键盘的键被按下
    function kfn(){
        console.log("键盘被按下了...");
    }
    //onmouseover：鼠标移动到元素之上
    function over() {
        console.log("鼠标移入啦...");
    }
    //onmouseout：鼠标移出某元素
    function out (){
        console.log("鼠标移出...");
    }
    //onsubmit:提交表单事件
    function subfn(){
        alert("表单被提交了...");
    }

</script>
</html>
```



#### 三、案例

![image-20241227102035377](img/image-20241227102035377.png)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <img src="./img/off.gif" id="h1"> <br>
    <input type="button" value="点亮" onclick="on()">
    <input type="button" value="熄灭" onclick="off()">
    <br><br>
    <input type="text" id="name" value="ITCASD" onfocus="lower()" onblur="upper()">
    <br><br>
    <input type="checkbox" name="hobby">电影
    <input type="checkbox" name="hobby">旅游
    <input type="checkbox" name="hobby">游戏
    <br>
    <input type="button" value="全选" onclick="checkAll()">
    <input type="button" value="反选" onclick="checkNull()">
</body>
<script>
    function on(){
        document.getElementById("h1").src = "./img/on.gif";
    }
    function off(){
        document.getElementById("h1").src = "./img/off.gif";
    }
    function lower(){
        var tex = document.getElementById("name");
        tex.value = tex.value.toLowerCase();
    }
    function upper(){
        var tex = document.getElementById("name");
        tex.value = tex.value.toUpperCase();
    }
    function checkAll(){
        const elements = document.getElementsByName("hobby");
        for (let i = 0; i < elements.length; i++) {
            const element = elements[i];
            element.checked = true;
        }
    }
    function checkNull(){
        const elements = document.getElementsByName("hobby");
        for (let i = 0; i < elements.length; i++) {
            const element = elements[i];
            element.checked = false;
        }
    }
</script>
</html>
```



## 四、Vue

### 一、快速入门

**1、什么是vue：**

- Vue是一套前端框架，免除原生js中的dom操作，简化书写。
- 基于MVVM（Model-View-ViewModel）思想，实现数据的双向绑定，将编程的关注点放在数据上。

![image-20241227105451977](img/image-20241227105451977.png)

MVVM思想：model，数据模型，里面包含着数据和对数据的操作。view，视图模型，进行数据的展示，说白了就是html页面，就是dom元素。ViewModel是这当中最核心的，它实现了数据的双向绑定，当数据模型中的数据发生变化时，ViewModel会监测到，然后让view层的数据也发生相应的变化，反之亦然。这个ViewModel不需要我们自己实现，Vue已经帮我们实现好了。

框架：是一个半成品软件，是一套可重用的、通用的基础代码模型。基于框架进行开发，更加快捷更加高效。

**2**、**快速入门代码及步骤**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<!-- 1、新建html页面，引入vue.js文件 -->
<script src="./js/vue.js"></script>
<body>
    <!-- 3、编写视图 -->
    <div id="app">
        <input type="text" v-model="message">
        {{message}}
    </div>
</body>
<script>
    // 2、在js代码区域创建vue核心对象，定义数据模型，及要接管的视图区域。
    new Vue({
        el: "#app",//Vue要接管的视图区域
        //数据模型
        data: {
            message: "Hello World"
        }
    })
</script>
</html>
```



**3、插值表达式：**

形式：{{表达式}}

内容可以是：变量、三元运算符、函数调用、算术运算

### 二、常用指令

指令：html标签上带有v-前缀的特殊属性，不同指令具有不同意义。

#### 1、v-bind和v-model

v-bind:为html标签的属性绑定属性值。

v-model：在表单元素上创建双向数据绑定。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="./js/vue.js"></script>
</head>
<body>
    <div id="app">
        <a v-bind:href="url">链接1</a>
        <!-- v-bind简化形式 -->
        <a :href="url">链接2</a>
        <input type="text" v-model="url">
    </div>
</body>
<script>
    new Vue({
        el:"#app",
        data: {
            url: "https://www.baidu.com"
        }
    })
</script>
</html>
```



#### 2、v-on

v-on：为html标签绑定事件

如果绑定的函数没有参数，()可以省略。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="./js/vue.js"></script>
</head>
<body>
    <div id="app">
        <input type="button" value="点我一下" v-on:click="handel()">
        <!-- 简写形式 -->
        <input type="button" value="点我一下" @click="handel()">
    </div>
</body>
<script>
    new Vue({
        el:"#app",
        data: {

        },
        methods: {
            handel: function(){
                alert("我被点了一下")
            }
        }
    })
</script>
</html>
```



#### 3、v-if、v-show和v-for

v-if、v-else-if、v-else：条件性的渲染某元素，判断为true时渲染，否则不渲染。这三个是组合的，比如if成立了，那就不会再往下执行else-if了。

v-show：根据条件判断是否要展示某些元素，它会渲染所有元素，就是一个展示不展示的问题，它通过display来控制展示还是不展示。如果有多个v-show判断，那都会一个一个执行的，只要符合条件就显示。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="./js/vue.js"></script>
</head>
<body>
    <div id="app">
        年龄<input type="text" v-model="age">经判定为：
        <span v-if="age <= 35">年轻人（35岁及以下）</span>
        <span v-else-if="age > 35 && age < 60">中年人（35岁以上-60岁）</span>
        <span v-else>老年人（60岁及以上）</span>
        <br><br>
        年龄<input type="text" v-model="age">经判定为：
        <span v-show="age <= 35">年轻人（35岁及以下）</span>
        <span v-show="age > 35 && age < 60">中年人（35岁以上-60岁）</span>
        <span v-show="age>60">老年人（60岁及以上）</span>
    </div>
</body>
<script>
    new Vue({
        el: "#app",
        data: {
            age: 20
        }
    })
</script>
</html>
```



v-for：列表渲染，遍历容器的元素或者对象的属性。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="./js/vue.js"></script>
</head>
<body>
    <div id="app">
        <div v-for="addr in addres">
            {{ addr }}
        </div>
        <div v-for="(addr, index) in addres">
            {{index + 1}}:{{ addr }}
        </div>
    </div>
</body>
<script>
    new Vue({
        el: "#app",
        data: {
            addres: ["北京", "上海", "西安", "成都", "深圳"]
        }
    })
</script>
</html>
```



### 三、案例

![image-20241227201122789](img/image-20241227201122789.png)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="./js/vue.js"></script>
</head>
<body>
    <div id="app">
        <table border="1px" width="60%" cellspacing="0">
            <tr>
                <th>编号</th>
                <th>姓名</th>
                <th>年龄</th>
                <th>性别</th>
                <th>成绩</th>
                <th>等级</th>
            </tr>
            <tr v-for="(user, index) in users" align="center">
                <td>{{index + 1}}</td>
                <td>{{user.name}}</td>
                <td>{{user.age}}</td>
                <td>
                    <span v-if="user.gender == 1">男</span>
                    <span v-if="user.gender == 2">女</span>
                </td>
                <td>{{user.score}}</td>
                <td>
                    <span v-if="user.score >= 85">优秀</span>
                    <span v-else-if="user.score >= 60">及格</span>
                    <span v-else style="color: red;">不及格</span>
                </td>
            </tr>
        </table>
    </div>
    
</body>
<script>
    new Vue({
        el:"#app",
        data: {
            
            users: [
                {
                    name: "Tom",
                    age:20,
                    gender: 1,
                    score: 78
                },
                {
                    name: "Rose",
                    age:18,
                    gender: 2,
                    score: 86
                },
                {
                    name: "Jerry",
                    age:26,
                    gender: 1,
                    score: 90
                },
                {
                    name: "Tony",
                    age:30,
                    gender: 1,
                    score: 52
                }
            ]
        }
    })
</script>
</html>
```



### 四、Vue生命周期

Vue的生命周期共分为8个阶段，每发生一个生命周期事件，会自动触发执行一个生命周期方法（钩子函数）

beforeCreate:Vue对象创建之前。

created:Vue对象创建完成后

beforeMount:Vue挂载到指定的dom元素之前。

mounted:Vue挂载到指定的dom挂载完成后。

beforeUpdate:挂载完成后，当数据模型中的数据发生变化，但还没有更新dom当中的展示之前触发。

update:数据模型中的数据发生了变化，并且已经更新了dom当中的展示之后触发updated。

beforeDestroy表示vue对象销毁前。

destroy表示vue对象销毁后。 

### 五、Axios函数库使用

1、介绍：Axios对原生的Ajax进行了封装，简化了书写，提高了开发效率。

2、官网：https://www.axios-http.cn/

1、在前后端交互时千万别忘了解决跨域问题，用一个注解就可以解决。

```html
<body>
    <script src="https://unpkg.com/axios/dist/axios.min.js"></script>
    <script>
    	//发送请求
        axios({
            method:'get',
            url:'http//localhost:8080/article/getAll'
        }).then(result=>{
            //成功的回调
            //result代表服务器响应的所有数据，包括了响应头，响应体。result.data代表的是接口响应的核心数据。
        })
    </script>
</body>
```

我猜我猜!刚开始一两次用这段代码前端请求后端数据失败是因为，这是一个异步请求，所以它可能正好没有等到后端响应回来的数据。

所以应该要同步等待异步请求的结果才健壮。在axios前加上await,加上这个如果没有等到后台返回的结果方法就不会结束。但是要在调用axios的方法外加上async。因为await只能用在异步函数里。

#### 一、Axios入门

1、引入Axios的js文件

```html
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
```



2、使用Axios发送请求并获取响应结果

```js
axios({
    method:"get",
    url:"要请求的地址"
}).then((result)=>{
    console.log(result.data);
});
```



method表示请求的方式，url是要请求的后端地址。,then()是成功后要调用的函数，它的箭头函数参数是成功回调函数，当请求成功时，then()函数执行，并自动执行其中的成功回调函数，自动获取回调函数的参数result。

```js
axios({
    method:"post",
    url:"要请求的地址",
    data:"id=1"
}).then((result)=>{
    console.log(result.data);
});
```



在post请求中，data属性值是要在请求体中传递的请求参数。

**注意**：在浏览器中直接访问（在浏览器地址栏输入地址，然后回车）的任何地址，都是以get请求的方式访问的。

#### 二、请求方式别名

**注意**：推荐以这种方式发送请求

```js
axios.get("要请求的地址").then((result)=>{
    console.log(result.data);
});
```



```js
axios.post("要请求的地址", "id=1").then((result)=>{
    console.log(result.data);
});
```

**什么是箭头函数？**

解构是什么意思{...一个数据名}

问题：promise函数

### 六、Vue的各种相关工具及脚手架

![image-20241228145942977](img/image-20241228145942977.png)

webpack 是一个全能选手，啥都能干，只是有点复杂，对新手不太友好。
Rollup 是后起之秀，打包更简洁。
vite 把 rollup 变成了“开袋即食”，便于新手入门。
create-vue 基本取代了 vue-cli，除非你想创建 vue2 的项目。

所以，想创建一个 vue3 的项目，首选 create-vue，非常方便快捷，建立的项目也可以统一风格。

### 七、Vue项目的目录结构

基于Vue的脚手架工具所创造出来的vue项目有固定的目录结构。其中：

node_modules目录中存放整个项目所依赖的包，比如所依赖的各种js文件和css文件。

public目录中存放项目的静态文件。

package.json文件中存放模块的基本信息，项目开发所需要模块，版本信息。

vue.config.js文件中存放了vue的配置信息，例如，端口号、代理的配置等。

src目录下存放项目的源代码。

#### 一、Vue项目配置端口

在vue.config.js文件中添加一个属性

```js
devServer: {
    port: 端口号
}
```



### 八、vue项目的运行流程

在vue的默认首页中通过script标签引入main.js文件，项目启动后访问项目时浏览器就会渲染这个vue的默认首页index.html，从而也会自动执行main.js。

```html
<!DOCTYPE html>
<html lang="">
  <head>
    <meta charset="UTF-8">
    <link rel="icon" href="/favicon.ico">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vite App</title>
  </head>
  <body>
    <div id="app"></div>
    <script type="module" src="/src/main.js"></script>
  </body>
</html>
```



在main.js中将项目的根组件App.vue引入。并给引入的它起名App。同时引入node_modules目录中的依赖包vue中的createApp函数。然后调用createApp函数，将引入的根组件作为参数传进去，创建出一个vue实例（vue的核心对象）。然后通过其中的mount函数将该vue实例挂载到vue默认首页index.html的div元素上。所以最终我们的App.vue里有什么内容，我们默认首页index.html的div中就有什么内容。

```js
import './assets/main.css'

import { createApp } from 'vue'
import App from './App.vue'

createApp(App).mount('#app')
```



这里用到了默认导出，所以在main.js的导入方式中，App这个名字可以自己起。data在这里是函数，可以简写，把：function去掉。

```vue
<script>
  export default{
    data: function(){
      return{
        message: "上海"
      }
    }
  }
</script>

<template>
  <h1>{{ message }}</h1>
</template>

<style>
  h1 {
    color: red;
  }
</style>
```



### 九、Vue的API风格

vue的组件有两种不同的风格：组合式API和选项式API。

#### 一、选项式API

选项式api，可以用包含多个选项的对象来描述组件的逻辑，如：data、methods、mounted等。

```vue
<script>
  export default{
    data: function(){
      return{
        message: "上海",
        count: 0
      }
    },
    methods: {//里面声明方法
      increment: function(){
        this.count ++
      }
    },
    mounted(){
      alert("页面挂载完成")
    }
  }
</script>

<template>
  <h1>{{ message }}</h1>
  <br>
  <h6>选项式api</h6>
  <button v-on:click="increment()">{{ count }}</button>
</template>

<style>
  h1 {
    color: red;
  }
</style>

```



#### 二、组合式API

setup:是一个标识，告诉Vue进行一些处理，让我们可以更简介的使用组合式api。

ref():ref函数，参数接收一个值，我们称之为响应式值。返回一个响应式的ref对象，此对象只有一个指向响应式值的属性value。

什么时候使用.value:(1)在 JavaScript/TypeScript 代码中直接访问或修改 `ref` 创建的响应式变量的值。（2）在 `watch` 或 `watchEffect` 中观察 `ref` 创建的响应式变量。

什么时候不需要使用.value:（1）在vue模板中，当你在 Vue 的模板中引用 `ref` 创建的响应式变量时，Vue 会自动为你解包（unwrap）这个值，所以你不需要使用 `.value`。

```vue
<template>
  <p>{{ count }}</p> <!-- Vue 会自动解包 ref 的值，不需要 .value -->
</template>
```



（2）在setup函数的返回值中，当你在 `setup` 函数中返回一个响应式变量给模板时，你不需要使用 `.value`。Vue 会自动处理这些响应式变量，使它们在模板中可用。

```vue
import { ref } from 'vue';

export default {
  setup() {
    const count = ref(0);
    return {
      count // 不需要写 count.value
    };
  }
}
```



（3）使用定义好的pinia里的状态对象里的响应式变量时，都不需要.value。

### 十、路由

#### 一、路由

路由，决定从起点到终点的路径的进程。

在前端工程中，路由指的是根据不同的访问路径，展示不同组件的内容。

Vue Router是Vue官方提供的路由。

#### 二、VueRouter的使用步骤

1、安装VueRouter npm install vue-router@4

2、在src/router/index.js中创建路由器

在创建路由器时，需要从下载好的vue-router中引入两个模块：createRouter和createWebHistory

在应用路由的时候，我们的关键任务就是指明访问路径与组件的对应关系。

```js
import {createRouter, createWebHistory} from 'vue-router';
//导入组件
import LoginVue from '@/views/Login.vue';
impory LayoutVue from '@/views/Layout.vue';
import Articalcategory from '@/views/artical/ArticalCategory.vue'
//创建一个数组，定义路由关系
//path为要访问的路径，component指定要访问的组件
const routes = [
    {path:'/login', component:LoginVue},
    {path:'/', 
     component:LayoutVue,
     //配置子路由
     children:[
         {path:'/artical/category', component:Articalcategory}
     ],
     redirect:'/artical/category' //重定向，意思是访问'/'时默认重定向到'/artical/category'
    }
];
//创建路由器
const router = createRouter({
    history:createWebHistory(),
    routes:routes
});
export default router;
```



3、在vue的应用实例中使用刚刚自己创建好的router

```js
import router from '@/router'
app.use(router);
```



4、在App.vue的templet中写上 `<router-view>` 标签，展示组件内容。

#### 三、路由器如何切换组件

```js
import {userRouter} from 'vue-router'
const router = userRouter();
router.push('/');
```



用push()是可以返回的，就是可以点浏览器的那个前进后退键。它有路由记录功能。

问题：Vue懒加载、回调函数、模块化开发

## 五、Vue2

prototype是vue的原型，在里面定义一些全局的变量，所有的vue都可以用。

template标签里面只能有一个标签。

### 一、Vuex

#### 一、基础知识

#### 1、Vuex是什么

Vuex是一个专门为Vue.js应用程序开发的状态管理工具，它采用集中式存储管理应用的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化。Vuex也集成到了vue官方的调试工具devtools extension，提供了诸如零配置的time-travel调试、状态快照导入导出等高级调试功能。

可以把Vuex理解成一个全局状态管理库。

#### 2、Vuex中的store包括哪几个部分

我们学习Vuex其实主要是学它的store对象，这个对象用来存放全局状态变量的一个仓库。

**state**:定义状态变量，我们在vuex中的所有全局状态变量都放在这里。

**mutations：**定义改变state中状态变量的方法。

**actions：**定义提交mutation的方法，可以包含异步操作。

**modules：**引入其他store模块（对象），模块包含以上4个部分。 

#### 3、改变state的三种方法

1、Vue组件用this.$store.dispatch()提交到actions,然后actions再commit到mutations中，最后mutations改变state中的状态变量。这种方式允许异步操作。

2、Vue组件用this.$store.mutations提交到mutations，然后mutations改变state中的状态变量。这个只允许同步操作。

3、Vue组件直接使用this.$store.state.xxx改变state中的状态变量。（不推荐使用这种方式，因为这种方式改变的state是不可以被devtools监控的）

#### 5、体验state、actions、mutations三部分

这里先体验用第2种方法改变state中的状态变量。

src/store/index.js

```js
import Vue from 'vue'
import Vuex from 'vuex'

Vue.use(Vuex)

export default new Vuex.Store({
  state: {
    Fan: {id: 1, name: '凡三岁', rank: 'p6', online: true},
    Jack: {id: 2, name: 'Jack Ma', rank: 'p10', online: true},
    Tony: {id: 2, name: 'Tony Ma', rank: 'p10', online: true},
    userCount: 3
  },
  getters: {
  },
  mutations: {
    SET_RANK: (state, payload) => state.Fan.rank = payload,
    SET_ONLINE: (state, payload) => state.Fan.online = false
  },
  actions: {
    
  },
  modules: {
  }
})
```



Login.vue

```vue
<template>
    <div class="login" :style="'background-image:url('+ Background +');'">
    <el-form ref="loginForm" :model="loginForm" :rules="loginRules" label-position="left" label-width="0px" class="login-form">
      <h3 class="title">
        ELADMIN 后台管理系统
      </h3>
      <el-form-item prop="username">
        <el-input v-model="loginForm.username" type="text" auto-complete="off" placeholder="账号">
          <!-- <svg-icon slot="prefix" icon-class="user" class="el-input__icon input-icon" /> -->
        </el-input>
      </el-form-item>
      <el-form-item prop="password">
        <el-input v-model="loginForm.password" type="password" auto-complete="off" placeholder="密码" @keyup.enter.native="handleLogin">
          <!-- <svg-icon slot="prefix" icon-class="password" class="el-input__icon input-icon" /> -->
        </el-input>
      </el-form-item>
      <el-form-item prop="code">
        <el-input v-model="loginForm.code" auto-complete="off" placeholder="验证码" style="width: 63%" @keyup.enter.native="handleLogin">
          <!-- <svg-icon slot="prefix" icon-class="validCode" class="el-input__icon input-icon" /> -->
        </el-input>
        <div class="login-code">
          <img :src="codeUrl" @click="getCode">
        </div>
      </el-form-item>
      <el-checkbox v-model="loginForm.rememberMe" style="margin:0 0 25px 0;">
        记住我
      </el-checkbox>
      <el-form-item style="width:100%;">
        <el-button :loading="loading" size="medium" type="primary" style="width:100%;" @click.native.prevent="handleLogin">
          <span v-if="!loading">登 录</span>
          <span v-else>登 录 中...</span>
        </el-button>
        <el-button @click="setRank()">改变rank</el-button>
      </el-form-item>
    </el-form>
    <!--  底部  -->
    <!-- <div v-if="$store.state.settings.showFooter" id="el-login-footer">
      <span v-html="$store.state.settings.footerTxt" />
      <span v-if="$store.state.settings.caseNumber"> ⋅ </span>
      <a href="https://beian.miit.gov.cn/#/Integrated/index" target="_blank">{{ $store.state.settings.caseNumber }}</a>
    </div> -->
  </div>
</template>

<script>
import Background from '@/assets/images/background.jpeg';
import { encrypt } from '@/utils/rsaEncrypt'
    export default{
        name:"Login",
        created(){
          this.getCode()
        },
        data(){
            return {
                loginForm:{
                  username: 'admin',
                  password: '123456',
                  code: '',
                  rememberMe: false,
                  uuid: ''
                },
                loginRules:{
                  username:[{required:true, trigger:'blur', message:'用户名不能为空'}],
                  password:[{required:true, trigger:'blur', message:'密码名不能为空'}],
                  code:[{required:true, trigger:'blur', message:'验证码不能为空'}]
                },
                Background: Background,
                codeUrl:'',
                loading : false
            }
        },
        methods: {
            getCode(){
              //发送请求到后端，需要用到axios
              this.$request.get('http://localhost:8000/auth/code').then(res=>{
                this.codeUrl = res.data.img
                this.loginForm.uuid = res.data.uuid
              })
            },
            handleLogin(){
              this.$refs.loginForm.validate(vaild=>{
                if(vaild){
                  this.loginForm.password = encrypt(this.loginForm.password);//对密码进行加密
                  console.log(this.loginForm.password);
                  this.$request.post('http://localhost:8000/auth/login', this.loginForm).then(res=>{
                    this.$router.push('/dashboard')
                  })
                }else{
                  alert('请按要求完善登录信息');
                }
              })
              
            },
            setRank() {
              this.$store.commit('SET_RANK', 'p8');
            }
        }
    }
</script>

<style rel="stylesheet/scss" lang="scss">
  .login {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
    background-size: cover;
  }
  .title {
    margin: 0 auto 30px auto;
    text-align: center;
    color: #707070;
  }

  .login-form {
    border-radius: 6px;
    background: #ffffff;
    width: 385px;
    padding: 25px 25px 5px 25px;
    .el-input {
      height: 38px;
      input {
        height: 38px;
      }
    }
    .input-icon{
      height: 39px;width: 14px;margin-left: 2px;
    }
  }
  .login-tip {
    font-size: 13px;
    text-align: center;
    color: #bfbfbf;
  }
  .login-code {
    width: 33%;
    display: inline-block;
    height: 38px;
    float: right;
    img{
      cursor: pointer;
      vertical-align:middle
    }
  }
</style>
```



体验第一种方式

src/store/index.js

```js
import Vue from 'vue'
import Vuex from 'vuex'

Vue.use(Vuex)

export default new Vuex.Store({
  state: {
    Fan: {id: 1, name: '凡三岁', rank: 'p6', online: true},
    Jack: {id: 2, name: 'Jack Ma', rank: 'p10', online: true},
    Tony: {id: 2, name: 'Tony Ma', rank: 'p10', online: true},
    userCount: 3
  },
  getters: {
  },
  mutations: {
    SET_RANK: (state, payload) => state.Fan.rank = payload,
    SET_ONLINE: (state, payload) => state.Fan.online = false
  },
  actions: {
    setRank: (injectee, payload) => injectee.commit('SET_RANK', payload)
  },
  modules: {
  }
})
```



Login.vue

```vue
<template>
    <div class="login" :style="'background-image:url('+ Background +');'">
    <el-form ref="loginForm" :model="loginForm" :rules="loginRules" label-position="left" label-width="0px" class="login-form">
      <h3 class="title">
        ELADMIN 后台管理系统
      </h3>
      <el-form-item prop="username">
        <el-input v-model="loginForm.username" type="text" auto-complete="off" placeholder="账号">
          <!-- <svg-icon slot="prefix" icon-class="user" class="el-input__icon input-icon" /> -->
        </el-input>
      </el-form-item>
      <el-form-item prop="password">
        <el-input v-model="loginForm.password" type="password" auto-complete="off" placeholder="密码" @keyup.enter.native="handleLogin">
          <!-- <svg-icon slot="prefix" icon-class="password" class="el-input__icon input-icon" /> -->
        </el-input>
      </el-form-item>
      <el-form-item prop="code">
        <el-input v-model="loginForm.code" auto-complete="off" placeholder="验证码" style="width: 63%" @keyup.enter.native="handleLogin">
          <!-- <svg-icon slot="prefix" icon-class="validCode" class="el-input__icon input-icon" /> -->
        </el-input>
        <div class="login-code">
          <img :src="codeUrl" @click="getCode">
        </div>
      </el-form-item>
      <el-checkbox v-model="loginForm.rememberMe" style="margin:0 0 25px 0;">
        记住我
      </el-checkbox>
      <el-form-item style="width:100%;">
        <el-button :loading="loading" size="medium" type="primary" style="width:100%;" @click.native.prevent="handleLogin">
          <span v-if="!loading">登 录</span>
          <span v-else>登 录 中...</span>
        </el-button>
        <el-button @click="setRank()">改变rank</el-button>
      </el-form-item>
    </el-form>
    <!--  底部  -->
    <!-- <div v-if="$store.state.settings.showFooter" id="el-login-footer">
      <span v-html="$store.state.settings.footerTxt" />
      <span v-if="$store.state.settings.caseNumber"> ⋅ </span>
      <a href="https://beian.miit.gov.cn/#/Integrated/index" target="_blank">{{ $store.state.settings.caseNumber }}</a>
    </div> -->
  </div>
</template>

<script>
import Background from '@/assets/images/background.jpeg';
import { encrypt } from '@/utils/rsaEncrypt'
    export default{
        name:"Login",
        created(){
          this.getCode()
        },
        data(){
            return {
                loginForm:{
                  username: 'admin',
                  password: '123456',
                  code: '',
                  rememberMe: false,
                  uuid: ''
                },
                loginRules:{
                  username:[{required:true, trigger:'blur', message:'用户名不能为空'}],
                  password:[{required:true, trigger:'blur', message:'密码名不能为空'}],
                  code:[{required:true, trigger:'blur', message:'验证码不能为空'}]
                },
                Background: Background,
                codeUrl:'',
                loading : false
            }
        },
        methods: {
            getCode(){
              //发送请求到后端，需要用到axios
              this.$request.get('http://localhost:8000/auth/code').then(res=>{
                this.codeUrl = res.data.img
                this.loginForm.uuid = res.data.uuid
              })
            },
            handleLogin(){
              this.$refs.loginForm.validate(vaild=>{
                if(vaild){
                  this.loginForm.password = encrypt(this.loginForm.password);//对密码进行加密
                  console.log(this.loginForm.password);
                  this.$request.post('http://localhost:8000/auth/login', this.loginForm).then(res=>{
                    this.$router.push('/dashboard')
                  })
                }else{
                  alert('请按要求完善登录信息');
                }
              })
              
            },
            setRank() {
              this.$store.dispatch('setRank', 'p9');
            }
        }
    }
</script>

<style rel="stylesheet/scss" lang="scss">
  .login {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
    background-size: cover;
  }
  .title {
    margin: 0 auto 30px auto;
    text-align: center;
    color: #707070;
  }

  .login-form {
    border-radius: 6px;
    background: #ffffff;
    width: 385px;
    padding: 25px 25px 5px 25px;
    .el-input {
      height: 38px;
      input {
        height: 38px;
      }
    }
    .input-icon{
      height: 39px;width: 14px;margin-left: 2px;
    }
  }
  .login-tip {
    font-size: 13px;
    text-align: center;
    color: #bfbfbf;
  }
  .login-code {
    width: 33%;
    display: inline-block;
    height: 38px;
    float: right;
    img{
      cursor: pointer;
      vertical-align:middle
    }
  }
</style>
```



#### 6、gettets

src/store/index.js

```js
import Vue from 'vue'
import Vuex from 'vuex'

Vue.use(Vuex)

export default new Vuex.Store({
  state: {
    Fan: {id: 1, name: '凡三岁', rank: 'p6', online: true},
    Jack: {id: 2, name: 'Jack Ma', rank: 'p10', online: true},
    Tony: {id: 2, name: 'Tony Ma', rank: 'p10', online: true},
    userCount: 3
  },
  getters: {
    simpelHandle: (state) => {
      let rankP = Number(state.Fan.rank.replace('p', ''));
      let salary = Math.pow(2, rankP - 5) * 20;
      return salary + 'w';
    }
  },
  mutations: {
    SET_RANK: (state, payload) => state.Fan.rank = payload,
    SET_ONLINE: (state, payload) => state.Fan.online = false
  },
  actions: {
    setRank: (injectee, payload) => injectee.commit('SET_RANK', payload)
  },
  modules: {
  }
})
```



```vue
<template>
    <div class="login" :style="'background-image:url('+ Background +');'">
        <el-button @click="setRank()">改变rank</el-button>
  </div>
</template>

<script>
import Background from '@/assets/images/background.jpeg';
import { encrypt } from '@/utils/rsaEncrypt'
    export default{
        name:"Login",
        created(){
          this.getCode()
        },
        data(){
            return {
                
            }
        },
        methods: {
            setRank() {
              this.$store.dispatch('setRank', 'p8');
              console.log(this.$store.getters.simpelHandle);
            }
        }
    }
</script>
```



点击按钮触发事件，控制台上打印出了计算属性，并且修改了rank的值后，计算属性计算出的值也会跟着相应的改变。

#### 7、moduls

moduls其实就是存放多个子store的对象，我们先新建一个ModulsA.js的文件，然后在里面定义state、actions、mutations、getters

```js
const module = {
    state: {
        Fan_A: {id: 1, name: '凡三岁', rank: 'p6', online: true},
        Jack_A: {id: 2, name: 'Jack Ma', rank: 'p10', online: true},
        Tony_A: {id: 2, name: 'Tony Ma', rank: 'p10', online: true},
        userCount_A: 3
      },
      getters: {
        simpelHandle_A: (state) => {
          let rankP = Number(state.Fan_A.rank.replace('p', ''));
          let salary = Math.pow(2, rankP - 5) * 20;
          return salary + 'w';
        }
      },
      mutations: {
        SET_RANK_A: (state, payload) => state.Fan_A.rank = payload,
        SET_ONLINE_A: (state, payload) => state.Fan_A.online = false
      },
      actions: {
        setRank_A: (injectee, payload) => injectee.commit('SET_RANK_A', payload)
      }
}

export default module;
```



然后把ModulesA.js导入到index.js中的modules中即可，这样其中的state、actions、mutations、getters在组件眼里和父store是一样的。

```js
import Vue from 'vue'
import Vuex from 'vuex'
import module from '@/store/ModulesA.js'
Vue.use(Vuex)

export default new Vuex.Store({
  state: {
    Fan: {id: 1, name: '凡三岁', rank: 'p6', online: true},
    Jack: {id: 2, name: 'Jack Ma', rank: 'p10', online: true},
    Tony: {id: 2, name: 'Tony Ma', rank: 'p10', online: true},
    userCount: 3
  },
  getters: {
    simpelHandle: (state) => {
      let rankP = Number(state.Fan.rank.replace('p', ''));
      let salary = Math.pow(2, rankP - 5) * 20;
      return salary + 'w';
    }
  },
  mutations: {
    SET_RANK: (state, payload) => state.Fan.rank = payload,
    SET_ONLINE: (state, payload) => state.Fan.online = false
  },
  actions: {
    setRank: (injectee, payload) => injectee.commit('SET_RANK', payload)
  },
  modules: {
    module
  }
})
```



Login.vue

```vue
<template>
    <div class="login" :style="'background-image:url('+ Background +');'">
        <el-button @click="setRank()">改变rank</el-button>
  </div>
</template>

<script>
import Background from '@/assets/images/background.jpeg';
import { encrypt } from '@/utils/rsaEncrypt'
    export default{
        name:"Login",
        created(){
          this.getCode()
        },
        data(){
            return {
                
            }
        },
        methods: {
            
            setRank() {
              this.$store.dispatch('setRank_A', 'p8');
              console.log(this.$store.getters.simpelHandle_A);
            }
        }
    }
</script>


```



问题：（1）@click.native.prevent是起个什么作用。（2）为什么添加了响应拦截器

## JavaScript导入导出

JS提供的导入导出机制可以实现按需导入。export关键字，将对象或函数导出为模块。

```js
//showMessage.js
//简单的展示信息
export function simplemessage(msg){
    console.log(msg)
}

//复杂的展示信息
export function   complexMessage(msg){
    console.log(new Date() + ": " + msg)
}
```



message.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JS导入导出</title>
</head>
<body>
    <div>
        <button id="btn">点我展示信息</button>
    </div>
    <script type="module">
        import {complexMessage} from './showMassage.js'
        document.getElementById("btn").onclick = function(){
            complexMessage('我被点击了...');
        }
    </script>
</body>
</html>
```



批量导出：

```js
//showMessage.js
//简单的展示信息
function simplemessage(msg){
    console.log(msg)
}

//复杂的展示信息
function   complexMessage(msg){
    console.log(new Date() + ": " + msg)
}
//批量导出
export {simplemessage, complexMessage}
```



message.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JS导入导出</title>
</head>
<body>
    <div>
        <button id="btn">点我展示信息</button>
    </div>
    <script type="module">
        import {complexMessage} from './showMassage.js'
        document.getElementById("btn").onclick = function(){
            complexMessage('我被点击了...');
        }
    </script>
</body>
</html>
```



导入时起别名：

```js
//showMessage.js
//简单的展示信息
function simplemessage(msg){
    console.log(msg)
}

//复杂的展示信息
function   complexMessage(msg){
    console.log(new Date() + ": " + msg)
}
//批量导出
export {simplemessage, complexMessage}
```



message.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JS导入导出</title>
</head>
<body>
    <div>
        <button id="btn">点我展示信息</button>
    </div>
    <script type="module">
        import {complexMessage as cm} from './showMassage.js'
        document.getElementById("btn").onclick = function(){
            cm('起别名我被点击了...');
        }
    </script>
</body>
</html>
```



导出时起别名：

```js
//showMessage.js
//简单的展示信息
function simplemessage(msg){
    console.log(msg)
}

//复杂的展示信息
function   complexMessage(msg){
    console.log(new Date() + ": " + msg)
}
//批量导出
export {simplemessage as sm, complexMessage as cm}
```



message.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JS导入导出</title>
</head>
<body>
    <div>
        <button id="btn">点我展示信息</button>
    </div>
    <script type="module">
        import {cm} from './showMassage.js'
        document.getElementById("btn").onclick = function(){
            cm('导出时起别名我被点击了...');
        }
    </script>
</body>
</html>
```



默认导出：

```js
//showMessage.js
//简单的展示信息
function simplemessage(msg){
    console.log(msg)
}

//复杂的展示信息
function   complexMessage(msg){
    console.log(new Date() + ": " + msg)
}
//批量导出
//export {simplemessage as sm, complexMessage as cm}
//默认导出
export default {simplemessage, complexMessage} 
```



message.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JS导入导出</title>
</head>
<body>
    <div>
        <button id="btn">点我展示信息</button>
    </div>
    <script type="module">
        import messageMethods from './showMassage.js'
        document.getElementById("btn").onclick = function(){
            messageMethods.simplemessage('aaa');
            messageMethods.complexMessage('bbb');
        }
    </script>
</body>
</html>
```



默认导出时不能起别名，导入时把花括号去掉，随便起个名字，比如上面的messageMethods代表showMassage.js中所有默认导出的内容。

## 五、NodeJs

NodeJs是前端工程化的运行环境。


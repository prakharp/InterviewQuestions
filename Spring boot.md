# Spring-Boot-Interview-Questions

### 1. What is Spring Boot?
First of all Spring Boot is not a framework, it is a way to ease to create stand-alone application with minimal or zero configurations. It is approach to develop spring based application with very less configuration. It provides defaults for code and annotation configuration to quick start new spring projects within no time. It leverages existing spring projects as well as Third party projects to develop production ready applications. It provides a set of Starter Pom’s or gradle build files which one can use to add required dependencies and also facilitate auto configuration.
Spring Boot automatically configures required classes depending on the libraries on its classpath. Suppose your application want to interact with DB, if there are Spring Data libraries on class path then it automatically sets up connection to DB along with the Data Source class.

### 2. What are the advantages of using Spring Boot?
- It is very easy to develop Spring Based applications with Java or Groovy.
- It reduces lots of development time and increases productivity.
- It avoids writing lots of boilerplate Code, Annotations and XML Configuration.
- It is very easy to integrate Spring Boot Application with its Spring Ecosystem like Spring JDBC, Spring ORM, Spring Data, Spring Security etc.
- It follows “Opinionated Defaults Configuration” Approach to reduce Developer effort
- It provides Embedded HTTP servers like Tomcat, Jetty etc. to develop and test our web applications very easily.
- It provides CLI (Command Line Interface) tool to develop and test Spring Boot (Java or Groovy) Applications from command prompt very easily and quickly.
- It provides lots of plugins to develop and test Spring Boot Applications very easily using Build Tools like Maven and Gradle
- It provides lots of plugins to work with embedded and in-memory Databases very easily.

### 3. What are the disadvantages of using Spring Boot?
It is very tough and time consuming process to convert existing or legacy Spring Framework projects into Spring Boot Applications. It is applicable only for brand new/Greenfield Spring Projects.

### 4. Why is it “opinionated”?
It follows “Opinionated Defaults Configuration” Approach to reduce Developer effort. Due to opinionated view of spring boot, what is required to get started but also we can get out if not suitable for application.
-   Spring Boot uses sensible defaults, “opinions”, mostly based on the classpath contents.
-   For example
-  Sets up a JPA Entity Manager Factory if a JPA implementation is on the classpath.
- Creates a default Spring MVC setup, if Spring MVC is on the classpath.
-  Everything can be overridden easily
-  But most of the time not needed

### 5. How does it work? How does it know what to configure?
-  Auto-configuration works by analyzing the classpath
-  If you forget a dependency, Spring Boot can’t configure it
-  A dependency management tool is recommended
-  Spring Boot parent and starters make it much easier
-  Spring Boot works with Maven, Gradle, Ant/Ivy
-  Our content here will show Maven

### 6. How are properties defined? Where?
In spring boot, we have to define properties in the application.properties file exists in classpath of application as follow.

Example: configure default DataSource bean
database.host=localhost
database.user=admin

### 7. What is the difference between an embedded container and a WAR?
There is no force to go container less
-  Embedded container is just one feature of Spring Boot
-  Traditional WAR also benefits a lot from Spring Boot
-  Automatic Spring MVC setup, including DispatcherServlet
-  Sensible defaults based on the classpath content
-  Embedded container can be used during development

### 8. What embedded containers does Spring Boot support?
Spring Boot includes support for embedded Tomcat, Jetty, and Undertow servers.
By default the embedded server will listen for HTTP requests on port 8080.

### 9. What does @EnableAutoConfiguration do? What about @SpringBootApplication?
@EnableAutoConfiguration annotation on a Spring Java configuration class
– Causes Spring Boot to automatically create beans it thinks you need
– Usually based on classpath contents, can easily override
                    
                    @Configuration
                    @EnableAutoConfiguration
                    public class MyAppConfig {
                          public static void main(String[] args) {
                          SpringApplication.run(MyAppConfig.class, args);
                       }
                    }
                    
@SpringBootApplication was available from Spring Boot 1.2
It is very common to use @EnableAutoConfiguration, @Configuration, and @ComponentScan together.
      
      @Configuration
      @ComponentScan
      @EnableAutoConfiguration
      public class MyAppConfig {
              ...
      }
      
      With @SpringBootApplication annotation
      @SpringBootApplication
      public class MyAppConfig {
              ...
      }

### 10. What is a Spring Boot starter POM? Why is it useful?
Starters are a set of convenient dependency descriptors that you can include in your application. The starters contain a lot of the dependencies that you need to get a project up and running quickly and with a consistent, supported set of managed transitive dependencies.

The starter POMs are convenient dependency descriptors that can be added to your application’s Maven. In simple words, if you are developing a project that uses Spring Batch for batch processing, you just have to include spring-boot-starter-batch that will import all the required dependencies for the Spring Batch application. This reduces the burden of searching and configuring all the dependencies required for a framework.

### 11. How to reload my changes on Spring Boot without having to restart server?
Include following maven dependency in the application.

    <dependency>
       <groupId>org.springframework</groupId>
       <artifactId>springloaded</artifactId>
       <version>1.2.6.RELEASE</version>
    </dependency>

Automatic restart
Applications that use spring-boot-devtools will automatically restart whenever files on the classpath change. This can be a useful feature when working in an IDE as it gives a very fast feedback loop for code changes. By default, any entry on the classpath that points to a folder will be monitored for changes.
    
    <dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-devtools</artifactId>
      <optional>true</optional>
    </dependency>

This can be achieved using DEV Tools. With this dependency any changes you save, the embedded tomcat will restart. Spring Boot has a Developer tools (DevTools) module which helps to improve the productivity of developers. One of the key challenge for the Java developers is to auto deploy the file changes to server and auto restart the server. Developers can reload changes on Spring Boot without having to restart my server. This will eliminates the need for manually deploying the changes every time. Spring Boot doesn’t have this feature when it has released it’s first version. This was a most requested features for the developers. The module DevTools does exactly what is needed for the developers. This module will be disabled in the production environment.

### 12. How to run Spring boot application to custom port ?
In application.properties, add following property.
    
    server.port = 8181

### 13. What is the configuration file name used by Spring Boot?
The configuration file used in spring boot projects is application.properties. This file is very important where we would over write all the default configurations. Normally we have to keep this file under the resources folder of the project.

### 14. How to implement Spring web using Spring boot?
Web Application Convenience 
-   Boot automatically configures
-   A DispatcherServlet & ContextLoaderListener
-   Spring MVC using same defaults as @EnableWebMvc
-   Plus many useful extra features:
-   Static resources served from classpath
-   /static, /public, /resources or /META-INF/resources
-   Templates served from /templates
-   If Velocity, Freemarker, Thymeleaf, or Groovy on classpath
-   Provides default /error mapping
-   Easily overridden
-   Default MessageSource for I18N

### 15.What is actuator in spring boot?
An actuator is one of the best parts of spring boot which consists of production-ready features to help you monitor and manage your application. 

With the help of an actuator, you can monitor what is happening inside the running application.
Actuator dependency figures out the metrics and makes them available as a new endpoint in your application and retrieves all required information from the web. You can identify beans, the health status of your application, CPU usage, and many more with the actuator.

### 16.What is JPA in spring boot?
JPA is basically Java Persistence API. It’s a specification that lets you do ORM when you are connecting to a relational database which is Object-Relational Mapping. 

So, when you need to connect from your java application to relational database, you need to be able to use something like JDBC and run SQL queries and then you get the results and convert them into Object instances. 

ORM lets you map your entity classes in your SQL tables so that when you connect to the database , you don’t need to do query yourself, it’s the framework that handles it for you.

And JPA is a way to use ORM, it’s an API which lets you configure your entity classes and give it to a framework so that the framework does the rest.

### 15. Spring Boot supports both Java properties and YML files. Would you recognize and understand them if you saw them?

    spring boot application java property file name is application.properties
    spring boot application YML file name is application.yml

## 16. @Controller vs RestController 
The @Controller is a common annotation which is used to mark a class as Spring MVC Controller while the @RestController is a special controller used in RESTFul web services and the equivalent of @Controller + @ResponseBody .29-Aug-2017

## Spring Framework Annotations

|Sl.No| Annotation    | Description  |
|-----|---------------|--------------|
| 01. |@Autowired	  |Annotation @Autowired is used to inject object dependency implicitly for a **constructor, field or method**. This is known as “autowired by type” since the object to be injected is discovered by its type. The items declared @Autowired need not have to be public.|				
| 02. |@Configurable  |	Used on classes to inject properties of domain objects. Types whose properties are injected without being instantiated by Spring can be declared with @Configurable annotation.	|
| 03. |@Qualifier	  |It can be used to create more than one bean of the same type and wire only one of the types with a property. It provides greater control on the dependency injection process and can be used with @Autowired annotation.|
| 04. |@Required	  |Used to mark class members that are mandatory. The Spring auto-configuration fails if a particular property specified with this annotation cannot be injected.|
| 05.  |@ComponentScan|Make Spring scan the package for the @Configuration clases.|
| 06.  |@Configuration|It is used on classes that define beans.|
| 07.  |@Bean	      |It indicates that a method produces a bean which will be mananged by the Spring container.|			
| 08.  |@Lazy	      |Makes a @Bean or @Component to be initialized only if it is requested.|		
| 09.  |@Value	      |It is used to inject values into a bean’s attribute from a property file. @Value annotation indicates a default value expression for the field or parameter.|	
| 10.  |@Resource     |Annotation used to inject an object that is already in the Appl­ication Context. It searches the instance by name. It also works on setter methods.|
| 11.  |@Primary      |Annotation used when no name is provided telling Spring to inject an object of the annotated class first. Used along with @Comp­onent.|
| 12.  |@Component    |Generic stereotype annotation used to tell Spring to create an instance of the object in the Appl­ication Context. It's possible to define any name for the instance, the default is the class name as camel case.|
| 13.  |@Contr­oller   |Stereotype annotation for presen­tation layer.|
| 14.  |@Repos­itory   |Stereotype annotation for persis­tence layer. |
| 15.  |@Service      |Stereotype annotation for service layer.     |
| 16.  |@Conditional  |Annotation is used to load beans into Application Context only if the given condition is met.|


#### Spring-Boot Web Annotations

|Sl.No| Annotation            | Description  |
|-----|-----------------------|--------------|
| 01. |@SpringBootApplication |	This annotation is used to qualify the main class for a Spring Boot project. The class used with this annotation must be present in the base path. @SpringBootApplication scans for sub-packages by doing a component scan.|   			
| 02. |@EnableAutoConfiguration|Based on class path settings, property settings, new beans are added by Spring Boot by using this annotation.|					
| 03. |@Controller	           |Allows detection of component classes in the class path automatically and register bean definitions for the classes automatically.|					
| 04. |@RestController	       |Used in controllers that will behave as RESTful resources. @RestController is a convenience annotation that combines @Controller and @ResponseBody.	|				
| 05. |@ResponseBody	       |Makes Spring to convert the returned object to a response body. This is useful for classes exposed as RESTful resources.|				
| 06. |@RequestMapping	       |Used to map web requests to specific handler classes and methods, based on the URI.|
| 07. |@RequestParam	       |This annotation is used to bind request parameters to a method parameter in your controller.| 
| 08. |@PathVariable	       |This annotations binds the placeholder from the URI to the method parameter and can be used when the URI is dynamically created or the value of the URI itself acts as a parameter.	|	



#### Profile

|Sl.No| Annotation            | Description  |
|-----|-----------------------|--------------|
| 01. |spring.profiles.active |Property to be set in appl­ica­tio­n.p­rop­ert­ies in order to tell Spring what profiles are active.|
| 02. |@Profile("dev")       |Annotation used to define which profile can execute the annotated method.|


#### Aspect Annotations

|Sl.No| Annotation     |USE       | Description  |
|-----|----------------|----------|--------------|
| 01. |@Aspect         |Type      |Declares a class to be an aspect.|
| 02. |@After          |Method    |Declares a method to be called after a pointcut completes.|
| 03. |@AfterReturning |Method    |Declares a method to be called after a pointcut returns successfully.|
| 04. |@AfterThrowing  |Method    |Declares a method to be called after a pointcut throws an exception.|
| 05. |@Around         |Method    |Declares a method that will wrap the pointcut.|
| 06. |@Before         |Method    |Declares a method to be called before proceeding to the pointcut.|
| 07. |@DeclareParents |Static Field |Declares that matching types should be given new parents,that is, it introduces new functionality into matching types.|
| 08. |@Pointcut       |Method    |Declares an empty method as a pointcut placeholder method.|


#### Spring-Boot Testing Annotations

|Sl.No| Annotation            | Description  |
|-----|-----------------------|--------------|
| 01.  |@AfterTransaction	  |Annotation used to identify which method needs to be invoked after a transaction is completed.|
| 02.  |@BeforeTransaction	  |Used to identify the method to be invoked before a transaction starts executing.	|			
| 03.  |@ContextConfiguration |Declares the annotated classes which will be used to load the context for the test. The location of the configuration file has to be povided to Spring.|					
| 04.  |@DirtiesContext	      |This annotation indicates the test(s) modify or corrupt the SpringApplicationContext and that it should be closed. Hence, context is reloaded before the next test is executed.|					
| 05. |@ExpectedException	  |The test method is expected to throw a particular exception, else the test fails.|
| 06. |@WebAppConfiguration	  |Used to create web version of the application context.	|				
| 07. |@Repeat	              |Specifies the test method to be executed multiple times.	|				
| 08. |@Transactional 	      |Describes transaction attributes on a method or class.	|				
| 09. |@Rollback	          |Indicates if the transaction of a test method must be rolled back after the execution of the test completed.	|     			
| 10. |@Commit	              |Indicates that the transaction of a test method must be committed after the execution of the test completed.|     		
| 11. |@Timed	              |Indicates the time limit for the test method. If the test has not completed execution before the time expires, the test fails.|					
| 12. |@TestPropertySource	  |Annotation specifies the property sources for the test class.|					
| 13. |@Sql	                  |Annotation declares a test class/method to run SQL scripts against a database.|	


##### Workflow and Tools 

|Sl.No| Category     |Tool                    | Description                         |
|-----|--------------|------------------------|-------------------------------------|
| 01. |Development	 |Spring Tool Suite (STS) |	STS is an Eclipse-based development environment that can be used to develop Spring applications easily.|
| 02. |Development	 |Eclipse	              |IDE used to develop Java applications. It has a plugin for develping Spring applications. Useful when working simultaneously on Spring and non-Spring based apps.|
| 03. |Development	 |IntelliJ IDEA	          |Provides a smooth environment and user experience for developing Spring applications. Provides a comprehensive view of the project forspeedy navigation, error highlighting, plugins for numerous purposes, code completion.|
| 04. |Unit Testing	  |JUnit	              |JUnit is a regression Testing Framework used to implement unit testing in Java with an enhanced speed and quality.|
| 05. |Unit testing	  |Mockito                |It is an open source mocking framework to create mock classes and interfaces providing realistic tests to predict the behaviour of the application.|
| 06. |Unit testing	  |JaCoCo                 |Provides support for code-coverage measurement and generates a detailed test report.|
| 07. |API Testing	  |JMeter                 |Apache’s JMeter is an open source testing tool which includes load, functional, regression and performance tests.|
| 08. |API Testing	  |Postman	              |Postman is a powerful tool used to test web services. It provides a feature to create test collections and can be used for API testing.|
| 09. |API Testing	  |REST-Assured	          |Makes API tesing in Java simple by providing behaviour driven development. It can integrate with any existing Java automation framework.|
| 10. |Monitoring	  |spring-boot-actuators  |Enables monitoring and managing Spring boot application by shipping production ready featues like health, metrics, HTTP tracing etc.|
| 11. |Monitoring	  |Micrometer	          |Micrometer is an application-neutral facade or abstraction for reporting application metrics which integrates with many monitoring systems, e.g., Graphite, New Relic and Statsd. Micrometer integrates with the metrics endpoint of spring-boot-actuators.|

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

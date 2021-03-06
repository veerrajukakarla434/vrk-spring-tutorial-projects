# vrk-spring-tutorial-projects : Documentation

* Spring Framework is one of the most popular Java EE frameworks.
* The Spring Framework is a mature, powerful and highly flexible framework focused on building **web applications** in Java.
* The Spring Framework consists of features organized into about 20 modules. These modules are grouped into Core Container, Data Access/Integration, Web, AOP (Aspect Oriented Programming), Instrumentation, Messaging, and Test, as shown in the following diagram.

![spring-overview](https://github.com/veerrajukakarla434/vrk-spring-tutorial-projects/blob/main/src/images/spring-overview.png "spring-overview")

##### Spring modules description 

* Spring is well-organized architecture consisting  of seven modules. Modules in the Spring framework are:

#### Core Container:

* The Core Container consists of the Core, Beans, Context, and Expression Language modules the details of which are as follows −

* The Core module provides the fundamental parts of the framework, including the IoC and Dependency Injection features.

* The Bean module provides **BeanFactory**, which is a sophisticated implementation of the factory pattern.

* The Context module builds on the solid base provided by the Core and Beans modules and it is a medium to access any objects defined and configured. The **ApplicationContext** interface is the focal point of the Context module.

* The SpEL module provides a powerful expression language for querying and manipulating an object graph at runtime.

#### Data Access/Integration:

* The Data Access/Integration layer consists of the JDBC, ORM, OXM, JMS and Transaction modules whose detail is as follows −

* The JDBC module provides a JDBC-abstraction layer that removes the need for tedious JDBC related coding.

* The ORM module provides integration layers for popular object-relational mapping APIs, including JPA, JDO, Hibernate, and iBatis.

* The OXM module provides an abstraction layer that supports Object/XML mapping implementations for JAXB, Castor, XMLBeans, JiBX and XStream.

* The Java Messaging Service JMS module contains features for producing and consuming messages.

* The Transaction module supports programmatic and declarative transaction management for classes that implement special interfaces and for all your POJOs.

#### Web:
* The Web layer consists of the Web, Web-MVC, Web-Socket, and Web-Portlet modules the details of which are as follows −

* The Web module provides basic web-oriented integration features such as multipart file-upload functionality and the initialization of the IoC container using servlet listeners and a web-oriented application context.

* The Web-MVC module contains Spring's Model-View-Controller (MVC) implementation for web applications.

* The Web-Socket module provides support for WebSocket-based, two-way communication between the client and the server in web applications.

* The Web-Portlet module provides the MVC implementation to be used in a portlet environment and mirrors the functionality of Web-Servlet module.

#### Spring – IoC Containers

* The Spring IoC container is at the core of the Spring Framework. 
* The container will create the objects, wire them together, configure them, and manage their complete life cycle from creation till destruction. 
* The Spring container uses dependency injection (DI) to manage the components that make up an application.

* Spring provides following two types of containers.

 * **BeanFactory container**
 * **ApplicationContext container**
 
#### 1. BeanFactory
* A BeanFactory is essentially nothing more than the interface for an advanced factory capable of maintaining a registry of different beans and their dependencies.
* The BeanFactory enables us to read bean definitions and access them using the bean factory.

#### 1.1. How to create BeanFactory
* When using just the BeanFactory we can create one and read in some bean definitions in the XML format as follows:

```console
How to Create XmlBeanFactory
InputStream is = new FileInputStream("beans.xml");
BeanFactory factory = new XmlBeanFactory(is);
 
//Get bean
HelloWorld obj = (HelloWorld) factory.getBean("helloWorld");
```

* Other ways to create bean factory are as below:
```console
//How to Create XmlBeanFactory

Resource resource = new FileSystemResource("beans.xml");
BeanFactory factory = new XmlBeanFactory(resource);
 
ClassPathResource resource = new ClassPathResource("beans.xml");
BeanFactory factory = new XmlBeanFactory(resource);
```
#### 2. ApplicationContext
* ApplicationContext container adds more enterprise-specific functionality such as the ability to resolve textual messages from a properties file and the ability to publish application events to interested event listeners. This container is defined by the org.springframework.context.ApplicationContext interface.

* The ApplicationContext container includes all functionality of the BeanFactory container, so it is generally recommended over the BeanFactory. BeanFactory can still be used for lightweight applications like mobile devices or applet based applications where data volume and speed is significant.

#### 2.1. Types of ApplicationContext
* The most commonly used ApplicationContext implementations are:

* **FileSystemXmlApplicationContext** – This container loads the definitions of the beans from an XML file. Here you need to provide the full path of the XML bean configuration file to the constructor.

* **ClassPathXmlApplicationContext** – This container loads the definitions of the beans from an XML file. Here you do not need to provide the full path of the XML file but you need to set CLASSPATH properly because this container will look bean configuration XML file in CLASSPATH.

* **WebXmlApplicationContext** – This container loads the XML file with definitions of all beans from within a web application.

#### 2.2. How to create ApplicationContext
* A sample code for application context instantiation will look like this.
```console
//How to create ApplicationContext

ApplicationContext context = new FileSystemXmlApplicationContext("beans.xml");
HelloWorld obj = (HelloWorld) context.getBean("helloWorld");
```
#### Difference between BeanFactory and the ApplicationContext

* The org.springframework.beans.factory.BeanFactory and the org.springframework.context.ApplicationContext interfaces acts as the IoC container. 
* The ApplicationContext interface is built on top of the BeanFactory interface. 
* It adds some extra functionality than BeanFactory such as simple integration with Spring's AOP, message resource handling (for I18N), event propagation, application layer specific context (e.g. WebApplicationContext) for web application. So it is better to use ApplicationContext than BeanFactory.



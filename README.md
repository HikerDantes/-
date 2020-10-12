# -Spring框架
a. 概述
Spring框架，可以解决对象创建以及对象之间依赖关系的一种框架。
			且可以和其他框架一起使用；Spring与Struts,  Spring与hibernate
			(起到整合（粘合）作用的一个框架)
Spring提供了一站式解决方案：
	1） Spring Core  spring的核心功能： IOC容器, 解决对象创建及依赖关系
	2） Spring Web  Spring对web模块的支持。
						- 可以与struts整合,让struts的action创建交给spring
					    - spring mvc模式
	3） Spring DAO  Spring 对jdbc操作的支持  【JdbcTemplate模板工具类】
	4） Spring ORM  spring对orm的支持： 
						 既可以与hibernate整合，【session】
						 也可以使用spring的对hibernate操作的封装
	5）Spring AOP  切面编程
	6）SpringEE   spring 对javaEE其他模块的支持
b. 开发步骤
spring各个版本中：
	在3.0以下的版本，源码有spring中相关的所有包【spring功能 + 依赖包】
		如2.5版本；
	在3.0以上的版本，源码中只有spring的核心功能包【没有依赖包】
		(如果要用依赖包，需要单独下载！)


1） 源码, jar文件：spring-framework-3.2.5.RELEASE
	commons-logging-1.1.3.jar           日志
spring-beans-3.2.5.RELEASE.jar        bean节点
spring-context-3.2.5.RELEASE.jar       spring上下文节点
spring-core-3.2.5.RELEASE.jar         spring核心功能
spring-expression-3.2.5.RELEASE.jar    spring表达式相关表

以上是必须引入的5个jar文件，在项目中可以用户库管理！

2） 核心配置文件: applicationContext.xml  
	Spring配置文件：applicationContext.xml / bean.xml
	
	约束参考：
spring-framework-3.2.5.RELEASE\docs\spring-framework-reference\htmlsingle\index.html
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:p="http://www.springframework.org/schema/p"
    xmlns:context="http://www.springframework.org/schema/context"
    xsi:schemaLocation="
        http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context
        http://www.springframework.org/schema/context/spring-context.xsd">
	
</beans>   

3）Api
public class App {

	// 1. 通过工厂类得到IOC容器创建的对象
	@Test
	public void testIOC() throws Exception {
		// 创建对象
		// User user = new User();
		
		// 现在，把对象的创建交给spring的IOC容器
		Resource resource = new ClassPathResource("cn/itcast/a_hello/applicationContext.xml");
		// 创建容器对象(Bean的工厂), IOC容器 = 工厂类 + applicationContext.xml
		BeanFactory factory = new XmlBeanFactory(resource);
		// 得到容器创建的对象
		User user = (User) factory.getBean("user");
		
		System.out.println(user.getId());
		
	}
	
	//2. （方便）直接得到IOC容器对象 
	@Test
	public void testAc() throws Exception {
		// 得到IOC容器对象
		ApplicationContext ac = new ClassPathXmlApplicationContext("cn/itcast/a_hello/applicationContext.xml");
		// 从容器中获取bean
		User user = (User) ac.getBean("user");
		
		System.out.println(user);
	}
}

2.2 Spring框架
a. 概述
Spring框架，可以解决对象创建以及对象之间依赖关系的一种框架。
			且可以和其他框架一起使用；Spring与Struts,  Spring与hibernate
			(起到整合（粘合）作用的一个框架)
Spring提供了一站式解决方案：
	1） Spring Core  spring的核心功能： IOC容器, 解决对象创建及依赖关系
	2） Spring Web  Spring对web模块的支持。
						- 可以与struts整合,让struts的action创建交给spring
					    - spring mvc模式
	3） Spring DAO  Spring 对jdbc操作的支持  【JdbcTemplate模板工具类】
	4） Spring ORM  spring对orm的支持： 
						 既可以与hibernate整合，【session】
						 也可以使用spring的对hibernate操作的封装
	5）Spring AOP  切面编程
	6）SpringEE   spring 对javaEE其他模块的支持
b. 开发步骤
spring各个版本中：
	在3.0以下的版本，源码有spring中相关的所有包【spring功能 + 依赖包】
		如2.5版本；
	在3.0以上的版本，源码中只有spring的核心功能包【没有依赖包】
		(如果要用依赖包，需要单独下载！)


1） 源码, jar文件：spring-framework-3.2.5.RELEASE
	commons-logging-1.1.3.jar           日志
spring-beans-3.2.5.RELEASE.jar        bean节点
spring-context-3.2.5.RELEASE.jar       spring上下文节点
spring-core-3.2.5.RELEASE.jar         spring核心功能
spring-expression-3.2.5.RELEASE.jar    spring表达式相关表

以上是必须引入的5个jar文件，在项目中可以用户库管理！

2） 核心配置文件: applicationContext.xml  
	Spring配置文件：applicationContext.xml / bean.xml
	
	约束参考：
spring-framework-3.2.5.RELEASE\docs\spring-framework-reference\htmlsingle\index.html
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:p="http://www.springframework.org/schema/p"
    xmlns:context="http://www.springframework.org/schema/context"
    xsi:schemaLocation="
        http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context
        http://www.springframework.org/schema/context/spring-context.xsd">
	
</beans>   

3）Api
public class App {

	// 1. 通过工厂类得到IOC容器创建的对象
	@Test
	public void testIOC() throws Exception {
		// 创建对象
		// User user = new User();
		
		// 现在，把对象的创建交给spring的IOC容器
		Resource resource = new ClassPathResource("cn/itcast/a_hello/applicationContext.xml");
		// 创建容器对象(Bean的工厂), IOC容器 = 工厂类 + applicationContext.xml
		BeanFactory factory = new XmlBeanFactory(resource);
		// 得到容器创建的对象
		User user = (User) factory.getBean("user");
		
		System.out.println(user.getId());
		
	}
	
	//2. （方便）直接得到IOC容器对象 
	@Test
	public void testAc() throws Exception {
		// 得到IOC容器对象
		ApplicationContext ac = new ClassPathXmlApplicationContext("cn/itcast/a_hello/applicationContext.xml");
		// 从容器中获取bean
		User user = (User) ac.getBean("user");
		
		System.out.println(user);
	}
}

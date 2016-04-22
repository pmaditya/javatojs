---
layout: post
title:  "What is Spring Container"
date:   2016-04-22 18:49:41 -0700
categories: node
---

To understand Spring container we need to understand two terms before, **Inversion of Control** and **Dependency Injection**. The basic idea of dependency injection is that the object just creates the dependencies via constructor or setter methods and allows an assembler/container to create an object with these dependencies. This is in contrast with the regular way we create objects and its dependencies using the **new** keyword.  Let us look at these two classes to understand the contrast between them.

First Version : 

    Class PersonService{
    private DataSourceDao dataSourceDao;
    private SearchSao searchSao;
	
	PersonService(DataSourceDao datasourceDao, SearchSao searchSao){
	this.dataSourceDao = datasourceDao;
	this.searchSao = searchSao;
    }

Second Version : 

    Class PersonService{
    private DataSourceDao datasourceDao = new MysqlDataSourceDao();
    private SearchSao searchSao = new CloudSearchSao();
    }
Which of the above code is more flexible ? First Version isn't ? The first version creates dependencies that it requires a dataSource and SearchSao, and others to customize it whereas the second one has created objects of dependencies itself. 

**What is spring container has to do with this ?** Spring container instantiates the objects and injects the dependencies (assemble them) for those objects and returns them. They also manage the life cycle of these objects. Any object that is created by the spring container is called `Spring Bean`. 

**How will spring get to know what objects to create and what dependencies to inject inside them ?** Spring does not know by itself, as an application developer you have define them in a configuration either via XML, Java Config or Annotations. 

**So essentially SpringContainer is a BeanFactory (A factory class that creates Beans) ?** It is more than that. But to understand it at a high level spring container/Bean Factory provides a method to get a bean object and it makes sure that the object initialized is assembled properly with its dependencies. 

    <T> getBean(String name, Clazz T)

ApplicationContext extends BeanFactory and provides enterprise support functionality. To initialize the spring container we need to create an object of BeanFactory or ApplicationContext with some configuration like XML.

    ApplicationContext applicationContext = new ClassPathApplicationContext("context.xml")
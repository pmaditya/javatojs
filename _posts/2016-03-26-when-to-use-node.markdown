---
layout: post
title:  "My Experience with Node.js"
date:   2016-03-26 18:49:41 -0700
categories: node
---

I have been developing applications in Java/J2EE environment from past 8 years and I am very much comfortable with the support it provides. Recently I was talking with my ex-collegue and he hinted me that their team uses node.js and that aroused me some curiosity to find out what node is? and I started looking for Node.

I started looking out for some online tutorials and using that information I was able to run the run a node application in 5 minutes. It is a basic `hello world` application but the node was able to host a server on `port` and I was able to run it, this was never my experience with any of the Java based containers like Tomcat or others. Here is my first code which ran my application.

{% highlight javascript %}
var http=require("http");

var server = http.createServer(function(request,response){
    response.end("Hello World");
});

server.listen("8080", function(){
    console.log("running on port 8080");
});
{% endhighlight %}

I haven't understood what `require` meant but I just copy pasted the code and type ran it. With in a second my server was up and when I hit `http://localhost:8080` I was able to see my `Hello World` greeting. I never saw any server that gets started in a second, so I was amazed by its speed so started thinking why where can I use this node in my real world ? Can we replace all the java or other servers with Node ? The answer is `NO`.

**Why is Node so popular ?**

	1. Node is incredibely simple. Easy to install and use
	2. Nodes package manager(**npm**) is modular.
	3. Node ecosystem is on fire.
	4. Node scales well, built on google v8 engine. Single threaded application. 
	5. Amazon web services, heroku, windows azure. We can use elastic beanstalk deployment for node.js
    6. Non blocking, asynchronous nature.


**What real world problems can be solved with Node ?**

There are two types of applications -  `IO intensive`, `CPU intensive`. IO intensive applications uses a lot of disk IO or network IO. For example retrieving data from a database in the same machine or from an another server can be considered as an IO task. For these kind of tasks the server thread will be waiting for a response from the disk or network to complete the request. CPU intensive applications makes a lot of calculations on CPU cycles and thread will not be in idle state. Node is good for IO intensive applications, where it has an event loop which takes requests and makes IO calls and then continues to take another requests. If the IO operation gets completed a callback function will be invoked which perform the necessary task.

Applications that can be used by node are called as `DIRTy` applications - Data intensive real time applications. 

	*Designed for responsive
	*Doing small operations like proxy content between servers etc
	*Online whiteboard collobaration
	*Real time pinpointing of transit buses. 
	*Responds instantly to large number of users.

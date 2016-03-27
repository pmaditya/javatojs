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

Let us see how the node is built and why is it so fast :

What real world problems can be solved with Node ?
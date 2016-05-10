![AIDAX logo](https://raw.githubusercontent.com/astfarias/aidax/master/files/logo/logo2-less.png)  
##Dust.js - Cheat Sheet
>*"Dust.js is a safe template engine with a great degree of flexibility, allowing you to easily customize webhook actions."*
>**Alisson Agiani - AIDAX CTO**

###Overview
Dust.js is the default templating engine used by AIDAX. This document gives an overview of the templating language syntax in your AIDAX views.

> The official Dust.js documentation can be found in http://www.dustjs.com/.

###How use

//To do

###About Variables
The variables are rendered only **if there is no spacing** between `{}`. If there is space, it will be processed as a JSON key.  

*Example:*   

In Case(1), `atributes.email` is a variable.

 - Case(1)  

	```javascript
    var variable: "{attributes.email}"	
	```

In Case(2), `atributes.email` is a JSON key.

 - Case(2)  
 
	```javascript
	var jsonKey: "{ attributes.email }"  
	```  
	  	
###Objective in Webhook Template
The user has access to three objects: `root`, `visitor_goals` and `attributes`.

 * `root  `
It contains the properties of the profile root event.   
 * `visitor_goals`  
The visitor's goals target webhook.  
 * `attributes`  
The attributes of the visitor target webhook.  

##References

* [Dust.js doc](http://www.dustjs.com/docs/)
* [Mobify doc](http://adaptivejs.mobify.com/v2.0/docs/)
* [Github user: rek - Gist Dust.js Cheatsheet ](https://gist.github.com/rek/f18a7e38b8e4e3686584)
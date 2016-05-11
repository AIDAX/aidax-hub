[![AIDAX logo](https://raw.githubusercontent.com/astfarias/aidax/master/files/logo/logo2-less.png)](http://aidaxbi.com/)
##Dust.js 2.x - Cheat Sheet with AIDAX
>*"Dust.js is a safe template engine with a great degree of flexibility, allowing you to easily customize webhook actions."*
>**Alisson Agiani - AIDAX CTO**

###Overview
Dust.js is the default templating engine used by AIDAX. This document gives an overview of the templating language syntax in your AIDAX views.

> The official Dust.js documentation can be found in http://www.dustjs.com/.

##Syntax  

####**`{reference}`**   
Insert values from your context (or JSON data) into your template.
To reference keys in the view, surround the key name in brackets like this: `{key}`  

 - Dust path: One or more Dust keys, separated by dots (`.`).
 - Dust key: One or more of the following characters: `a-z`, `A-Z`, `_` (underscore), `$`, `0-9`, or `-`
>Note: If there is space between `{}`, it will be rendered as a text.  

####**`{! comments !}`**  

```javascript
{! All Dust comments are
multiline comments !}
```  

####**`{#section/}`**  

```javascript
{#key}
  "Some content"
{:else}
  "Some other content, if key do not exist in the context."
{/key}
```  

####**`{?exists/}`**  

```javascript
{?key}"Show if key exist!"{:else}"Else show this"{/key}
```

####**`{^not-exists/}`**  

```javascript
{^key}"Show if key does not exist"{:else}"Else show this"{/isReady}
```

####**`{@helper/}`**   

```javascript
{@eq key=email value="contact@aidax.com.br"}
  This e-mail belongs to AIDAX
{:else}
  This is a new e-mail.
{/eq}

```

#####**Logic Helpers**   

 - `{@eq}`: Strictly equal to
 - `{@ne}`: Not strictly equal to
 - `{@gt}`: Greater than
 - `{@lt}`: Less than
 - `{@gte}`: Greater than or equal to
 - `{@lte}`: Less than or equal to

#####**Casting**
```javascript
{@eq key=foo value="50" type="number"} Casting value {/eq}
```
#####**Separator Helper (Loop)**  

 - `{@sep}`: Output for every loop iteration except the last
 - `{@first}`: Output only on the first loop iteration
 - `{@last}`: Only output on the last loop iteration

#####**Select Helper (Switch-like)**  

- `@select`: Take one action based on multiple comparisons with a single key value
- `@none`:  What to do if none of the conditions are true
- `@any`: Run if any of the conditions are true
How use
```javascript
<span class="
  {@select key=testEnabled}
    {@any}test-enabled {/any}
    {@none}test-disabled {/none}
    {@eq value="email"}test-email{/eq}
    {@eq value="name"}test-name{/eq}
  {/select}
">
```
#####**Math Helper**  

- `{@math}`: Perform simple math operations
-  It accepts `key` and `method` parameters as well as an `operand` parameter for operations that require two values, like adding or subtracting.
	- `method` can be: add, subtract, multiply, divide, mod, ceil, floor, round, toint, abs  

```javascript
{@math key=$idx method="mod" operand="2"}
   {@eq value="0" type="number"} class="foo"{/eq}
{/math}
```
#####**Debugging with `@contextDump`**  

 - `{@contextDump}`: Helper outputs the current context portion of the JSON data model to the output 
 - `key="full"` or `"current"`: Print the context
 - `to="console"` or `"output"`: Print to the console or output stream

```javascript
{#foo}
  {! Default: key="current" and to="output" !}
  {@contextDump/}
  {! Check your console for the full context !}
  {@contextDump key="full" to="console"/}
{/foo}
```

####**`{>partial/}`**  
Include one dust template inside of another dust template.
```javascript
{> my_template /}
```

####**Blocks: `{+partial}`**  
Pre-define several blocks in the common base template, and then override certain blocks as necessary.  

```javascript
{+classNames} "Hello" {/classNames} "world!"
```

####**Block Overrides:`{<inline-partial/}`**   
Can override the default header block in a child template like this:

```javascript
{+classNames} "Hello" {/classNames} "world!"
{<classNames} "By" {/classNames}
```

####**`{~special}`**  
A special is converted to a special character  

 - `{~s}` becomes a single space
 - `{~n}` becomes a new line
 - `{~r}` becomes a carriage return
 - `{~lb}` becomes a left curly brace `{`
 - `{~rb}` becomes a right curly brace `}`


###About Variables
The variables are rendered only **if there is no spacing** between `{}`. If there is space, it will be rendered as a text.  

*Example:*   

In Case(1), `atributes.email` is a variable.

 - Case(1)  

	```javascript
    var variable: "{attributes.email}"	
	```

In Case(2), `atributes.email` is a text.

 - Case(2)  
 
	```javascript
	var text: "{ attributes.email }"  
	```  
	  	
###Objective in Webhook Template
The user has access to three objects: `root`, `visitor_goals` and `attributes`.

 * `root`: It contains the properties of the profile root event.   
 * `visitor_goals`: The goals of visitor target of the webhook .   
 * `attributes`: The attributes of visitor target of the webhook.   

##References

* [Dust.js doc](http://www.dustjs.com/docs/)
* [Mobify doc](http://adaptivejs.mobify.com/v2.0/docs/)
* [Github user: rek - Gist Dust.js Cheatsheet ](https://gist.github.com/rek/f18a7e38b8e4e3686584)
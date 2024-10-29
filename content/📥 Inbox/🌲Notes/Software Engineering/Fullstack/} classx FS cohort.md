---
tags: 🧠️/📥️/🏛️/🟥️
source: Harkirat Singh
publish: true
parent: Fullstack
aliases: 
type: course
status: 🟥
---

Related: 
URL: 


### [[Javascript|JS]]
#### Basics of Javascript: 

* some history: 
	* programming language is an abstraction to assembly language, which is further an abstraction of 0's and 1's that the machine can actually understand. Recently, we have been able to generate even programming language through LLM's. When this is properly functional, we will consider english to be an abstraction of programming language as well. Keep in mind, the logic across the abstractions remains the same. 
	* A browser has specific needs , due to which scripting languages were introduced. eg. when i press `this` button, `this` should happen. ECMAScript standard was used so that even if different browsers had different engines that were based on different scripting languages, they could still function the same way. Consequently, even JS compilers follow the same standard. Every few years, ECMAscript standard changes, and compilers and browsers need to keep up. 
	* Node.js:  The compiler from the browser engine is extracted and used independantly. its not a framework or a language. 
		* C++, Java, Javascript, Golang, Rust are some other programming languages that can be used for backend. 
		* But 
* Javascript datatypes Basics: 
	* Variables: 
		* numbers `var name="asish"`
		* strings `var age=29`
		* arrays `var names = ["asish","ashu","sharmaji"]`
			* easier to iterate through arrays 
		* objects 
			* key value pair stores
			* `var user_and_age = ["asish",28,"sharma",1995]` can be used to represent array with multiple values, but this is a complicated data structure. 
			* instead, write like this```
			  	var user1={
					  	name: "asish",
					  	age: 29
					  	}
			  	var user2={
					  	name:"rick",
					  	age:72
					  	}
			  	var user3={
					  	name:"morty",
					  	age:14
					  	}
				
			  	```
	* Loops: 
		* for
		* while
	* Functions
		* primitive
		* callbacks
	* API's
		* Native
		* Web
	* 
* Async JS
	* Async JS![[Async javascript]]
 * 
* 



[[callback function]]


using ==> instead of callback for compact code? ❔



### Week 2. Intro to express, Node.js, backend

Things you need to understand in backend: 
- HTTP servers
- Authentication
- databases
- middlewares

---


- #### HTTP servers: 
	- request methods: 
	- URL route
	- query parameters, headers and body
	- status codes
	- Response: HTML, Json, text
	- cors 

Client server model: 
In the early days of the internet, machines existed independently. Typically, only huge institutions, mostly colleges had big machines, which ran moderately complex algo's. 
In the client server model, when big machines are connected to smaller `clients` which just provide the commands to run on the big machine `server` which has the computational power to execute the logic behind the commands/query/code. Post executing the cmd, result is again sent back to be viewed/acted upon to the client device. This is the [[client-server model]] 

clients and servers need to follow certain protocols so that there is no confusion, and one such protocol is [[HTTP]] protocol. (Hyper-text-transfer-protocol)
These are rules on how incoming and outgoing messages are to be. 

 - What to know to send a HTTP request: 
	 - URL
		 - eg. http://chat.openai.com
	 - Route
		 - eg. .....com/backend-api/conversation
		 - / is also a request. 
	 - port
- 
- Structure of a node.js app
	- package.json -- has all the package details, including versions, in a json format. sort of a check before running the `.js` file
	- npm modules -- has the 
	- .js files 

example: creating a server that returns sum of all numbers until a particular number queried(through multiple means)
Packages are libraries written by many people for [[Javascript]] for specific usecases. 
`fs` is a package that comes inbuilt with NodeJS. 
the E in MERN stack stands for [[Express library]]. 
how to install it? 
```terminal
npm install express
```
(useful code snippets :: starting boiler plate code for express) 
```js 
const express = require('express')](<const express = require('express')
const app = express()
const port = 3000

app.get('/', (req, res) =%3E {
  res.send('Hello World!')
})

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`)
})
```

a simpler form of writing the above for better understanding
```Javascript
const express = require('express')](<const express = require('express')
const app = express()
const port = 3000

function handleFirstRequest(req, res){
 res.send("hello world!");
}

app.get('/', handleFirstRequest)

function started(){
 console.log(`example app listening on port ${port}`)
}

app.listen(port, started)
```


```js
setInterval(fn,1000); //runs the function `fn` endlessly at an interval of 1000ms
setTimeout(fn,1000); //runs the function `fn` and stops all processes related to it after 1000ms. If fn has completed running, well and good, if not, then fn is cut short. 
```

The `setInterval` process used above is a [[Long running process]]. Similarly, the process `app.listen(port, fn)` needs to be a [[Long running process]], which makes sure the process runs indefinitely. `app.listen` in addition to being a long running process listens for any requests at that port 3000. 

now, the above sample code only listens on the base route, of `/`. We need to do different things when different routes are called. Therefore, a `app.get()` needs to be written for every route, not just for the default `/` route

How can user pass an input?
	Can be passed through either or all of `query parameters, headers, or body`

---

#### Query parameters: 

these are passed through the URL itself through the following syntax: 
```
localhost:3000/handleSum?counter=1000&counter2=2000

```
the counter needs to be used in the js file as well. the `req` parameter contains this data(as well as header and body data), and it can be accessed in the js file by using `req.query.counter` and `req.query.counter2`

The route typically tells us which algorithm to run, and the parameters, header and body specify the inputs 

There are other type of requests. The type of requests for HTML protocol are : GET, POST, PUT, DELETE. 
Everything can be done using GET, but for other reasons, the standard is to use appropriate requests. 
The default when you visit a website is a GET requests, with the route '/' 

- [ ] doubt:Why so many request types in Postman,if the only ones in the protocol are GET, POST, PUT and DELETE. #task/❔

Why do you need header?






## Middlewares
```javascript
function middleware(req, res, next){
//here, req is the request received from the 
// `next` controls to which request the control is transferred to after the middleware operations are performed on the request. The request query `req` is sent as it is.
}
```

- what is it?
	- 
* There are a lot of middleware written by [[Javascript|JS]]  programmers for common use cases which we can simply use as a black box
* you don't need to understand the inner workings of these. 
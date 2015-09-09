#Introduction to Angular JS
- Angular is a great framework that allows you to write front end code in a sort of MVC pattern.
- The library wraps in many utility functions such as AJAX and data binding that are a part of the core functionality.
- Angular also gives us a clean format for writing single-page applications (SPAs).

##App Setup
- Angular apps have some basic configuration that we need to do before they can be run.
- We will need the main script located [here](https://angularjs.org/).
- Because Angular uses AJAX to load in its views, it's best to run any Angular app via a server.
- We will be using simplehttpserver that we downloaded earlier to accomplish this.

##Running a Simple Server
- When we load in additional views later in the course we will need to run a simple server to see the result.
- This is due to CORS permissions that are avoided by running the server.
- We will be using a module called Python SimpleHTTPServer.
- To run the server in a specific directory, navigate to the directory via your terminal and type the following command:

```
python -m SimpleHTTPServer 3000
```

- Replace the 3000 with a port of your choice. 

##Data Binding
- One of the core aspects of Angular is data binding.
- Angular is a two-way binding system. This means that data that is inputted on the HTML side is also immediately available to JavaScript.
- For example, form fields that are filled out are accessible without any additional code. How did we used to do it?
- Data binding is accomplished through the `$scope` variable, which is a common theme throughout any Angular application.
- Let's see an example:

```html
<input type="text" ng-model="userEntry" />

<div>
	{{ userEntry }}
</div>
```

- Because of this we don't have to do tons of extra work grabbing things from the DOM and adding event listeners and such.
- All data within views is accessible via `$scope`.

##Angular Modules
- Modules are like a container for different parts of the application.
- They are like the main hub that links up controllers, services, filters, directives, and more.
- This allows your code to be reusable throughout your application.
- Modules can be loaded in any order, or even in parallel, because the modules delay execution.
- They are declared on the HTML side by the `ng-app` directive.

#####Modules can be attached to elements, even the `body` or `html` tags

HTML

```html
<div ng-app="myApp">
</div>
```

JS

```javascript
var myAppModule = angular.module("myApp", []);
```

- Now this functionality is hooked up to Angular, and can be manipulated using controllers, services, factories, etc.

##Controllers
- Controllers are sort of the brain of your application.
- They are responsible for the "business logic" of the app.
- These are what interact with that `$scope` variable we saw earlier.
- Let's see an example:

```javascript
app.controller("userListController", function($scope) {
	$scope.users = [
		{
			firstname: "Arun",
			lastname: "Sood",
			age: 28,
			username: "arsood"
		},
		
		{
			firstname: "John",
			lastname: "Doe",
			age: 34,
			username: "jdoe"
		}
	];
});
```
- To sync this with the HTML we simply can add this to the `body` tag:

```html
<body ng-controller="userListController">
```

- You can attach controllers to individual elements, but bear in mind that the `$scope` variable would only pertain to functionality inside of these elements and nothing else.

##Built-In Directives
- Angular comes packed with great features that allow us to extend the functionality of our applications.
- The first directive we will look at is `ng-repeat`.
- This allows us to loop through data and display it on the page.
- Here is an example using a table row:

```html
<tr ng-repeat="todo in todos">{{todo.todoText}}</tr>
```
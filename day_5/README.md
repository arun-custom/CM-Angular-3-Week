##Custom Directives
- We have already seen how directives enhance the functionality of the page.
- If we want to create custom functionality that can be reused throughout the app we can register our own custom directive.
- Directives can be declared via element, attribute, or class.
- The Angular team recommends using either the element or attribute form for intuitiveness.

HTML

```html
<my-todos></my-todos>
```

JS

```javascript
app.directive("myTodos", function() {
	return {
		templateUrl: "templates/todos.html",
		controller: "todoCtrl"
	}
});
```

- You can split your templates into multiple files, essentially creating a partial.
- templateUrl can be a string as in the above, but it can also be a function that gets access to the element and any related attributes.
- Imagine we had an attributes we wanted to use:

HTML

```html
<my-todos type="awesome"></my-todos>
```

JS

```javascript
app.directive("myTodos", function() {
	return {
		templateUrl: function(elem, attr) {
			console.log(elem);
			console.log(attr.type);
			return "templates/todos.html"
		},
		controller: "todoCtrl"
	}
});
```

#####Restricting directive types
- By default Angular directives are restricted to element and attribute types.
- If you want to use a directive that is triggered by a class name you will have to use the `restrict` option.
- Restrict supports three types - A, E, and C for attribute, element, and class name respectively.
- Let's see an example where we want the directive to only be available as a class name:

HTML

```html
<div class="my-todos" type="awesome"></div>
```

JS

```javascript
app.directive("myTodos", function() {
	return {
		restrict: "C",
		templateUrl: function(elem, attr) {
			console.log(elem);
			console.log(attr.type);
			return "templates/todos.html"
		},
		controller: "todoCtrl"
	}
});
```

##Movie Search Lab
- For this lab we will be building an application that can search for movies in a database and display the results.
- The frontend is already done for you [here](movie_starter_app/).
- For this project we will imagine that we want to build a widget that can pull this movie information, and that we want to use this functionality throughout our app.
- Your job is to create a directive for the search function of this app and have it render on the page.
- To hide and show the search box you will have to look into [ngShow](https://docs.angularjs.org/api/ng/directive/ngShow).
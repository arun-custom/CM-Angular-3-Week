##ngAnimate
- ngAnimate is a module that allows us to perform animations on elements selectively.
- This functionality requires the ngAnimate module from the Angular extras.
- Let's take a look at the documentation [here](https://docs.angularjs.org/api/ngAnimate/).
- Animations work by applying the `.ng-enter`, `.ng-enter-active`, `.ng-leave`, or `.ng-leave-active` classes on any of your existing classes.
- Your classes should implement some sort of CSS3 animation.
- Let's try this out with some pre-built css classes to help us out: https://github.com/Augus/ngAnimate.

##Wine List Lab Part 3
- In this part of the lab we will implement some animations between views.
- Use your existing application and create an animation between the wine list and the edit view.
- Experiment using different CSS3 properties.

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
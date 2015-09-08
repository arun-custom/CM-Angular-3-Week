##Filters
- Filters allow you to alter $scope data to transform it in some way.
- Think of it like we are passing the data through some filter before it is shown to the user or used in the JavaScript.
- Let's look at an example that will take numbers entered into an input box and multiply them by 2:

HTML

```html
<input type="text" ng-model="numbers" />
{{numbers | multiply}}
```

JS

```javascript
app.filter("multiply", function() {
	return function(input) {
		if (input) {
			var num = parseInt(input);

			return num * 2;
		} else {
			return "";
		}
	}
});
```

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

##Q&A
- Let's answer some of your questions on Angular!
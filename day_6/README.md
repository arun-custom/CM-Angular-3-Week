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

##Q&A
- Let's answer some of your questions on Angular!
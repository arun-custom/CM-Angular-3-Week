##Movie Search Lab
- For this lab we will be building an application that can search for movies in a database and display the results.
- The frontend is already done for you [here](movie_starter_app/).
- For this project we will imagine that we want to build a widget that can pull this movie information, and that we want to use this functionality throughout our app.
- Your job is to create a directive for the search function of this app and have it render on the page.
- To hide and show the search box you will have to look into [ngShow](https://docs.angularjs.org/api/ng/directive/ngShow).

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
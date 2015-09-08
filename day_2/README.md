##Todo List Lab
- We will be building a todo list using Angular.
- The front end is already done for you [here](todo_html/).
- Use each of the concepts we learned to make your app work.
- **Bonus:** When each todo is clicked, create a strikethrough on the todo text.
- **Bonus:** Persist your data using localStorage.

##Using $http for AJAX Calls
- So far we have seen how we can use `$scope` variables to bring data into the HTML view.
- Normally though, these values aren't hard-coded. We usually use AJAX to pull dynamic values.
- This can be accomplished through the `$http` service built into Angular.
- To use the $http service we will have to "inject" this dependency into the controller:

```javascript
app.controller("userListController", function($scope, $http) {
	$http.get("url here")
		.success(function(users) {
			$scope.users = users;
		})
		
		.error(function() { //Error here });
});
```

##Wine List Lab Part 1
- In this lab we will be using Angular to send a GET request to pull a list of wines.
- Set up a new Angular project and try to make a GET request to `http://daretodiscover.herokuapp.com/wines`.
- Use the front end provided [here](wine_manager_html/) to display the wine data on the page.
- Make a POST request to the same url with the data from the add wine modal window form.

##$routeProvider
- Routes allow you to add multiple page functionality to your app.
- Views are triggered via the location hash.
- Routes are set up on the application configuration:

```javascript
app.config(["$routeProvider", function($routeProvider) {
	$routeProvider
		.when("/wines", {
			templateUrl: "templates/wine-list.html",
			controller: "wineCtrl"
		})
		.otherwise({
			redirectTo: "/wines"
		});
}]);
```

- In order to use this new ngRoute module however it has to be one of our dependencies in our module setup:

```javascript
var app = angular.module("wineApp", ["ngRoute"]);
```

#####Accessing route parameters

- In order to access parameters that are passed into a URL, you will need to inject $routeParams into your controller:

```javascript
app.controller("wineCtrl", function($scope, $http, $routeParams) {
	console.log($routeParams.id);
});
```
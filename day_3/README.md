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

##Wine List Lab Part 2
- In this part we will use routing to full data about a specific wine and render the edit page.
- Here are the steps you will need to follow:
	- Step 1: Create a route to `/edit/:id`.
	- Step 2: Use the route parameter to make a GET request to `http://daretodiscover.herokuapp.com/wines/:id`.
	- Step 3: Display wine data in the form on edit.html.
	- Step 4: On submit of the form create a PUT request to the same URL as above to update the wine record.
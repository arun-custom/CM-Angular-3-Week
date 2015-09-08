##Factories
- Factories allow us to create Angular code that is modular and reusable.
- We can create methods within factories that can be injected into controllers throughout a module.
- This is often used to streamline work with API calls and other functionality that has to be replicated over and over.
- Let's see a simple example:

```javascript
app.factory("Helpers", function() {
	var factory = {};
	
	factory.addTo = function(array, item) {
		return array.push(item);
	}
	
	factory.removeFrom = function(array, index) {
		return array.splice(index, 1);
	}
	
	return factory;
});
```

- Now in our controller we have:

```javascript
app.controller("wineCtrl", function($scope, Helpers) {
	$scope.wines = Helpers.addTo($scope.wines, "New Wine");
});
```

##$resource
- $resource is a higher-level abstraction on $http.
- It gives us a few pre-defined routes that we can use to easily query a server backend.
- $resource assumes a classical RESTful architecture of our backend service.
- First thing we need to do to use it is include it as a dependency in our module:

```javascript
var app = angular.module("wineApp", ["ngResource"]);
```

- We can then set up our resource in our controller:

```javascript
app.controller("wineCtrl", function($scope, $http, $resource) {
	var Wine = $resource("http://daretodiscover.herokuapp.com/wines/:id", {
		id: "@id"
	}, {
		update: {
			method: "PUT"
		}
	});
});
```

- This sets up Wine as a resource with the following methods:
	- `query()` - GET /wines
	- `get()` - GET /wines/:id
	- `save()` - POST /wines
	- `update()` - PUT /wines/:id
	- `remove()` - DELETE /wines/:id
	- `delete()` - DELETE /wines/:id

##Wine List Lab Part 4
- For this lab we will be refactoring our API query code to use resources.
- Your job is to remove the $http calls and instead use $resource.
- You will also be breaking out the logic for these calls into factories.
- You may want to refer to web tutorials to help you:
	- [Angular guide](https://docs.angularjs.org/api/ngResource/service/$resource)
	- [CRUD app with resources](http://www.sitepoint.com/creating-crud-app-minutes-angulars-resource/)
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
##Wine List Lab Part 2
- In this part we will use routing to full data about a specific wine and render the edit page.
- Here are the steps you will need to follow:
	- Step 1: Create a route to `/edit/:id`.
	- Step 2: Use the route parameter to make a GET request to `http://daretodiscover.herokuapp.com/wines/:id`.
	- Step 3: Display wine data in the form on edit.html.
	- Step 4: On submit of the form create a PUT request to the same URL as above to update the wine record.

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
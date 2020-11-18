# JS client-side conventions

JavaScript is often difficult to get started with because the landscape (and
language) is vast, and the community has less adherence to conventions.

This is a conventions document for not getting into trouble in JS.

In the future, we will have a little js pack repo for copying in a good set
of standards into a new application.

## React

* Use `jsx` to build templates
* Create templates that are as declarative as possible
* Extract all logic into presenters

## Redux

* Use `react-redux` to bind state and handlers to jsx templates
* Put all state into the redux store
* Even UI related state. Once this is a pattern it becomes easy
* Don't use `jsx` in the connect files, instead create a new template
* Extract logic for handlers into a handlers area
* Extract logic reasoning about state into presenters

## Testing

* [jest](https://jestjs.io/) - for unit testing
* [cypress](https://www.cypress.io/) - for acceptance testing

### View testing

If your templates are declarative, and you extract and test logic from templates
and connector files, you shouldn't need to test React views. If the app needs
testing at the view layer use: [React Testing Library](https://testing-library.com/docs/react-testing-library/intro/)
# React-Interview-Question-Answer

## 1. What is React ?  
ReactJS, a JavaScript library for creating user interfaces, makes the development of UI components easy and modular.

## 2. fearures of React 
The key features of React are:

* **Component-based architecture:** A Component is the smallest unit in a React application. Anything that is to be rendered on the browser can be rendered through components. Components help in maintainability and re-usability.
* __Virtual DOM:__ React uses virtual DOM concept for DOM manipulation which improves the performance of the application.
* __Unidirectional data flow:__  React’s one-way data flow (also called one-way binding) keeps everything modular and fast and easy to debug.
* __JSX syntax:__ React used JSX syntax which is similar to XML and HTML syntax that makes it easy for writing markup and binding events in components. 
* __SEO performance:__ The SEO performance can be improved using the server-side rendering concept.  Isomorphic applications can be developed by using React which increases the SEO performance.

## 3. Difference between  React and Angular
  React  | Angular
------------- | -------------
React is a small view library  | Angular is a full framework
React covers only the rendering and event handling part	  | Angular provides the complete solution for front-end development
Presentation code in JavaScript powered by JSX | Presentation code in HTML embedded with JavaScript expressions
React's core size is smaller than Angular, so bit fast | Angular being a framework contains a lot of code, resulting in longer load time
React is very flexible | Angular has less flexibility
Great performer, since it uses Virtual DOM | Angular uses actual DOM which affects its performance

## 4. What is CDN ?
CDN stands for Content Delivery Network. It is a distributed network of servers that provides faster delivery of website content by caching it on multiple servers.

## 5. What is a Cross Origin Attribute ?
A Cross Origin Attribute is a security feature used in web development that allows or restricts scripts, stylesheets, images, and other resources from different domains to interact with each other.

## 6. What is Babel ?
Babel is a JavaScript transpiler that converts modern JavaScript code into a backward-compatible version that can run in older browsers. It is commonly used in web development to ensure compatibility across different platforms.

## 7. What is Webpack ?
Webpack is a module bundler for JavaScript applications. It takes modules with dependencies and generates a single bundle that can be loaded by a browser.

## 8. Can you name some other bundler ?
Some other popular module bundlers are Browserify, Rollup, Parcel, and FuseBox.

## 9. What is package.json and why it is important ?
package.json is a configuration file in Node.js projects that contains metadata about the project, such as dependencies, scripts, and other project-specific details. It is important because it helps in managing the project's dependencies and automating common tasks.

## 10. What is NPM ?
NPM stands for Node Package Manager. It is a package manager for Node.js projects that allows developers to install and manage third-party packages and dependencies.

## 11. What is Git ?
Git is a version control system used in software development to manage code changes and collaborate with other developers. It allows developers to track and revert changes, work on different branches, and merge code changes.

## 12. What is PolyFill ?
A polyfill is a piece of code that provides functionality that is not natively supported by a browser. It is commonly used to add support for new web APIs and features to older browsers.

```JavaScript
if (!Math.sign) { // if the function does not exist

// implementation

Math.sign = function(number) {

if (number > 0) {

return 1;

} else if (number < 0) {

return -1;

} else {

return 0;

}

};

}
```

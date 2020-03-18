# Coding Standards


## Philosophy
Our aspirations to become a multi platform, multi production company relies on how seamlessly these sectors integrate with one another. To make this seamless integration possible, coding standards need to be enforced. Here are a few great reason for having these standards.

1. Readability. Reading code becomes much easier. You can discern patterns easily without having to read each line, which helps in debugging, and speeds ip the process of reading, and synthesising new code.
2. Speed. Code standards help speed up the code writing process. Simple rules lead to simple execution, which helps tackle complex tasks. It also frees your mind when worrying about the look of the code.
3. Assist. With code conventions, especially ones refined on a regular basis, errors made by developers are corrected, which helps in anticipating new errors, and guiding new developers down the right path.

## Recommendations
If you’re reading this document, there’s a high chance you’re a part of the Zicli Software team. This means you should’ve gone through enough testing to make certain you’re familiar with the basics needed to do your job to the best of your abilities. If you’re just a simple internet traveler, welcome, and I hope these recommendations help you on your journey. 

In any case, to make your work easier, here are some refreshers in the basics. 

- [Eloquent Javascript, Third Edition](https://eloquentjavascript.net/)
- [Algorithms in Javascript](https://medium.com/siliconwat/algorithms-in-javascript-b0bed68f4038)
- [Data Structures and Algorithms in Javascript (video)](https://www.youtube.com/watch?v=t2CEgPsws3U)

Let's dive in!

## Folders and Files
Depending on the nature of the project (Node project or React project), the root folder tends to take on different forms. Generally, it contains the following.

- setup files (docker, gitignore, env, travis, hound, etc)
- package files (package.json, package.lock.json, yarn, etc)
- node module folder
- src folder

Most of the magic occurs in the```/src```. this is where we will focus all of the source code files used for the project.

### Naming and Hierarchy
All folders created in the src file should be named with small letters, and should use a word that distinguishes all concurrent files / folders within it (i.e a category). It should be pluralised to hint at multiple content. 

All folders must contain an index.js file, which will be used to route all exports for that folder. This means all file exports in a folder must be mapped to the index.js file, allowing for destructured imports directly from the folder throughout the code base. 

<img width="174" alt="Screenshot 2020-02-06 at 10 03 38" src="https://user-images.githubusercontent.com/60140805/73921752-3f3f6600-48c8-11ea-9b6f-63ad568a1064.png">


## Styling
We generally use the [Airbnb Javascript Style Guide (ES6)](https://github.com/airbnb/javascript) for our projects. This guide suits our coding structure well, so please take a look at it. Linting is also added to all our code, so errors will pop up whenever the styling guide isn't followed.

## Features
### Variable Declarations
All variables should be declared just once at all times, and before they are used. JavaScript does not require this, but doing so makes the program easier to read and makes it easier to detect undeclared variables that may become implied. Implied global variables should never be used. Use of global variables should be minimized. 

Type ```const``` are preferred to ```let``` at all times, i.e. ```let``` should only be used when you’re certain a variable will be reassigned. 

Names should be formed from the 26 upper and lower case letters ```(A .. Z, a .. z)```, and thethe 10 digits ```(0 .. 9)```. Avoid use of international characters because they may not read well or be understood everywhere. Do not use ```$``` dollar sign or ```\``` backslash or ```_``` underbar in names.

All variables should be in camel case (camelCase), and should describe its function. The difference in a variable storing all users, and one storing users from Canada should not be simply implied but read out.

```javascript
const allUsers;
const usersFromCanada;
```

Try to avoid using more than 4 descriptive words to name a variable.

Single letter variables should be avoided at all costs, only use single letter variables when needed for iterations in a loop or function. Even then, useful methods are available to help you avoid needing such interations (forEach, map ...)

:white_check_mark:
```javascript
  const describedValue = 45;
  foo.bar(describedValue);
```

:x:
```javascript
  const x = 45;
  foo.bar(x);
```



Buffer variables should be explicitly named and point to its function (the values it is a buffer for).

```javascript
  const userNameBuffer;
```
### Arrays
Name them for what they hold. An array of messages should be called ```messages```. An array of file names should be called ```fileNames```. Retain camelCase naming for arrays. Ensure all array names are pluralised. Arrays can be declared on a single line if they are short 

### Objects
Object declarations can be made on a single line if they are short. When an object declaration is too long to fit on one line, there must be one property per line. Property names only need to be quoted if they are reserved words or contain special characters

```javascript
const user = {
  firstName: 'john',
  lastName: 'Doe',
}
```

### Functions
When iterating through an array for use in transformation, mapping and looping methods, make use of Arrow functions. 

```javascript
this.foo.forEach(bar => {
  this.doSomething(bar);
});
```
Another place arrow functions make for cleaner and more intuitive code is in managing asynchronous code.

Promises make it far easier to manage async code (and even if you're excited to use async/await, you should still understand promises which is what async/await is built on top of!). However, while using promises still requires defining functions that run after your asynchronous code or call completes.

This is an ideal location for an arrow function, especially if your resulting function is stateful, referencing something in your object. Example:

```javascript
this.asyncFunc().then((value) => {
  this.doSomething(value);
});
```
Try to avoid using arrow functions in object methods, or as methods in classes, as they allow fo unintuitive code, inhibiting testing and creates problems if you attempt to subclass/use this object as a prototype. [Read this article for better context](https://medium.com/@charpeni/arrow-functions-in-class-properties-might-not-be-as-great-as-we-think-3b3551c440b1)

### Classes
Use uppercase CamelCase when naming all classes in the code base. This helps differentiate them from other functions and variables. Class methods should be async by defaut. Only when you're certain the logic does not use any await statements can you safely omit the async.


```javascript
class FooBar {
  static async bar() {
    // some code
  }
}
```
A class should be the focal point of its file, i.e only one class per file created, allowing for a single class export. The name of the class should be the name of the file. For example, if the file is made for creating bicycle parts:

in ```src/bicycleParts```
```javascript
export default class BicycleParts {
  static async bicycleTyre() {
    // some code
  }
}
```


## Architecture
### Imports

### Exports / Indexing

### Error Handling

### MVC

### Services

### 

## JSDoc
### Form

### Types and Members

## Git
### 

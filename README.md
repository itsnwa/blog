## setup
- from the `docs` directory
- `npm install -g gulp`
- `npm install -g node-sass`
- `npm install`
- 'git clone git@github.com:forestryio/forestry-doc-theme.git hugo/themes/forestry-doc-theme' to the `./themes/` directory

## gulp commands

- `gulp` or `gulp server`
  - Will serve the website with browser sync, watching for changes and automatically reloading
  the web browser. You may also use the external ip of your dev machine to view the
  website on other devices, such as a phone. Interactions with one instance of the website,
  will also happen on other instances.
- `gulp build`
  - will generate a "production" version of the content


## javascipt with webpack 101

Webpack let's you write modular javascipt code, and use node packages to
make your life as a developer easier. You can write your code for the web the same
way your write nodejs.

to require a module, simply do the following

`var $ = require('jquery');`

This will make jquery available on $ in the current scope, each module has it's own scope.

When writing your own modules you have to tell webpack what you want to make 'public'.
To do this you can use `module.exports =`. Here are a few example

```javascript
function awesome(){
  console.log("This is my awesome function");
  }
  module.exports = awesome;
  ```

  NOTE: I passed the name of the function, but didn't invoke it with `awesome();`. If
  I did that the value returned from the function, and not the function would
  have been exported


  Here is an example where you may have more than one thing you want to make "public"

  ```javascript
  var num = 2;
  var shh = "shh";
  var alias = "al";
  function awesome(){
    console.log("This is my awesome function");
  }

  function notAwesome(){
    console.log("this function sucks")
  }
  module.exports = {
    awesome: awesome,
    notAwesome: notAwesome,
    num: num,
    a: alias
  };

  ```

  You basically just have to wrap everything up in an object and you're good to go.


  It's also important to remember that when you use `require('thing')` you will run all of the code in the module.
  So for example

  ```javascript
  // mo.js
  console.log("I am imported");

  // main.js
  require('mo');

  // output
  // I am imported
  ```

#### npm

you can find packages you want to use on www.npmjs.com. Then install them in one of two way.

- `npm install [package] --save`
  - use this if it's a package that will be used in the source code, like Jquery.
- `npm install [package] --save-dev`
  - Use this if it's just a dev tool, like the sass compiler.


  ## settings

- theme
  - The name of the projects theme
  - jsEntryPoints
  - A list of js files that will be compiled into bundles by webpack. This is useful if you want to
  have different js files for different pages. Other js files will only be compiled if they need to be
  because of require calls.


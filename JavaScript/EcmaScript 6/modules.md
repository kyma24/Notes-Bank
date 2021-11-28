it is a good practice to divide related code into modules. Before ES6 there were some libraries which made this possible(e.g. RequireJS, CommonJS). ES6 is now supporting this feature natively.

**Considerations when using modules**:
The first consideration is **maintainability**. A module is independent of other modules, making improvements and expansion possible w/o any dependency on code in other modules.
The second consideration is **namespacing**. Before, talked abt variables and scope. As known, vars are globally declared, so it's common to have namespace pollution where unrelated variables are accessible all over the code. Modules solve this problem by creating a private space for variables.
Another important consideration is **reusability**. When writing code that can be used in other projects, modules make it possible to easily reuse the code w/o having to rewrite it in a new project.

See how should use modules in JS files.
```jsx
// lib/math.js
export let sum = (x, y) => {return x + y;}
export let pi = 3.14;

//app.js
import * as math from "lib/math"
console.log(`2p = + ${math.sum(math.pi, math.pi)}`)
```
Here are exporting the sum function and the pi variable so can use them in different files.

note that ES6 supports **modules** officially, however, some browsers aren't supporting modules natively yet. So, should use bundlers(builders) such as Webpack or Browserify to run the code.
# Organizing Code with Import/Export

# Modular Code

is code that is separated into segments (modules), where each file is responsible for a feature or specific functionality.

`Reason to separate code into modulars`

 1. **Stricter variable scope**: Variables declared in modules are private unless
  they are explicitly exported, so by using modules, you don't have to worry
  about polluting the global variable scope.

2.  **Single-responsibility principle**: Each module is responsible for
   accomplishing a certain piece of functionality, or adding a specific feature
   to the application.

3.  **Easier to navigate**: Modules that are separated and clearly named make code more readable for other developers.

4.  **Easier to debug**: Bugs have less room to hide in isolated, contained code.

5.  **Produce clean and DRY code**: Modules can be reused and repurposed throughout applications.

`Modularizing React Code`

React introduces components structures making modularizing easier.

Reamber when Mosh created a folder Components and entered new file to it... its a must ndio code doesn't look messy.

To access this snippet codes in other files mostly App.js we use the import and export keywords


`Import and Export`

Import and Export keywords helps us define variables in one file and access them from different files.
  
` Exporting Variables`

Exporting any variable — data type, or React component — allows us to access that exported
variable in other file.

Two ways of exporting:

1. #### Default Export Syntax

Only used once per file,This syntax lets us export one
variable from a file which we can then import in another file.

`Example`
```js
function howManyParks() {

  console.log("42 parks!");
}

export default howManyParks;
```
To excess this from a different file we `import`

The `export default` syntax allows us rename the exported variable to whatever
we want when importing it:

```jsx
// src/ColoradoStateParks.js
import React from "react";
import aDifferentName from "./parks/howManyParks";

function ColoradoStateParks() {
  aDifferentName(); // => "42 parks!"

  return <h1>Colorado State Parks!</h1>;
}
```

We export `React components` too since ita a function but on on `import React` per file.


```jsx
// src/parks/MesaVerde.js
import React from "react";

function MesaVerde() {
  return <h1>Mesa Verde National Park</h1>;
}

export default MesaVerde;
```

`importing component to another file`

```jsx
// src/ColoradoStateParks.js
import React from "react";
import MesaVerde from "./parks/MesaVerde";

function ColoradoStateParks() {
  return (
    <div>
      <MesaVerde />
    </div>
  );
}

export default ColoradoStateParks;
```

We can do this;

```js
export default function ColoradoStateParks() {
  // ...
}
```

.....but the export by default should be at the buttom.


2. #### Named Exports

`To export`

With named exports, we can export multiple variables from a file.

```js
// src/parks/RockyMountain.js
const trees = "Aspen and Pine";

function wildlife() {
  console.log("Elk, Bighorn Sheep, Moose");
}

function elevation() {
  console.log("9583 ft");
}

// named export syntax:
export { trees, wildlife };
```


`To import`

```js
// src/ColoradoStateParks.js
import { trees, wildlife } from "./parks/RockyMountain";

console.log(trees);
// => "Aspen and Pine"

wildlife();
// => "Elk, Bighorn Sheep, Moose"
```

We can also write named exports next to the function definition

```js
// src/parks/RockyMountain.js
export const trees = "Aspen and Pine";

export function wildlife() {
  console.log("Elk, Bighorn Sheep, Moose");
}

function elevation() {
  console.log("9583 ft");
}
```
 ### Import

 The `import` keyword lets us take variables that we've exported and use them in
other files throughout our application.

Methods of using `import`

1. #### Importing Multiple Variables

Here we use `import * from` import all variables that have being exported from given module

```js
// src/ColoradoStateParks.js
import * as RMFunctions from "./parks/RockyMountain";

console.log(RMFunctions.trees);
// => "Aspen and Pine"

RMFunctions.wildlife();
// => "Elk, Bighorn Sheep, Moose"

RMFunctions.elevation();
// => Attempted import error
```

2. #### Importing Specific Variables


`import { variable } from` we use this to get a specific variable.

```js
// src/ColoradoStateParks.js
import { trees, wildlife } from "./parks/RockyMountain";

console.log(trees);
// > "Aspen and Pine"

wildlife();
// > "Elk, Bighorn Sheep, Moose"
```
we can rename any or all variables inside our import statement

```js
// src/ColoradoStateParks.js
import {
  trees as parkTrees,
  wildlife as parkWildlife,
} from "./parks/RockyMountain";

console.log(parkTrees);
// > "Aspen and Pine"

parkWildlife();
// > "Elk, Bighorn Sheep, Moose"
```

3. #### Importing Node Modules

```jsx
// src/ColoradoStateParks.js
import React from "react";
import howManyParks from "./parks/howManyParks";
import MesaVerde from "./parks/MesaVerde";
import * as RMFunctions from "./parks/RockyMountain";

export default function ColoradoStateParks() {
  return (
    <div>
      <MesaVerde />
    </div>
  );
}

```jss
import React from "react"; - `in node_modules which contains packages on thrid party-code. 

Every time we use code from npm packages we must import React.









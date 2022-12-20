Showcases a small example of how to write architecture based rules with dependency cruiser.
Having a validator that makes sure that a controller does not use a repository directly is a good example.

Having some validation doesn't have to take a lot of time. This example shows how to do it in a few minutes.


## How to use this example
```bash
npm i
npx depcruise . --config
```

Will produce:
```bash

  warn no-orphans: index.ts
  warn no-controller-using-repository: hello.controller.ts → asd.repository.ts

✖ 2 dependency violations (0 errors, 2 warnings). 4 modules, 1 dependencies cruised
```

## Custom rule breakdown
The custom rule added here is:
    
    ```javascript
    {
      name: "no-controller-using-repository",
      from: { path: "controller" },
      to: { path: "repository" },
    } 
    ```

The prerequisite to the rule is that your project must have file names that end with `.controller.ts` and `.repository.ts` (or `.controller.js` and `.repository.js`).
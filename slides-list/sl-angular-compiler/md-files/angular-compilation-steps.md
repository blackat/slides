# Compilation steps

![alt text](./images/compiler-steps.png)

- TypeScript compiler has 3 steps.
- Angular compiler is built on top.
- 3 steps are shared.
- Add 2 more steps for instance to import `ngfactory` for advanced things.


## Program Creation

![alt text](./images/compiler-steps.png)

- TypeScript process to discover app source files.
- Start from `tsconfig.json`
- Via `import` discover all the files.
- Check the application types.



## Analysis

![alt text](./images/compiler-steps.png)

- Angular compiler takes all the TS files.
- Class by class look for Angular things (decorators, etc).
- Gather isolated information (e.g. components but not modules).



## Resolve

![alt text](./images/compiler-steps.png)

- Angular compiler looks again at the whole application.
- Look at things in a larger picture (modules).
- Global decisions and optimizations.


## Type checking

![alt text](./images/compiler-steps.png)

- Ask TypeScript to check any errors:
  - in the application
  - in the templates (expression validations)


## Emit

![alt text](./images/compiler-steps.png)

- The most expensive code in compilation.
- TypeScrit code transformation.
- Generated JavaScript code ready to run in the browser.
- Imperative code added to Angular class if needed:
  - template functions to components, etc.
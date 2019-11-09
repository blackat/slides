## How Angular works

- What the framework is doing under the hood?
- How the *application code* and the *Angular framework code* work together?
  


## Angular Parts

- **Angular compiler**, JIT or AOT, build utility.
- **Angular runtime**, framework code that ships with the application and runs in the browser.


## Angular Declarative Syntax

```javascript
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: `
    <h1>
      Welcome to {{ title }}!
    </h1>`,
  styleUrls: ['h1 { font-weight: normal; }']
})
export class AppComponent {
  title = 'Angular is awesome!';
}
```

- Make component development easier.
- *Angular runtime* cannot understand it.
- Must be turned into JavaScript.


## Angular Compiler

![alt text](./images/compiler-steps.png)

- **Angular compiler**
  - jump in the TS compilation process.
  - transform *decorators*, *templates* into TS.
- **TypeScript**
  - type check application code.
  - emit JS *Angular runtime* can execute.


## Invoke ngc

In `package.json` add

```javascript
"scripts": {
  ...
  "compile": "ngc"
},
```

In the `tsconfig.json` generate `d.ts` files

```javascript
"compilerOptions": {
  ...
  "declaration": true,
  ...
}
```

- Compiled code with *factory functions*.
- See instructions *Angular runtime* executes.


## Component Defintion

```javascript
export function View_AppComponent_0(_l) {
  return i1.ɵvid(0,[
      (_l()(),
      i1.ɵeld(0, 0, null, null, 1, "h1", [], null, null, null, null, null)),
      (_l()(), i1.ɵted(1, null, ["Welcome to ", "!"]))],
    null,function(_ck, _v) {
      var _co = _v.component;
      var currVal_0 = _co.title;
      _ck(_v, 1, 0, currVal_0);
    });
}
```

- `@angular/compiler` generates instructions *Angular runtime* can understand.
- *Angular runtime* implements those instructions to run the application.


## Application Bootstrap

1. **Module bootstrap**, module setup
2. **Component bootstrap**
    1. View creation
    2. Change detection


## Component Bootstrap

<pre><code class="hljs" data-line-numbers="5" data-trim data-noescape>
@NgModule({
  declarations: [AppComponent],
  imports: [BrowserModule,FormsModule],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
</code></pre>

- Look for the component to bootstrap.
- Locate the *root element*.
- Create instance of the *root component*.


## Factory Functions

```javascript
export function View_AppComponent_0(_l) {
  return i1.ɵvid(0,[(_l()(),
      i1.ɵeld(0, 0, null, null, 1, "h1", [], null, null, null, null, null)),
      (_l()(), i1.ɵted(1, null, ["Welcome to ", "!"]))],
      ...});
}
export function View_AppComponent_Host_0(_l) {
  return i1.ɵvid(0,[
      (_l()(),i1.ɵeld(0,0,null,null,1,"app-root",[],null,null,null,View_AppComponent_0,RenderType_AppComponent)),
      i1.ɵdid(1, 49152, null, 0, i2.AppComponent, [], null, null)],null,null);
}
var AppComponentNgFactory = i1.ɵccf(
  "app-root",i2.AppComponent,View_AppComponent_Host_0,{},{},[]);
export { AppComponentNgFactory };
```

- Angular compiler generates *factory functions*.
- A factory function tells runtime how to create a component with its dependencies.
## TS Compilation model

- `library.ts` compiled into `library.js`
- JavaScript code:
  - has not type information;
  - ready to be executed in the browser.
- `library.d.ts` type declaration file:
  - describe the *interface*


## Definition file

- `app.ts` imports a library from npm

```javascript
import {AwesomeLib} from 'awesome-lib';
// use the lib
```

- `library.d.ts` brings type information.
- TypeScript can static type check.

```javascript
declare class AwesomeLib {
    awesomeMethod(): string;
}
```


## <i class="fab fa-angular angular-logo-medium"></i> Compilation Model

Angular component

```javascript
@Component({
    selector: 'awesome-comp'
})
export class AwesomeComponent {
    @Input() value: string;
}
```

Component definition file

```javascript
export declare class AwsomeComponent() {
    value: string;
    static ngComponentDef: ng.ComponentDef<
        AwsomeComponent,
        `awesome-comp`,
        {value: 'value'}
    >;
}
```


## Definition file changed

- Similar to the TypeScript one.
- `library.d.ts` file changed: selectors, inputs...
  - component public API;
  - compiler can use the component.


## Template checking

- Compiler knows the component is an instance of what is in the library.

app template uses component from library

```html
<awesome-comp [value]="a value">
    just a component
</awesome-comp>
```

definition library

```javascript
export declare class AwsomeComponent() {
    value: string;
    static ngComponentDef: ng.ComponentDef<
        AwsomeComponent,
        `awesome-comp`,
        {value: 'value'}
    >;
}
```

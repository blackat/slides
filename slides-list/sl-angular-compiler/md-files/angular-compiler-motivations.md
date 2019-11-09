# A compiler? Really?

> Why does Angular have a compiler at all?

- The Angular compiler `ngc` turns the template into code to be executed by a browser.
- Compile HTML templates into generated JavaScript code to build render and change detection at runtime.


## Declarative templates

```javascript
@Component({
  selector: 'app-hero-parent',
  template: `
    <h2>{{master}} controls {{heroes.length}} heroes</h2>
    <app-hero-child *ngFor="let hero of heroes"
      [hero]="hero"
      [master]="master">
    </app-hero-child>
  `
})
export class HeroParentComponent {...}
```

- Templates *Angular declarative syntax*: HTML, bindings, etc.
- No change detection mechanism.
- The browser does not understand.



## Imperative code

- Angular compiler transforms the template into imperative code.
- The browser can understand it.
- Less boilerplate code.
- Optimizations follow browser evolution.


## JIT vs. AoT

- JIT: imperative code is generated at *runtime*
  - compiler comes with the application
  - mainly for development
- AoT: imperative code is generated at built time
  - faster
  - mainly for production

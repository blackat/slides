## Welcome to Angular

```javascript
@Component({
  selector: "app-root",
  templateUrl: `
    <div style="text-align:center">
      <h1> Welcome to {{ title }}!</h1>
    </div>
    <input [(ngModel)]="title">`,
  styleUrls: [...]
})
export class AppComponent {
    @Input() title = "Angular!";
}
```

- `ng build --aot`
- `ngx http-server dist/my-app`
- Compile/bundle the application to be executed.


## Angular parts

- **Angular compiler**, JIT or AOT, build utility.
  - Transform templates into code *runtime* can execute.
  - Use interfaces methods.
- **Angular runtime**, framework code that ships with the application.
  - Interface implementation.
  - *Execute application code.*


## Boostrap sequence

<img src="./images/angular-platform.png" width="45%">

- `main-es2015.js` IIEF bootstraps the platform.
- Platform instanciates the.
- Application bootstraps the root component.
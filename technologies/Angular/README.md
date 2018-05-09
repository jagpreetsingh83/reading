# Angular JS

[Udemy Course - `maximilian schwarzmüller`](https://www.udemy.com/the-complete-guide-to-angular-2/)

## Basics

> **`Why do we need Node?`**: Angular Cli internally uses Node and also to manage dependencies along with running a web server.

> **`Why do we need a Web Server?`**

* **Absolute links relative to a domain name**  
  I mean if you try to reference a resource with an absolute path from the root path of your domain. This won't probably work with the file protocol since its root path is the root folder of your file system

* **JavaScript and AJAX**  
  JavaScript doesn't work well with the file:// protocol and you can some security restrictions according to browsers.

> **JWT Token?** `header.payload.signature`

> `main` file contains the application code and `vendor` file contains the angular

> A component must have a template.

> View Encapsulation

* ViewEncapsulation._Emulated_
* ViewEncapsulation._Native_
* ViewEncapsulation._None_

> Selector by ID and Psuedo selectors are not supported by Angular. `[attribute]` and `.class` works fine!

> `$event` in the template represents the data emitted by the event.

> `Components` are `Directives` with templates.

> `*ngIf else`

```html
<div *ngIf="isValid;else other_content">
    content here ...
</div>
<ng-template #other_content>other content here...</ng-template>
```

> If you add `accessors` to the constructor arguments you don't have to declare the properties in the class - **TypeScript Feature**

> In `angular-cli.json` file, the paths are relative to `index.html`

> Debugging https://augury.angular.io/

![SourceMap](./images/sourcemap.png 'Debugging .ts files in chrome debugger')

> Always configure your server to return `index.html` instead of `404` and then display an error page if you want. (This is the default behavior of the server spun up by `angular-cli`)

> There is a `<base href="/">` setting in index.html which can be configured.

> `@Injectable` decorator declares that we can now inject stuff!

> Instead of using type `any` prefer inline type definition e.g.

```javscript
serverData : { name: string, content: string}
```

> Anything between the opening and closing tag of your own tag is simply ignored/removed by Angular.

> Custom events don't propagate up.

> backgroundColor is a DOM property and DOM properties do not have `-` dashes.

## Directive

> `Directives` are instructions in the DOM.

> `*ngIf` \* respresents this directive as a structural directive.

> We can't have more than one structural directive on one element.

> Use renderer approach for DOM manipulation since its platform agnostic (Isomorphic rendering)

> Following are identical

```
<div *ngIf="something">
    Hello
</div>
```

```
<ng-template [ngIf]="something">
    <div>
        Hello
    </div>
</ng-template>
```

> Following are identical

```
<input [value]="currentHero.name"
       (input)="currentHero.name=$event.target.value" >
```

```
<input [(ngModel)]="currentHero.name">
```

> Directives are very powerful e.g. the following custom directive performs count based ng repeat

```
import {Directive, Input, TemplateRef, ViewContainerRef} from '@angular/core';

@Directive({selector: '[biRepeat]'})
export class CountRepeatDirective {

  constructor(private templateRef : TemplateRef < any >, private viewContainer : ViewContainerRef) {}

  @Input('biRepeat')set count(c : number) {
    this
      .viewContainer
      .clear();
    for (var i = 0; i < c; i++) {
      this
        .viewContainer
        .createEmbeddedView(this.templateRef);
    }
  }
}
```

## Modules

> You must not declare the same `Component, Directive or a Pipe` in more than one module. However, import is OK! If this is absolutely necessary e.g. you have Directive that is needed in two places AppModule and a FeatureModule OR a Feature Module 1 and a Feature Module 2 then you should create a new module to contain this shared Directive. It is a nice trick to have your `CommonModule` imported in this shared module.

> `.forRoot()` is only called in AppModule while `.forChild()` is called in feature module e.g. for the `Router definition`.

> `Service provider` should should ideally be with `AppModule` since you would generally want the services to be available as singleton and across the app. However, it won't harm if they are provided at both `AppModule` and `FeatureModule`. The root injector will still be same and you will only have a singleton. However, if the Feature module is loded in the `Lazy` manner it will instantiate its own copy.

## Lazy Loading

> `Lazy Loading` is configured at the router.

> You can add canActivate to the lazy loaded routes but that of course means, that you might load code which in the end can't get accessed anyways. It would be better to check that BEFORE loading the code. You can enforce this behavior by adding the `canLoad` guard to the route which points to the lazily loaded module

```javascript
{
    path: 'recipes',
    loadChildren: './recipes/recipes.module#RecipesModule',
    canLoad: [AuthGuard]
}
```

In this example, the AuthGuard should implement the `CanLoad` interface.

> Don't provide Services in Shared Modules! Especially, when you plan to use them in lazy loaded modules.

## AOT

> The HTML templates are converted/compiled to JavaScript. This does not mean the templates will now have dynamic data rendered from the API calls but atleast the static part e.g. string interpolation etc. is performed and Agnular is now prepared to consume/process the dynamic data faster!

1.  Just-In-time (Default) - Happens on the Browser i.e. `Runtime`
2.  Ahead-Of-Time - `Compile Time`

### Benefits:

1.  Faster Startup
2.  Templates gets checked and errors are detected in advance
3.  Smaller File size  
    3a. Angular compiler is not shipped since its already compied(lot of code!)  
    3b. Angular strips out unneeded functionality e.g. if there is no usage of say `ngIf`, it will strip out the angular code and will reduce the size even further.

### Angular Commands

```javascript
// Inline Component
ng g c MyComp -is -it --spec false
// Declare the module
--module=app.module
```

### NgRX

> State is not persistent. You loose it when you refresh the page. If you want to save it, one can use `Local Storage`.

### Services

> Use `EventEmitter` in the service for cross component communication whenever its easier to avoid the chain of event and property bindings.

### Observable

![Observable](./images/observable.png 'Creating an observable from scratch')

> A `Subject` is an Observable and an Observer at the same time.

> A `Subject` is a better option for EventEmitter.

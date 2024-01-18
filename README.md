## How to add Bootstrap in Angular project?

In this repositories, you will find helpful content to build a web application using the latest version of Angular and bootstrap.Bootstrap CSS framework added to provides rich and responsive interface components.

### Prerequisites
Before you start, you need to install and configure the tools below to create the Angular application.

**Git**: It is a distributed version control system and we'll use it to sync the repository.

**Node.js** and npm: Node.js is a JavaScript code runtime software based on Google's V8 engine. npm is a package manager for Node.js (Node Package Manager). We'll use these tools to build and run the Angular application and install the libraries.

**Angular CLI**: Angular CLI is a command line utility tool for Angular and we'll use it to create the base structure of the Angular application.

**IDE** (like Visual Studio Code or WebStorm): an Integrated Development Environment is a tool with a graphical interface that helps you develop applications. We'll use one to develop our Angular application.

**Note**: From Angular v17 onwards, Standalone is now the new default for the CLI. However, it is still possible to create a module-based app by using the --no-standalone 
```
ng new demo --no-standalone
```

Angular is a development platform for building web, mobile, and desktop applications using HTML, CSS and TypeScript (JavaScript). Currently, Angular is at version 17 and Google is the main maintainer of the project.

Bootstrap is an open source CSS framework that has many components for building responsive web interfaces.

Let's create the application with the Angular base structure using the @angular/cli with the route file and the CSS style format.
```
ng new angular-bootstrap
```

Now you need to install the bootstrap and bootstrap-icons libraries that contain the files with Bootstrap's styles and JavaScript code like this:

```
npm install bootstrap bootstrap-icons
```

After install, we will configure the bootstrap and bootstrap-icons libraries. Change the `angular.json` file and add the `bootstrap.scss`, `bootstrap-icons.css` and `bootstrap.bundle.min.js` files as below:

```
"styles": [
  "node_modules/bootstrap/scss/bootstrap.scss",
  "node_modules/bootstrap-icons/font/bootstrap-icons.css",
  "src/styles.scss"
],
"scripts": [
  "node_modules/bootstrap/dist/js/bootstrap.bundle.min.js"
]
```

Now install the `@ng-bootstrap/ng-bootstrap` library which contains native Angular support:

```
npm install @ng-bootstrap/ng-bootstrap@next
```

After install, import the NgbModule module. Change the app.module.ts file and add the lines as below:

```typescript
import { NgbModule } from '@ng-bootstrap/ng-bootstrap';

imports: [
  BrowserModule,
  NgbModule,
  AppRoutingModule,
],
```

Now we will remove the contents of the AppComponent class from the src/app/app.component.ts file. Import the NgbModal service and create the open method to open a modal as below.

```typescript
import { Component } from '@angular/core';
import { NgbModal } from '@ng-bootstrap/ng-bootstrap';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.scss'],
})
export class AppComponent {

  constructor(private modalService: NgbModal) {
  }

  public open(modal: any): void {
    this.modalService.open(modal);
  }

}
```

Next remove the contents of the `src/app/app.component.html` file. Add some components in the HTML to view and test the components as below.

```html
<nav class="navbar navbar-expand-sm navbar-light bg-light">
  <div class="container">
    <a class="navbar-brand" href="#">
      <h1>Angular Bootstrap</h1>
    </a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li class="nav-item">
          <a class="nav-link active" aria-current="page" href="#">Home</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Link</a>
        </li>
        <li class="nav-item dropdown">
          <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-bs-toggle="dropdown" aria-expanded="false">
            Dropdown
          </a>
          <ul class="dropdown-menu" aria-labelledby="navbarDropdown">
            <li><a class="dropdown-item" href="#">Action</a></li>
            <li><a class="dropdown-item" href="#">Another action</a></li>
            <li><hr class="dropdown-divider"></li>
            <li><a class="dropdown-item" href="#">Something else here</a></li>
          </ul>
        </li>
        <li class="nav-item">
          <a class="nav-link disabled" href="#" tabindex="-1" aria-disabled="true">Disabled</a>
        </li>
      </ul>
      <form class="d-flex">
        <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
        <button class="btn btn-outline-success" type="submit">Search</button>
      </form>
    </div>
  </div>
</nav>
<div class="container py-3">
  <div class="row my-3">
    <div class="col-6">
      <label for="exampleFormControlInput1" class="form-label">Name</label>
      <input type="text" class="form-control form-control-sm" id="exampleFormControlInput1" placeholder="John Doe">
    </div>
    <div class="col-6">
      <label for="exampleFormControlInput2" class="form-label">Email address</label>
      <input type="email" class="form-control form-control-sm" id="exampleFormControlInput2" placeholder="name@example.com">
    </div>
  </div>
  <div class="row my-3">
    <div class="col">
      <label for="exampleFormControlTextarea1" class="form-label">Example textarea</label>
      <textarea class="form-control form-control-sm" id="exampleFormControlTextarea1" rows="3"></textarea>
    </div>
  </div>
  <div class="row my-3">
    <div class="col">
      <div class="form-check form-switch">
        <input class="form-check-input" type="checkbox" id="flexSwitchCheckDefault">
        <label class="form-check-label" for="flexSwitchCheckDefault">Default switch checkbox input</label>
      </div>
    </div>
  </div>
  <div class="row my-3">
    <div class="col">
      <button class="btn btn-sm btn-outline-primary" (click)="open(demoModal)">Launch demo modal</button>
    </div>
  </div>
</div>

<ng-template #demoModal let-modal>
  <div class="modal-header">
    <h4 class="modal-title" id="modal-basic-title">Profile update</h4>
    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close" (click)="modal.dismiss('Cross click')"></button>
  </div>
  <div class="modal-body">
    <form>
      <div class="form-group">
        <label for="state">State</label>
        <div class="input-group">
          <input id="state" name="state" class="form-control" placeholder="Enter your state" />
        </div>
      </div>
      <div class="form-group">
        <label for="country">Country</label>
        <div class="input-group">
          <input id="country" name="country" class="form-control" placeholder="Enter your country">
        </div>
      </div>
    </form>
  </div>
  <div class="modal-footer">
    <button type="button" class="btn btn-outline-dark" (click)="modal.close('Save click')">Save</button>
  </div>
</ng-template>
```
Finally, we will run the application with the command below:

```
npm start
```
Ready! You will access the URL at http://localhost:4200/ and check if the application is working.
---
title: Bind to host properties with host binding
author: kirjs
twitter: kirjs
level: intermediate
tags:
  - components
---
# Content
Every rendered angular component is wrapped in a host element (which is the same as component's selector).

It is possible to bind properties and attributes of host element using @HostBinding decorators, e.g. 

```typescript
import { Component, HostBinding } from '@angular/core';

@Component({
   selector: 'my-app', 
   template: `
    <div>Use the input below  to select host background-color:</div>
    <input type="color" [(ngModel)]="color"> 
  `,
  styles: [
    `:host { display: block; height: 100px; }`
  ]
})
export class AppComponent {
  @HostBinding('style.background') color = '#ff9900';
}
```

# file:app.component.ts
```typescript
  import { Component, HostBinding } from '@angular/core';

@Component({
   selector: 'my-app', 
   template: `
    <div>Use the input below  to select host background-color:</div>
    <input type="color" [(ngModel)]="color"> 
  `,
  styles: [
    `:host { display: block; height: 100px; }`
  ]
})
export class AppComponent {
  @HostBinding('style.background') color = '#ff9900';
}
```


# file:app.module.ts
```typescript
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { AppComponent } from './app.component';
import { FormsModule } from '@angular/forms';

@NgModule({
  imports: [BrowserModule, FormsModule],
  declarations: [AppComponent],
  bootstrap: [AppComponent]
})
export class AppModule {}
```

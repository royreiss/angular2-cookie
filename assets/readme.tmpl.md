# <%= pkg.name %>  [![Build Status](https://travis-ci.org/salemdar/angular2-cookie.svg?branch=<%= pkg.version %>)](https://travis-ci.org/salemdar/angular2-cookie) [![npm version](https://badge.fury.io/js/angular2-cookie.svg)](http://badge.fury.io/js/angular2-cookie) [![Downloads](http://img.shields.io/npm/dm/angular2-cookie.svg)](https://npmjs.org/package/angular2-cookie)

> <%= pkg.description %> **v<%= pkg.version %>**

_Please use >=1.2.4 for Angular >2.0.0, 1.1.x versions for beta, 1.2.2 version is for release candidates earlier than rc.5 and 1.2.3 is for >rc.5._

## Table of contents:
- [Get Started](#get-started)
  - [Installation](#installation)
  - [Usage](#usage)
  - [Examples](#examples)
    - [Angular2-quickstart](#quickstart)
    - [Angular2-seed](#seed)
    - [Angular-cli](#cli)
    - [Angular2 Webpack Starter](#angular2-webpack-starter)
- [CookieService](#cookieservice)
  - [get()](#get)
  - [getObject()](#getobject)
  - [getAll()](#getall)
  - [put()](#put)
  - [putObject()](#putobject)
  - [remove()](#remove)
  - [removeAll()](#removeall)
- [Options](#options)

## <a name="get-started"></a> Get Started

### <a name="installation"></a> Installation

You can install this package locally with npm.

```bash
# To get the latest stable version and update package.json file:
npm install angular2-cookie --save
```

After installing the library, it should be included in the SystemJS configurations.

```javascript
/**
 * System configuration for Angular 2 samples
 * Adjust as necessary for your application needs.
 * Taken from: https://github.com/angular/quickstart/blob/master/systemjs.config.js
 */
(function (global) {
  System.config({
    paths: {
      // paths serve as alias
      'npm:': 'node_modules/'
    },
    // map tells the System loader where to look for things
    map: {
      // our app is within the app folder
      app: 'app',

      // angular bundles
      '@angular/core': 'npm:@angular/core/bundles/core.umd.js',
      '@angular/common': 'npm:@angular/common/bundles/common.umd.js',
      '@angular/compiler': 'npm:@angular/compiler/bundles/compiler.umd.js',
      '@angular/platform-browser': 'npm:@angular/platform-browser/bundles/platform-browser.umd.js',
      '@angular/platform-browser-dynamic': 'npm:@angular/platform-browser-dynamic/bundles/platform-browser-dynamic.umd.js',
      '@angular/http': 'npm:@angular/http/bundles/http.umd.js',
      '@angular/router': 'npm:@angular/router/bundles/router.umd.js',
      '@angular/forms': 'npm:@angular/forms/bundles/forms.umd.js',

      // other libraries
      'rxjs':                       'npm:rxjs',
      'angular2-in-memory-web-api': 'npm:angular2-in-memory-web-api',
      'angular2-cookie':            'npm:angular2-cookie'
    },
    // packages tells the System loader how to load when no filename and/or no extension
    packages: {
      app: {
        main: './main.js',
        defaultExtension: 'js'
      },
      rxjs: {
        defaultExtension: 'js'
      },
      'angular2-in-memory-web-api': {
        main: './index.js',
        defaultExtension: 'js'
      },
      'angular2-cookie': {
        main: './core.js',
        defaultExtension: 'js'
      }
    }
  });
})(this);
```

### <a name="usage"></a> Usage

**CookieService** class is an injectable service with angular `@Injectable()` decorator. Therefore, it needs to be registered in the providers array (encouraged way).
Then, it will be available in the constructor of the component class.

```typescript
import { NgModule }      from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';

import { CookieService } from 'angular2-cookie/services/cookies.service';

import { AppComponent }  from './app.component';

@NgModule({
  imports: [ BrowserModule ],
  declarations: [ AppComponent ],
  providers: [ CookieService ],
  bootstrap: [ AppComponent ]
})
export class AppModule { }
```

```typescript
import {Component} from 'angular2/core';
import {CookieService} from 'angular2-cookie/core';

@Component({
    selector: 'my-very-cool-app',
    template: '<h1>My Angular2 App with Cookies</h1>'
})

export class AppComponent { 
  constructor(private _cookieService:CookieService){}
  
  getCookie(key: string){
    return this._cookieService.get(key);
  }
}
```

### <a name="examples"></a> Examples

Here you can find some usage examples with popular boilerplate libraries.

#### <a name="quickstart"></a> Angular2-quickstart

A boilerplate provided by Angular team.
_(Link: [https://github.com/angular/quickstart](https://github.com/angular/quickstart))_

Just edit the `systemjs.config.js` file and add the `angular2-cookie` there.

```typescript
/**
 * System configuration for Angular 2 samples
 * Adjust as necessary for your application needs.
 */
(function (global) {
  System.config({
    paths: {
      // paths serve as alias
      'npm:': 'node_modules/'
    },
    // map tells the System loader where to look for things
    map: {
      // our app is within the app folder
      app: 'app',

      // angular bundles
      '@angular/core': 'npm:@angular/core/bundles/core.umd.js',
      '@angular/common': 'npm:@angular/common/bundles/common.umd.js',
      '@angular/compiler': 'npm:@angular/compiler/bundles/compiler.umd.js',
      '@angular/platform-browser': 'npm:@angular/platform-browser/bundles/platform-browser.umd.js',
      '@angular/platform-browser-dynamic': 'npm:@angular/platform-browser-dynamic/bundles/platform-browser-dynamic.umd.js',
      '@angular/http': 'npm:@angular/http/bundles/http.umd.js',
      '@angular/router': 'npm:@angular/router/bundles/router.umd.js',
      '@angular/forms': 'npm:@angular/forms/bundles/forms.umd.js',

      // other libraries
      'rxjs':                       'npm:rxjs',
      'angular2-in-memory-web-api': 'npm:angular2-in-memory-web-api',
      'angular2-cookie':            'npm:angular2-cookie'
    },
    // packages tells the System loader how to load when no filename and/or no extension
    packages: {
      app: {
        main: './main.js',
        defaultExtension: 'js'
      },
      rxjs: {
        defaultExtension: 'js'
      },
      'angular2-in-memory-web-api': {
        main: './index.js',
        defaultExtension: 'js'
      },
      'angular2-cookie': {
        main: './core.js',
        defaultExtension: 'js'
      }
    }
  });
})(this);
```

#### <a name="seed"></a> Angular2-seed

A popular seed project.
_(Link: [https://github.com/mgechev/angular2-seed](https://github.com/mgechev/angular2-seed))_

Add the following settings to the (constructor of) `ProjectConfig` class (path: `./tools/config/project.config.ts`).

```typescript
/* Add to or override NPM module configurations: */
//this.mergeObject( this.PLUGIN_CONFIGS['browser-sync'], { ghostMode: false } );
this.mergeObject(this.SYSTEM_CONFIG_DEV['paths'], {'angular2-cookie': 'node_modules/angular2-cookie/bundles/angular2-cookie.js'});
this.mergeObject(this.SYSTEM_BUILDER_CONFIG['packages'], {
  'angular2-cookie': {
    main: 'core.js',
    defaultExtension: 'js'
  }
});
```

Do not forget to inject the service in the module (`providers` array).

#### <a name="cli"></a> Angular-cli

A CLI tool for Angular2.
_(Link: [https://github.com/angular/angular-cli](https://github.com/angular/angular-cli))_

Edit the `vendorNpmFiles` array (path: `./angular-cli-build.js`).

```javascript
// Angular-CLI build configuration
// This file lists all the node_modules files that will be used in a build
// Also see https://github.com/angular/angular-cli/wiki/3rd-party-libs

/* global require, module */

var Angular2App = require('angular-cli/lib/broccoli/angular2-app');

module.exports = function(defaults) {
  return new Angular2App(defaults, {
    vendorNpmFiles: [
      'systemjs/dist/system-polyfills.js',
      'systemjs/dist/system.src.js',
      'zone.js/dist/**/*.+(js|js.map)',
      'es6-shim/es6-shim.js',
      'reflect-metadata/**/*.+(ts|js|js.map)',
      'rxjs/**/*.+(js|js.map)',
      '@angular/**/*.+(js|js.map)',
      'angular2-cookie/**/*.+(js|js.map)'
    ]
  });
};
```

Also add `angular2-cookie` to the `map` and `packages` object in the `system-config.ts` (path: `./src/system-config.ts`)

```typescript
/***********************************************************************************************
 * User Configuration.
 **********************************************************************************************/
/** Map relative paths to URLs. */
const map: any = {
  'angular2-cookie': 'vendor/angular2-cookie'
};

/** User packages configuration. */
const packages: any = {
  'angular2-cookie': {main: 'core.js', defaultExtension: 'js'},
};
```

#### <a name="cli"></a> Angular2 Webpack Starter

An Angular 2 Starter kit featuring Angular 2 and Webpack 2 by @AngularClass
_(Link: [https://github.com/AngularClass/angular2-webpack-starter](https://github.com/AngularClass/angular2-webpack-starter))_

Add angular2-cookie to `vendor.browser.ts` (path: `./src/vendor.browser.ts`)

```typescript
// Angular 2
import '@angular/platform-browser';
import '@angular/platform-browser-dynamic';
import '@angular/core';
import '@angular/common';
import '@angular/forms';
import '@angular/http';
import '@angular/router';

// angular2 cookie
import 'angular2-cookie/core'

// AngularClass
import '@angularclass/hmr';

// RxJS
import 'rxjs/add/operator/map';
import 'rxjs/add/operator/mergeMap';

if ('production' === ENV) {
  // Production


} else {
  // Development

}

```

Add `CookieService` to the `APP_PROVIDERS` array in the `app.module.ts` file (path: `./src/app/app.module.ts`):

```typescript
// ...

// Application wide providers
const APP_PROVIDERS = [
  ...APP_RESOLVER_PROVIDERS,
  AppState,
  CookieService
];

// ...
```


## <a name="cookieservice"></a> CookieService

There are 7 methods available in the `CookieService` (6 standard methods from **Angular 1** and 1 extra `removeAll()` method for convenience)

### <a name="get"></a> get()
Returns the value of given cookie key.

```typescript
/**
 * @param {string} key Id to use for lookup.
 * @returns {string} Raw cookie value.
 */
get(key: string): string;
```

### <a name="getobject"></a> getObject()
Returns the deserialized value of given cookie key.

```typescript
/**
 * @param {string} key Id to use for lookup.
 * @returns {Object} Deserialized cookie value.
 */
getObject(key: string): Object;
```

### <a name="getall"></a> getAll()
Returns a key value object with all the cookies.

```typescript
/**
 * @returns {Object} All cookies
 */
getAll(): any;
```

### <a name="put"></a> put()
Sets a value for given cookie key.

```typescript
/**
 * @param {string} key Id for the `value`.
 * @param {string} value Raw value to be stored.
 * @param {CookieOptionsArgs} options (Optional) Options object.
 */
put(key: string, value: string, options?: CookieOptionsArgs): void;
```

### <a name="putobject"></a> putObject()
Serializes and sets a value for given cookie key.

```typescript
/**
 * @param {string} key Id for the `value`.
 * @param {Object} value Value to be stored.
 * @param {CookieOptionsArgs} options (Optional) Options object.
 */
putObject(key: string, value: Object, options?: CookieOptionsArgs): void;
```

### <a name="remove"></a> remove()
Remove given cookie.

```typescript
/**
 * @param {string} key Id of the key-value pair to delete.
 * @param {CookieOptionsArgs} options (Optional) Options object.
 */
remove(key: string, options?: CookieOptionsArgs): void;
```

### <a name="removeall"></a> removeAll()
Remove all cookies.

```typescript
/**
 */
removeAll(): void;
```

## <a name="options"></a> Options

Options object should be a type of `CookieOptionsArgs` interface. The object may have following properties:

- **path** - {string} - The cookie will be available only for this path and its sub-paths. By default, this is the URL that appears in your `<base>` tag.
- **domain** - {string} - The cookie will be available only for this domain and its sub-domains. For security reasons the user agent will not accept the cookie if the current domain is not a sub-domain of this domain or equal to it.
- **expires** - {string|Date} - String of the form "Wdy, DD Mon YYYY HH:MM:SS GMT" or a Date object indicating the exact date/time this cookie will expire.
- **secure** - {boolean} - If `true`, then the cookie will only be available through a secured connection.


### <a name="notes"></a> _Note_

_The build process and the file structure of this repository has respectively modeled after the awesome [angular2-google-maps](https://github.com/SebastianM/angular2-google-maps) project of [Sebastian Müller](http://twitter.com/Sebamueller)._
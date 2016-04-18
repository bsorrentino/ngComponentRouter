
# ngComponentRouter
Angular 2 Component Router for Angular 1

This is an extract directly built from Angular 2 source code. Adding this as an npm package, because Angular hasn't released an official version yet. 

## Based on Angular 2 Commit
930f58718b3d3cdc335a82dcd67d8eb2f1a16bdf

## Procedure of Extraction
As discussed on https://github.com/angular/angular.js/issues/12926.

- Install gulp globally `npm install -g gulp@latest`
- Clone the angular 2 repo: `git clone git@github.com:angular/angular.git angular2`
- Go into the angular2 directory and install the dependencies `cd angular2` and `npm install`
- After npm finishes, run the gulp command to build the router file `gulp buildRouter.dev`
- The angular_1_router.js file will be in your angular2/dist folder.

## Changes applied
- Added catch in method ```Router.prototype.commit``` on deactivation. This fixes an issue when there is an ucaught exeception on router activation (```$routerOnActivate```) that disable the navigation
```javascript
2940 next =
2941       this.deactivate(instruction)
2942            .then(function (_) { return _this._outlet.activate(componentInstruction); })
2943            .catch( function(e) { // this catch fix the issue
2944                console.error( "Router Deactivate");
2945            });
```

## Alternatives
This package is out there solely for convenience. You may directly import the router from Angular's npm package. 
Read more about on https://github.com/angular/angular.js/issues/12926.

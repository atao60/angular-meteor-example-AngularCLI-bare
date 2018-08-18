Cf. 
* [[1.7.1-beta.25] Error: Cannot find module '@babel/runtime/helpers/builtin/interopRequireDefault #10126](https://github.com/meteor/meteor/issues/10126)
    
* [[1.7.0.3] Error: Cannot find module '@babel/runtime/helpers/builtin/interopRequireDefault' #10128](https://github.com/meteor/meteor/issues/10128)

* [examples/AngularCLI `npm run api` crashes with `Error: Cannot find module '@babel/runtime/helpers/builtin/interopRequireDefault'` #1946](https://github.com/Urigo/angular-meteor/issues/1946)

* [[examples/AngularCLI]: "cannot find" messages as building the api server but it runs fine #1948](https://github.com/Urigo/angular-meteor/issues/1948)


```bash

node -v
# v8.11.3

npm list -g --depth=0
# /usr/local/lib
# ├── @angular-devkit/core@0.6.8
# ├── @angular/cli@6.0.8
# ├── @ng-toolkit/init@1.1.31
# ├── ajv-cli@3.0.0
# ├── cordova@8.0.0
# ├── express-generator@4.16.0
# ├── http-server@0.11.1
# ├── ionic@3.20.0
# ├── json@9.0.6
# ├── meteor-client-bundler@0.5.7
# ├── meteor-now@0.6.1
# ├── now@11.1.7
# ├── npm@5.6.0
# └── npm-check-updates@2.14.2
#
# [...]

ncu -v
# 2.14.2

ng new demo7 --routing --style scss
# CREATE demo7/README.md (1022 bytes)
# CREATE demo7/angular.json (3630 bytes)
# CREATE demo7/package.json (1309 bytes)
# CREATE demo7/tsconfig.json (384 bytes)
# CREATE demo7/tslint.json (2805 bytes)
# CREATE demo7/.editorconfig (245 bytes)
# CREATE demo7/.gitignore (503 bytes)
# CREATE demo7/src/environments/environment.prod.ts (51 bytes)
# CREATE demo7/src/environments/environment.ts (631 bytes)
# CREATE demo7/src/favicon.ico (5430 bytes)
# CREATE demo7/src/index.html (292 bytes)
# CREATE demo7/src/main.ts (370 bytes)
# CREATE demo7/src/polyfills.ts (3194 bytes)
# CREATE demo7/src/test.ts (642 bytes)
# CREATE demo7/src/assets/.gitkeep (0 bytes)
# CREATE demo7/src/styles.scss (80 bytes)
# CREATE demo7/src/browserslist (375 bytes)
# CREATE demo7/src/karma.conf.js (964 bytes)
# CREATE demo7/src/tsconfig.app.json (194 bytes)
# CREATE demo7/src/tsconfig.spec.json (282 bytes)
# CREATE demo7/src/tslint.json (314 bytes)
# CREATE demo7/src/app/app-routing.module.ts (245 bytes)
# CREATE demo7/src/app/app.module.ts (393 bytes)
# CREATE demo7/src/app/app.component.scss (0 bytes)
# CREATE demo7/src/app/app.component.html (1173 bytes)
# CREATE demo7/src/app/app.component.spec.ts (1105 bytes)
# CREATE demo7/src/app/app.component.ts (208 bytes)
# CREATE demo7/e2e/protractor.conf.js (752 bytes)
# CREATE demo7/e2e/src/app.e2e-spec.ts (301 bytes)
# CREATE demo7/e2e/src/app.po.ts (208 bytes)
# CREATE demo7/e2e/tsconfig.e2e.json (213 bytes)
# npm WARN deprecated istanbul-lib-hook@1.2.1: 1.2.0 should have been a major version bump
#
# > node-sass@4.9.3 install [...]/demo7/node_modules/node-sass
# > node scripts/install.js
#
# Cached binary found at [...]/.npm/node-sass/4.9.3/linux-x64-57_binding.node
#
# > node-sass@4.9.3 postinstall [...]/demo7/node_modules/node-sass
# > node scripts/build.js
#
# Binary found at [...]/demo7/node_modules/node-sass/vendor/linux-x64-57/binding.node
# Testing binary
# Binary is fine
#
# > @angular/cli@6.0.8 postinstall [...]/demo7/node_modules/@angular/cli
# > node ./bin/ng-update-message.js

cd demo7

code .  # Open the project under VSC

npm i -S meteor-node-stubs meteor-rxjs
# npm WARN meteor-rxjs@0.4.14 requires a peer of @types/meteor@^1.4.6 but none is installed. You must install peer dependencies yourself.
# npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.4 (node_modules/fsevents):
# npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.4: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})
#
# + meteor-node-stubs@0.4.1
# + meteor-rxjs@0.4.14
# added 74 packages in 11.46s

##### Force the version of @babel/runtime 
##### to be used with Meteor <= 1.7.0.4
npm i --save-exact @babel/runtime@7.0.0-beta.55
# npm WARN meteor-rxjs@0.4.14 requires a peer of @types/meteor@^1.4.6 but none is installed. You must install peer dependencies yourself.
# npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.4 (node_modules/fsevents):
# npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.4: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})
#
# + @babel/runtime@7.0.0-beta.55
# added 2 packages in 9.644s

npm i -D meteor-client-bundler @types/meteor
# npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.4 (node_modules/fsevents):
# npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.4: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})
#
# + @types/meteor@1.4.16
# + meteor-client-bundler@0.5.9
# added 17 packages in 12.574s

##### Force a minimal version for core-js:
npm i -S core-js@^2.5.7 # >= 2.5.7 && < 3.0.0
# npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.4 (node_modules/fsevents):
# npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.4: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})
#
# + core-js@2.5.7
# updated 1 package in 9.935s

##### Prevent from upgrading typescrypt to version 3:
npm i -S typescript@^2.9.2 # >= 2.9.2 && < 3.0.0
# npm WARN @ngtools/webpack@6.0.8 requires a peer of typescript@~2.4.0 || ~2.5.0 || ~2.6.0 || ~2.7.0 but none is installed. You must install peer dependencies yourself.
# npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.4 (node_modules/fsevents):
# npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.4: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})
#
# + typescript@2.9.2
# added 1 package and updated 1 package in 10.198s

ncu
# Using [...]/demo7/package.json
# [..................] - :
#  @babel/runtime                 7.0.0-beta.55  →  7.0.0-rc.1 
#  @angular-devkit/build-angular         ~0.6.8  →      ~0.7.4 
#  @angular/cli                          ~6.0.8  →      ~6.1.4 
#  @types/node                           ~8.9.4  →     ~10.7.1 
#  codelyzer                             ~4.2.1  →      ~4.4.4 
#  jasmine-core                         ~2.99.1  →      ~3.2.1 
#  karma                                 ~1.7.1  →      ~3.0.0 
#  karma-jasmine-html-reporter           ^0.2.2  →      ^1.3.0 
#  protractor                            ~5.3.0  →      ~5.4.0 
#  ts-node                               ~5.0.1  →      ~7.0.1 
#  tslint                                ~5.9.1  →     ~5.11.0 
#  typescript                            ^2.9.2  →      ^3.0.1 
#
# Run ncu with -u to upgrade package.json

ncu -a --reject @babel/runtime,typescript
# Using [...]/demo7/package.json
# [..................] \ :
#  @angular-devkit/build-angular   ~0.6.8  →   ~0.7.4 
#  @angular/cli                    ~6.0.8  →   ~6.1.4 
#  @types/node                     ~8.9.4  →  ~10.7.1 
#  codelyzer                       ~4.2.1  →   ~4.4.4 
#  jasmine-core                   ~2.99.1  →   ~3.2.1 
#  karma                           ~1.7.1  →   ~3.0.0 
#  karma-jasmine-html-reporter     ^0.2.2  →   ^1.3.0 
#  protractor                      ~5.3.0  →   ~5.4.0 
#  ts-node                         ~5.0.1  →   ~7.0.1 
#  tslint                          ~5.9.1  →  ~5.11.0 
# Upgraded [...]/demo7/package.json

npm update

##### belt and suspenders...
npm install
# [...]

##### !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
##### !!! using '--bare' template, not the default one !!!
##### !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
meteor create --bare api
# Created a new Meteor app in 'api'.           
#
# To run your new app:                          
#   cd api                                     
#   meteor                                      
#                                              
# If you are new to Meteor, try some of the learning resources here:
#   https://www.meteor.com/tutorials  

cat api/.meteor/release
# METEOR@1.7.0.4

cat api/.meteor/packages
# # Meteor packages used by this project, one per line.
# # Check this file (and the other files in this directory) into your repository.
# #
# # 'meteor add' and 'meteor remove' will edit this file for you,
# # but you can also edit it by hand.
#
# meteor-base@1.4.0             # Packages every Meteor app needs to have
# mobile-experience@1.0.5       # Packages for a great mobile UX
# mongo@1.5.0                   # The database Meteor supports right now
# static-html             # Define static page content in .html files
# reactive-var@1.0.11            # Reactive variable for tracker
# tracker@1.2.0                 # Meteor's client-side reactive programming library
#
# standard-minifier-css@1.4.1   # CSS minifier run for production mode
# standard-minifier-js@2.3.4    # JS minifier run for production mode
# es5-shim@4.8.0                # ECMAScript 5 compatibility for older browsers
# ecmascript@0.11.1              # Enable ECMAScript2015+ syntax in app code
# shell-server@0.3.1            # Server-side component of the `meteor shell` command

##### The package 'meteor-client-bundler' is expecting a Meteor project created
##### with default template. It won't remove 'static-html' package provided with 'bare' template. Such a package has to be removed explicitely:
(cd api && meteor remove static-html)
#                                              
# Changes to your project's package version selections:
#                                              
# blaze-tools            removed from your project
# caching-compiler       removed from your project
# caching-html-compiler  removed from your project
# deps                   removed from your project
# html-tools             removed from your project
# htmljs                 removed from your project
# spacebars-compiler     removed from your project
# static-html            removed from your project
# templating-tools       removed from your project
#
# static-html: removed dependency       

(cd api && meteor add barbatus:typescript)
#                                              
# Changes to your project's package version selections:
#                                              
# barbatus:typescript           added, version 0.7.0
# barbatus:typescript-compiler  added, version 0.10.0
# barbatus:typescript-runtime   added, version 1.1.0
#
#                                              
# barbatus:typescript: TypeScript for Meteor    

rm -rf api/node_modules api/package.json api/package-lock.json\
&& ln -s ../package.json api/package.json \
&& ln -s ../package-lock.json api/package-lock.json \
&& ln -s ../tsconfig.json api/tsconfig.json \
&& ln -s ../node_modules api/

mkdir -pv api/private/ api/server/{fixtures,methods,model}
# mkdir: création du répertoire 'api/private/'
# mkdir: création du répertoire 'api/server'
# mkdir: création du répertoire 'api/server/fixtures'
# mkdir: création du répertoire 'api/server/methods'
# mkdir: création du répertoire 'api/server/model'

##### Cf. https://github.com/Urigo/angular-meteor/issues/1948
#####     Not relevant here.
cat << ___EOF > api/server/fixtures/data.fixture.ts
import fs from 'fs';
const p = Assets.absoluteFilePath('dummy.txt');
console.log("Assets.absoluteFilePath('dummy.txt'): ", p);
const content = fs.readFileSync(p, 'UTF8');
console.log("private/dummy.txt content: ", content)
___EOF

cat << ___EOF > api/private/dummy.txt
Some dummy content.
___EOF

cat << ___EOF > api/server/main.ts
import { Meteor } from 'meteor/meteor';

Meteor.startup(() => {
  // code to run on server at startup
});
___EOF

cat << ___EOF > api/server/method.ts
import { Meteor } from 'meteor/meteor';
import { check } from 'meteor/check';
import { Todos } from './collections';

Meteor.methods({
  addTodo(content: string) {
    check(content, String);
    return Todos.insert({
      content
    });
  }
});
___EOF


cat << ___EOF > api/server/models.ts
export interface Todo {
  content: string;
}
___EOF


cat << ___EOF > api/server/publications.ts
import { Meteor } from 'meteor/meteor';
import { Todos } from './collections';

Meteor.publish('todos', function () {
  return Todos.find();
});
___EOF


cat << ___EOF > api/server/collections.ts
import { Todo } from './models';
import { MongoObservable } from 'meteor-rxjs';

export const Todos = new MongoObservable.Collection<Todo>('todos');
___EOF


cat << ___EOF > meteor-client.config.json
{
  "runtime": {
    "DDP_DEFAULT_CONNECTION_URL": "http://localhost:3000",
    "ROOT_URL": "http://localhost:3000"
  },
  "generateNodeModules": true
}
___EOF

PROJECT_NAME="$(cat angular.json | json "defaultProject")"

APP_DIST_FOLDER="$(cat angular.json | json "projects['$PROJECT_NAME'].architect.build.options.outputPath")"


json -I -f angular.json -e "this.projects['$PROJECT_NAME'].architect.build.options.scripts.push('node_modules/meteor-client.js')"
# json: updated "angular.json" in-place

##### Don't limit acces to types during client server build
json -I -f src/tsconfig.app.json -e "delete this.compilerOptions.types"
# json: updated "src/tsconfig.app.json" in-place

json -I -f tsconfig.json -e "this.compilerOptions.esModuleInterop=true" \
&& json -I -f tsconfig.json -e "this.compilerOptions.module='commonjs'"
# json: updated "tsconfig.json" in-place
# json: updated "tsconfig.json" in-place

##### To avoid alert about typescript casting in libraries (eg meteor-rxjs):
json -I -f tsconfig.json -e "this.compilerOptions.skipLibCheck=true"
# json: updated "tsconfig.json" in-place

##### Replace src/app/app.component.ts and src/app/app.component.html

cat << ___EOF > src/app/app.component.ts
import { Component, OnInit } from '@angular/core';
import { Todos } from 'api/server/collections';
import { Todo } from 'api/server/models';
import { Observable } from 'rxjs';
import { switchMap } from 'rxjs/operators';
import { MeteorObservable } from 'meteor-rxjs';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.scss']
})
export class AppComponent implements OnInit {
  title = 'AngularCLI Meteor Boilerplate';
  todos: Observable<Todo[]>;
  todoContent: string;
  ngOnInit() {
    this.todos = MeteorObservable.subscribe('todos')
      .pipe(switchMap(() => Todos.find()));
  }
  addTodo(\$event: MouseEvent) {
    \$event.preventDefault();
    MeteorObservable.call('addTodo', this.todoContent).subscribe(
      res => console.log(res),
      err => console.error(err)
    );
  }
}
___EOF


cat << ___EOF > src/app/app.component.html
<!--The content below is only a placeholder and can be replaced.-->
<div style="text-align:center">
  <h1>
    Welcome to {{ title }}!
  </h1>
  <img width="50" alt="Angular Logo" src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNTAgMjUwIj4KICAgIDxwYXRoIGZpbGw9IiNERDAwMzEiIGQ9Ik0xMjUgMzBMMzEuOSA2My4ybDE0LjIgMTIzLjFMMTI1IDIzMGw3OC45LTQzLjcgMTQuMi0xMjMuMXoiIC8+CiAgICA8cGF0aCBmaWxsPSIjQzMwMDJGIiBkPSJNMTI1IDMwdjIyLjItLjFWMjMwbDc4LjktNDMuNyAxNC4yLTEyMy4xTDEyNSAzMHoiIC8+CiAgICA8cGF0aCAgZmlsbD0iI0ZGRkZGRiIgZD0iTTEyNSA1Mi4xTDY2LjggMTgyLjZoMjEuN2wxMS43LTI5LjJoNDkuNGwxMS43IDI5LjJIMTgzTDEyNSA1Mi4xem0xNyA4My4zaC0zNGwxNy00MC45IDE3IDQwLjl6IiAvPgogIDwvc3ZnPg==">
</div>
<h2>Todo List </h2>
<fieldset>
  <legend>Add Todo</legend>
  <form>
    <p>
      <input name="todoContent" [(ngModel)]="todoContent" placeholder="Content">
    </p>
    <p>
      <button (click)="addTodo(\$event)">Add</button>
    </p>
  </form>
</fieldset>
<ul>
  <li *ngFor="let todo of todos | async">
    {{todo.content}}
  </li>
</ul>
___EOF


##### Update src/app/app.module.ts

sed -i '/^\s*import\s*{\s*NgModule\s*}/ i\
import { FormsModule } from '"'"'@angular/forms'"'"';
' src/app/app.module.ts

sed -i '/^\s*BrowserModule/ a\
    FormsModule,
' src/app/app.module.ts

##### Add scripts to launch the app at once:

npm i -D rimraf mkdirp npm-run-all wait-on path-exists-cli
# npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.4 (node_modules/fsevents):
# npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.4: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})
#
# + rimraf@2.6.2
# + npm-run-all@4.1.3
# + mkdirp@0.5.1
# + path-exists-cli@1.0.0
# + wait-on@2.1.0
# added 31 packages and updated 2 packages in 17.519s

json -I -f package.json -e "this.scripts['start:local:dev']='run-p start:local:api start:local:client:dev'"
# json: updated "package.json" in-place

##### Meteor api server can't be running during building meteor-client
json -I -f package.json -e "this.scripts['start:local:api']='wait-on -d 500 node_modules/meteor-client.js && cd api && meteor run'"
# json: updated "package.json" in-place

##### Don't start ui server until meteor-client.js is available
json -I -f package.json -e "this.scripts['start:local:client:dev']='wait-on node_modules/meteor-client.js && ng serve'"
# json: updated "package.json" in-place

##### Rebuild meteor-client if necessary
json -I -f package.json -e "this.scripts['prestart:local:client:dev']='path-exists node_modules/meteor-client.js || npm run build:meteor-client'"
# json: updated "package.json" in-place

json -I -f package.json -e "this.scripts['build:meteor-client']='meteor-client bundle -s api'"
# json: updated "package.json" in-place

json -I -f package.json -e "this.scripts['reset:api']='cd api && meteor reset'"
# json: updated "package.json" in-place

json -I -f package.json -e "this.scripts['reset:api:db']='rimraf api/.meteor/local/db'"
# json: updated "package.json" in-place

json -I -f package.json -e "this.scripts['clean']='npm run clean:dist'" \
&& json -I -f package.json -e "this.scripts['clean:build']='run-p clean:meteor-client clean:dist'" \
&& json -I -f package.json -e "this.scripts['clean:meteor-client']='rimraf node_modules/meteor-client.js'" \
&& json -I -f package.json -e "this.scripts['clean:dist']='rimraf $APP_DIST_FOLDER'" 
# json: updated "package.json" in-place
# json: updated "package.json" in-place
# json: updated "package.json" in-place
# json: updated "package.json" in-place

npm run start:local:dev
#
# > demo7@0.0.0 start:local:dev [...]/demo7
# > run-p start:local:api start:local:client:dev
#
#
# > demo7@0.0.0 start:local:api [...]/demo7
# > wait-on -d 500 node_modules/meteor-client.js && cd api && meteor run
#
#
# > demo7@0.0.0 prestart:local:client:dev [...]/demo7
# > path-exists node_modules/meteor-client.js || npm run build:meteor-client
#
#
# > demo7@0.0.0 build:meteor-client [...]/demo7
# > meteor-client bundle -s api
#
# Created a new Meteor app in '/tmp/tmp-21340yA18qr7WlVI0'.
#
# To run your new app:                          
#   cd /tmp/tmp-21340yA18qr7WlVI0               
#   meteor                                      
#                                              
# If you are new to Meteor, try some of the learning resources here:
#   https://www.meteor.com/tutorials            
#                                              
# To start with a different app template, try one of the following:
#
#   meteor create --bare    # to create an empty app
#   meteor create --minimal # to create an app with as few Meteor packages as possible
#   meteor create --full    # to create a more complete scaffolded app
#                                              
# audited 602 packages in 1.911s
# found 0 vulnerabilities
#
#                                              
# Changes to your project's package version selections:
#                                              
# autopublish                   removed from your project
# barbatus:typescript           added, version 0.7.0
# barbatus:typescript-compiler  added, version 0.10.0
# barbatus:typescript-runtime   added, version 1.1.0
# blaze                         removed from your project
# blaze-html-templates          removed from your project
# blaze-tools                   removed from your project
# caching-compiler              removed from your project
# caching-html-compiler         removed from your project
# deps                          removed from your project
# html-tools                    removed from your project
# htmljs                        removed from your project
# insecure                      removed from your project
# jquery                        removed from your project
# observe-sequence              removed from your project
# spacebars                     removed from your project
# spacebars-compiler            removed from your project
# templating                    removed from your project
# templating-compiler           removed from your project
# templating-runtime            removed from your project
# templating-tools              removed from your project
# ui                            removed from your project
#
#                                              
# WARNING: The output directory is under your source tree.
#          Your generated files may get interpreted as source code!
#          Consider building into a different directory instead
#          meteor build ../output
#                                              
#                                              
# > demo7@0.0.0 start:local:client:dev [...]/demo7
# > wait-on node_modules/meteor-client.js && ng serve
#
# [[[[[ ~/Développements/pwa/cornflourblue-ng6-bs4-login/demo7/api ]]]]]
#
# => Started proxy.                             
# ** Angular Live Development Server is listening on localhost:4200, open your browser on http://localhost:4200/ **
# => Started MongoDB.ids NamedModulesPlugin                                          #                                                  
#  92% after chunk asset optimization SourceMapDevToolPlugin polyfills.js generate SourceMap                                              Building the application      #            |                                                                       #                
# Date: 2018-08-18T08:03:01.412Z
# Hash: 00019e11478c8c591881
# Time: 26166ms
# chunk {main} main.js, main.js.map (main) 14.9 kB [initial] [rendered]
# chunk {polyfills} polyfills.js, polyfills.js.map (polyfills) 227 kB [initial] [rendered]
# chunk {runtime} runtime.js, runtime.js.map (runtime) 5.22 kB [entry] [rendered]
# chunk {scripts} scripts.js, scripts.js.map (scripts) 1.08 MB  [rendered]
# chunk {styles} styles.js, styles.js.map (styles) 16 kB [initial] [rendered]
# chunk {vendor} vendor.js, vendor.js.map (vendor) 3.78 MB [initial] [rendered]
# ℹ ｢wdm｣: Compiled successfully.              |
# server/fixtures/data.fixture.ts (1, 16): Cannot find module 'fs'.
# server/fixtures/data.fixture.ts (2, 11): Cannot find name 'Assets'.
# I20180818-10:04:02.794(2)? Assets.absoluteFilePath('dummy.txt'):  [...]/demo7/api/.meteor/local/build/programs/server/assets/app/dummy.txt
# I20180818-10:04:03.162(2)? private/dummy.txt content:  Some dummy content.
# I20180818-10:04:03.162(2)? 
# => Started your app.
#
# => App running at: http://localhost:3000/

##### Go to http://localhost:4200
##### OK, the application behaves as expected
^C

git add --all
git commit -m "Working application"

##### Restore the package 'static-html':

(cd api && meteor add static-html)
#                                              
# Changes to your project's package version selections:
#                                              
# blaze-tools            added, version 1.0.10  
# caching-compiler       added, version 1.1.12
# caching-html-compiler  added, version 1.1.3
# deps                   added, version 1.0.12
# html-tools             added, version 1.0.11
# htmljs                 added, version 1.0.11
# spacebars-compiler     added, version 1.1.3
# static-html            added, version 1.2.2
# templating-tools       added, version 1.1.2
#
#                                              
# static-html: Define static page content in .html files

npm run clean:build
#
# > demo7@0.0.0 clean:build [...]/demo7
# > run-p clean:meteor-client clean:dist
#
#
# > demo7@0.0.0 clean:meteor-client [...]/demo7
# > rimraf node_modules/meteor-client.js
#
#
# > demo7@0.0.0 clean:dist [...]/demo7
# > rimraf dist/demo7

npm run start:local:dev
#
# > demo7@0.0.0 start:local:dev [...]/demo7
# > run-p start:local:api start:local:client:dev
#
#
# > demo7@0.0.0 prestart:local:client:dev [...]/demo7
# > path-exists node_modules/meteor-client.js || npm run build:meteor-client
#
#
# > demo7@0.0.0 start:local:api [...]/demo7
# > wait-on -d 500 node_modules/meteor-client.js && cd api && meteor run
#
#
# > demo7@0.0.0 build:meteor-client [...]/demo7
# > meteor-client bundle -s api
#
# Created a new Meteor app in '/tmp/tmp-22153KmGKEQpbLn9j'.
#
# To run your new app:                          
#   cd /tmp/tmp-22153KmGKEQpbLn9j               
#   meteor                                      
#                                              
# If you are new to Meteor, try some of the learning resources here:
#   https://www.meteor.com/tutorials            
#                                              
# To start with a different app template, try one of the following:
#
#   meteor create --bare    # to create an empty app
#   meteor create --minimal # to create an app with as few Meteor packages as possible
#   meteor create --full    # to create a more complete scaffolded app
#                                              
# audited 602 packages in 1.871s
# found 0 vulnerabilities
#
#                                              
# Changes to your project's package version selections:
#                                              
# autopublish                   removed from your project
# barbatus:typescript           added, version 0.7.0
# barbatus:typescript-compiler  added, version 0.10.0
# barbatus:typescript-runtime   added, version 1.1.0
# blaze                         removed from your project
# blaze-html-templates          removed from your project
# insecure                      removed from your project
# jquery                        removed from your project
# observe-sequence              removed from your project
# spacebars                     removed from your project
# static-html                   added, version 1.2.2
# templating                    removed from your project
# templating-compiler           removed from your project
# templating-runtime            removed from your project
# ui                            removed from your project
#
#                                              
# WARNING: The output directory is under your source tree.
#          Your generated files may get interpreted as source code!
#          Consider building into a different directory instead
#          meteor build ../output
#                                              
# Errors prevented bundling:                    
# While processing files with static-html (for target web.browser):
# client/main.html:12: Expected <head> or <body> tag
#
# While processing files with static-html (for target web.browser.legacy):
# client/main.html:12: Expected <head> or <body> tag
#
# [...]/demo7/node_modules/meteor-client-bundler/node_modules/execa/index.js:350
# 		throw err;
# 		^
#
# Error: Command failed: meteor build --debug --directory .
#     at makeError ([...]/demo7/node_modules/meteor-client-bundler/node_modules/execa/index.js:172:9)
#     at Function.module.exports.sync ([...]/demo7/node_modules/meteor-client-bundler/node_modules/execa/index.js:341:15)
#     at Object.bundle ([...]/demo7/node_modules/meteor-client-bundler/lib/bundler.js:114:9)
#     at Command.<anonymous> ([...]/demo7/node_modules/meteor-client-bundler/cli:47:13)
#     at Command.listener ([...]/demo7/node_modules/meteor-client-bundler/node_modules/commander/index.js:315:8)
#     at emitTwo (events.js:126:13)
#     at Command.emit (events.js:214:7)
#     at Command.parseArgs ([...]/demo7/node_modules/meteor-client-bundler/node_modules/commander/index.js:651:12)
#     at Command.parse ([...]/demo7/node_modules/meteor-client-bundler/node_modules/commander/index.js:474:21)
#     at Object.<anonymous> ([...]/demo7/node_modules/meteor-client-bundler/cli:55:9)
# npm ERR! code ELIFECYCLE
# npm ERR! errno 1
# npm ERR! demo7@0.0.0 build:meteor-client: `meteor-client bundle -s api`
# npm ERR! Exit status 1
# npm ERR! 
# npm ERR! Failed at the demo7@0.0.0 build:meteor-client script.
# npm ERR! This is probably not a problem with npm. There is likely additional logging output above.
#
# npm ERR! A complete log of this run can be found in:
# npm ERR!     [...]/.npm/_logs/2018-08-18T08_17_09_985Z-debug.log
# npm ERR! code ELIFECYCLE
# npm ERR! errno 1
# npm ERR! demo7@0.0.0 prestart:local:client:dev: `path-exists node_modules/meteor-client.js || npm run build:meteor-client`
# npm ERR! Exit status 1
# npm ERR! 
# npm ERR! Failed at the demo7@0.0.0 prestart:local:client:dev script.
# npm ERR! This is probably not a problem with npm. There is likely additional logging output above.
#
# npm ERR! A complete log of this run can be found in:
# npm ERR!     [...]/.npm/_logs/2018-08-18T08_17_10_924Z-debug.log
# ERROR: "start:local:client:dev" exited with 1.
# npm ERR! code ELIFECYCLE
# npm ERR! errno 1
# npm ERR! demo7@0.0.0 start:local:dev: `run-p start:local:api start:local:client:dev`
# npm ERR! Exit status 1
# npm ERR! 
# npm ERR! Failed at the demo7@0.0.0 start:local:dev script.
# npm ERR! This is probably not a problem with npm. There is likely additional logging output above.
#
# npm ERR! A complete log of this run can be found in:
# npm ERR!     [...]/.npm/_logs/2018-08-18T08_17_11_043Z-debug.log

git add -all
git commit -m "Not buildable application when package 'static-html' is installed"

git remote add origin git@github.com:atao60/angular-meteor-example-AngularCLI-bare.git
git push -u origin master

```

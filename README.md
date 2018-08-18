# angular-meteor-example-AngularCLI

Demo about using `meteor --bare` to set up a Meteor AngularCLI example from scratch as [angular-meteor/examples/AngularCLI](https://github.com/Urigo/angular-meteor/tree/master/examples/AngularCLI).

See:

* [[examples/AngularCLI]: meteor-client-bundler doesn't like 'static-html' #1950](https://github.com/Urigo/angular-meteor/issues/1950)
* [meteor-client-bundler doesn't like 'static-html' #78](https://github.com/Urigo/meteor-client-bundler/issues/78)

## Install and run

```bash

git clone https://github.com/atao60/angular-meteor-example-AngularCLI-bare.git demo

cd demo

npm install

npm run start:local:dev

```

As it is, the application is not buildable.

```bash
(cd api && meteor remove static-html)

npm run clean:build

npm run start:local:dev

```

Go to http://localhost:4200
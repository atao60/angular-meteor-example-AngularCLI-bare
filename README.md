# angular-meteor-example-AngularCLI

Demo about using `meteor --bare` to set up a Meteor AngularCLI example from scratch. See [[examples/AngularCLI]: ???](https://github.com/Urigo/angular-meteor/issues/???).

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

npm run start:local:dev

```

Go to http://localhost:4200
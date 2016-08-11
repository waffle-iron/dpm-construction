# DPM Construction

### Install Prerequisites

* [Node.js](https://nodejs.org)
* [npm](https://www.npmjs.com/)
```bash
sudo apt-get install nodejs-legacy npm -y
```

* [bower](https://bower.io/)
* [polymer-cli](https://github.com/Polymer/polymer-cli)
* [firebase-tools](https://github.com/firebase/firebase-tools)
```bash
npm i -g bower polymer-cli firebase-tools
```

### Update dependencies
This command will update all the bower dependencies specified in `bower.json`.
```bash
bower update
```

### Run Development server
This command serves the app at `http://localhost:8080` and provides basic URL routing for the app.
```bash
polymer serve
```

### Build
This command performs HTML, CSS, and JS minification on the application
dependencies, and generates a service-worker.js file with code to pre-cache the
dependencies based on the entrypoint and fragments specified in `polymer.json`.
The minified files are output to the `build/unbundled` folder, and are suitable
for serving from a HTTP/2+Push compatible server.

In addition the command also creates a fallback `build/bundled` folder,
generated using fragment bundling, suitable for serving from non
H2/push-compatible servers or to clients that do not support H2/Push.

```bash
polymer build
```

### Test the Build
This command serves the minified version of the app in an unbundled state, as it would
be served by a push-compatible server.
```bash
polymer serve build/unbundled
```

This command serves the minified version of the app generated using fragment bundling.
```bash
polymer serve build/bundled
```

### Deploy
This command deploys the application to the firebase app instance based on the `firebase.json` file.
```bash
firebase deploy
```

### Clean, Update, Build, and Deploy
This command will clean the old build, update dependencies, rebuild, and deploy to the firebase instance.
```bash
rm -rf build && bower update && polymer build && firebase deploy
```

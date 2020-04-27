<div align="center">
<img alt="Electron Gatsby" src="https://raw.githubusercontent.com/soulehshaikh99/repo/master/svg/Electron_Gatsby.svg" width="550" />
</div>
<br />
The boilerplate code to get started creating Cross-platform Desktop Apps with Electron and Gatsby.js as front-end technology.
<br />
<br />
<div align="center">

[![forthebadge](http://forthebadge.com/images/badges/built-by-developers.svg)](http://forthebadge.com)&nbsp;&nbsp;&nbsp;&nbsp;[![forthebadge](http://forthebadge.com/images/badges/makes-people-smile.svg)](http://forthebadge.com)<br />

[![forthebadge](http://forthebadge.com/images/badges/uses-html.svg)](http://forthebadge.com)&nbsp;&nbsp;&nbsp;[![forthebadge](http://forthebadge.com/images/badges/uses-css.svg)](http://forthebadge.com)&nbsp;&nbsp;&nbsp;[![forthebadge](http://forthebadge.com/images/badges/uses-js.svg)](http://forthebadge.com)

[![js-standard-style](https://cdn.rawgit.com/feross/standard/master/badge.svg)](https://github.com/feross/standard)

</div>

## Overview

The aim of this project is to provide Web Developers using `gatsby.js` the power to create cross-platform desktop apps using `electron`. 

#### What packages does the project use?
`electron` enables you to create desktop applications with pure JavaScript by providing a runtime with rich native (operating system) APIs. You could see it as a variant of the Node.js runtime that is focused on desktop applications instead of web servers.
<br />

`electron-builder` is used as a complete solution to package and build a ready for distribution (supports Numerous target formats) Electron app with "auto update" support out of the box.
<br />

`electron-serve` is used for Static file serving for Electron apps.
<br />

`gatsby.js` is used as a front-end technology for this Project.

`gatsby-cli` is used to perform common functionality, such as creating a Gatsby application based on a starter, spinning up a hot-reloading local development server, and more!
<br />

`concurrently` is used to run multiple commands concurrently.
<br />

`wait-on` is used as it can wait for sockets, and http(s) resources to become available.
<br />

## Getting Started

**Note:** If you wish to use npm over yarn then modify package.json by replacing `yarn` with `npm` in `prebuild`, `electron-dev` and `preelectron-pack` scripts.
But I strongly recommend using <em>yarn</em> as it is a better choice when compared to <em>npm</em>.

### Use this boilerplate

```bash
# Clone the Project
# GitHub CLI Users
$ gh repo clone https://github.com/soulehshaikh99/create-gatsby-electron-app.git
# or Normal Git Users
$ git clone https://github.com/soulehshaikh99/create-gatsby-electron-app.git

# Switch location to the cloned directory
$ cd create-gatsby-electron-app

# Install dependencies
$ yarn # or npm install

# Run your app
$ yarn electron-dev # or npm run electron-dev

# Package Your App
$ yarn electron-pack # or npm run electron-pack
```

### Create this boilerplate from scratch (Manual Setup)

#### 1) Install `gatsby-cli` globally
```bash
$ yarn global add gatsby-cli # or npm i -g gatsby-cli
```

#### 2) Create new project
```bash
$ gatsby new create-gatsby-electron-app
```

#### 3) Change Directory
```bash
$ cd create-gatsby-electron-app
```

#### 4) Move all dependencies to devDependencies using IDE / Text Editor

```json
# It should look something like this
"dependencies": {},
"devDependencies": {
  "gatsby": "^2.20.35",
  "gatsby-image": "^2.3.5",
  "gatsby-plugin-manifest": "^2.3.7",
  "gatsby-plugin-offline": "^3.1.5",
  "gatsby-plugin-react-helmet": "^3.2.5",
  "gatsby-plugin-sharp": "^2.5.7",
  "gatsby-source-filesystem": "^2.2.5",
  "gatsby-transformer-sharp": "^2.4.7",
  "prettier": "2.0.4",
  "prop-types": "^15.7.2",
  "react": "^16.12.0",
  "react-dom": "^16.12.0",
  "react-helmet": "^6.0.0"
}
```

#### 5) Install Development Dependencies
```bash
$ yarn add --dev electron electron-builder wait-on concurrently
# npm i -D electron electron-builder wait-on concurrently
```

#### 6) Install Production Dependency
```bash
$ yarn add electron-serve # or npm i electron-serve
```

#### 7) Your dependencies should look something like this

```json
"dependencies": {
  "electron-serve": "^1.0.0"
},
"devDependencies": {
  "concurrently": "^5.2.0",
  "electron": "^8.2.3",
  "electron-builder": "^22.5.1",
  "gatsby": "^2.20.35",
  "gatsby-image": "^2.3.5",
  "gatsby-plugin-manifest": "^2.3.7",
  "gatsby-plugin-offline": "^3.1.5",
  "gatsby-plugin-react-helmet": "^3.2.5",
  "gatsby-plugin-sharp": "^2.5.7",
  "gatsby-source-filesystem": "^2.2.5",
  "gatsby-transformer-sharp": "^2.4.7",
  "prettier": "2.0.4",
  "prop-types": "^15.7.2",
  "react": "^16.12.0",
  "react-dom": "^16.12.0",
  "react-helmet": "^6.0.0",
  "wait-on": "^4.0.2"
}
```

#### 8) Create main.js file (serves as entry point for Electron App's Main Process)
```bash
$ notepad.exe main.js # Windows Users
$ touch main.js # Linux and macOS Users
```

#### 9) Paste the below code in main.js file
```js
// Modules to control application life and create native browser window
const {app, BrowserWindow, dialog } = require('electron');
const path = require('path');
const serve = require('electron-serve');
const loadURL = serve({directory: 'public'});

// Keep a global reference of the window object, if you don't, the window will
// be closed automatically when the JavaScript object is garbage collected.
let mainWindow;

function isDev() {
    return !app.isPackaged;
}

function createWindow () {
    // Create the browser window.
    mainWindow = new BrowserWindow({
        width: 800,
        height: 600,
        webPreferences: {
            nodeIntegration: true
        },
		icon: isDev() ? `${path.join(process.cwd(), 'src/images/gatsby-icon.png')}` : `${path.join(__dirname, 'public/icons/icon-512x512.png')}`,
        show: false
    });

    // This block of code is intended for development purpose only.
    // Delete this entire block of code when you are ready to package the application.
    if(isDev()) {
        mainWindow.loadURL('http://localhost:8000/');
    } else {
        //Do not delete this statement, Use this piece of code when packaging app for production environment
		loadURL(mainWindow);
    }

    // Open the DevTools and also disable Electron Security Warning.
    // process.env['ELECTRON_DISABLE_SECURITY_WARNINGS'] = true;
    // mainWindow.webContents.openDevTools();

    // Emitted when the window is closed.
    mainWindow.on('closed', function () {
        // Dereference the window object, usually you would store windows
        // in an array if your app supports multi windows, this is the time
        // when you should delete the corresponding element.
        mainWindow = null
    });

    // Emitted when the window is ready to be shown
    // This helps in showing the window gracefully.
    mainWindow.once('ready-to-show', () => {
        mainWindow.show()
    });
}

// This method will be called when Electron has finished
// initialization and is ready to create browser windows.
// Some APIs can only be used after this event occurs.
app.on('ready', createWindow);

// Quit when all windows are closed.
app.on('window-all-closed', function () {
    // On macOS it is common for applications and their menu bar
    // to stay active until the user quits explicitly with Cmd + Q
    if (process.platform !== 'darwin') app.quit()
});

app.on('activate', function () {
    // On macOS it's common to re-create a window in the app when the
    // dock icon is clicked and there are no other windows open.
    if (mainWindow === null) createWindow()
});
// In this file you can include the rest of your app's specific main process
// code. You can also put them in separate files and require them here.
```

#### 10) Add pre-build, electron, electron-dev, preelectron-pack and electron-pack scripts

```bash
# add this scripts
"prebuild": "yarn run clean",
"electron": "wait-on http://localhost:8000 && electron .",
"electron-dev": "concurrently \"yarn run start\" \"yarn run electron\"",
"preelectron-pack": "yarn run build",
"electron-pack": "electron-builder"

# you should end up with something similar
"scripts": {
  "start": "gatsby develop",
  "serve": "gatsby serve",
  "prebuild": "yarn run clean",
  "build": "gatsby build",
  "clean": "gatsby clean",
  "format": "prettier --write \"**/*.{js,jsx,json,md}\"",
  "test": "echo \"Write tests! -> https://gatsby.dev/unit-testing\" && exit 1",
  "electron": "wait-on http://localhost:8000 && electron .",
  "electron-dev": "concurrently \"yarn run start\" \"yarn run electron\"",
  "preelectron-pack": "yarn run build",
  "electron-pack": "electron-builder"
},
```
#### 11) Add the following Electron Configuration in package.json
**Note:** build configuration is used by electron-builder, modify it if you wish to add more packaging and native distribution options for different OS Platforms.
```json
"main": "main.js",
"build": {
  "icon": "src/images/gatsby-icon.png",
  "productName": "Gatsby and Electron App",
  "files": [
    "public/**/*",
    "main.js"
  ]
}
```

#### 12) Test drive your app
```bash
# Run your app
$ yarn electron-dev # or npm run electron-dev

# Package Your App
$ yarn electron-pack # or npm run electron-pack
```

<h3>Made with :heart: from Souleh</h3>

[![forthebadge](http://forthebadge.com/images/badges/built-with-love.svg)](http://forthebadge.com)
<br/>
<h3>:clipboard: License: </h3>
Licensed under the <a href="https://github.com/soulehshaikh99/create-gatsby-electron-app/blob/master/LICENSE">MIT License</a>.
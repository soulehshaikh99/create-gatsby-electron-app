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
<br />

`concurrently` is used to run multiple commands concurrently.
<br />

`wait-on` is used as it can wait for sockets, and http(s) resources to become available.
<br />

## Getting Started

**Note:** If you wish to use npm over yarn then modify package.json by replacing `yarn` with `npm` in electron-dev and preelectron-pack scripts.
But I strongly recommend using <em>yarn</em> as it is a better choice when compared to <em>npm</em>.

#### Use this boilerplate

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
$ yarn run electron-dev # or npm run electron-dev

# Package Your App
$ yarn run electron-pack # or npm run electron-pack
```
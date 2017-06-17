# VuejsFire Hackathon Starter

VuejsvFire is a project starter kit based on [Vue.js]() JavaScript framework and [Firebase]() as backend. This starter kit is actually born out of my side-project [Tolks]().

---
[Demo](http://kushagragour.in/vuejsfire-hackathon-starter/) • [Features](#features) • [Ingredients](#ingredients) • [Getting Started](#getting-started-with-development) • [Deployment](#deployment) • [Detailed Wiki](https://github.com/chinchang/vuejsfire-hackathon-starter/wiki/)
---

![](/screenshots/screenshot1.png)

### Features

- Built over Vuejs' [webpack-simple template](https://github.com/vuejs-templates/webpack-simple)
- ES6 ready
- Single file components
- In-built User Module
- Twitter/Facebook Authentication
- In-built notification system
- Beautiful design and experience
- Responsive UI

### Ingredients

- [Vue.js webpack-simple template](https://github.com/vuejs-templates/webpack-simple)
- [Firebase](https://firebase.google.com)
- [Material Design Icons](https://materialdesignicons.com/)
- Page loader by [Tobias Ahlin](http://tobiasahlin.com/spinkit/)
- [Roboto](https://fonts.google.com/specimen/Roboto) font from Google fonts

### Getting started with development

- Clone this repo.
- Create a project in [Firebase](https://console.firebase.google.com/). Note, the app would also run with the default Firebase config included in the project. But its advised to replace it with your own Firebase project.
- Turn on [Twitter](https://firebase.google.com/docs/auth/web/twitter-login) & [Facebook](https://firebase.google.com/docs/auth/web/facebook-login) in your Firebase project.
- Replace the Firebase credentials in `auth.js`.
- Run `npm install` to install all dependencies.
- Run `npm run dev` to spin the local server and access your cool app on `localhost:8080`.

### Deployment

- Run `npm run build` to build the project.
- If you are using Github pages for deployment, you can simply run `build-gh-pages.sh` instead.

[Read more about deployment](https://github.com/chinchang/vuejsfire-hackathon-starter/wiki#deployment).

### License

Open source under The MIT License

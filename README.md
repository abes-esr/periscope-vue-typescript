# periscope-poc-vue-js-latest

## Notes de developpement
Projet crée avec vue/cli4, en vue 2, avec vuetify 2, axios, jest, et gantt-timeline.
Pour visualiser l'avancement du projet, aller sur la branche develop.
Développeur: Thomas Angot
Tuteur: Jerome Villiseck

Be carefull ! Vuetify doesn't work with Vue3 project at 16.11.2020 (vue2 only).

## Project initialization
```
npm install -g @vue/cli
```

```
vue create periscope-poc-vue-js-latest
```
1. vue2, babel, router, vuex, linter, unit testing (jest).
2. cd [emplacement du projet]

```
vue add vuetify
```

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your unit tests
```
npm run test:unit
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).


### Force resolution of vulnerabilities
install in package.json file
```javascript
"scripts": {
    "serve": "vue-cli-service serve",
    "build": "vue-cli-service build",
    "test:unit": "vue-cli-service test:unit",
    "lint": "vue-cli-service lint",
    "preinstall": "npx npm-force-resolutions"
  },
  "resolutions": {
    "yargs-parser": "15.0.1"
  },
```
As the example, the script preinstall was added, and a specific version of yargs-parser (who depends on top level jest npm module)
will be forced to update in node_module.
Then, run the script: npx npm-force-resolutions
and just tap on commands:
```
npm i && npm audit fix --force
```
Tip: think to run the script after each npm installation modules.

##Router bug (warning)

Please tap after the creation of your vuetify project

```
vue add router
```

And this will restore functionalities on router.

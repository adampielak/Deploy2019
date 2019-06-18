### Installation vue-cli:
```bash
npm install -g @vue/cli
```

### Upgrade vue-cli:
```bash
npm uninstall -g vue-cli
npm install -g @vue/cli
```
### Install FontAwesome:
```bash
npm install vue-awesome
```
#### In main.js:
```js
import 'vue-awesome/icons'
import Icon from 'vue-awesome/components/Icon'
Vue.component('v-icon', Icon)
```

#### In xxx.vue:
```js

<template>
<v-icon name="camera"/>
```

#### Create Project:
```bash
vue create project_name
# or
vue create -p preset project_name

npm run serve
```

* check webpack configuration
```bash
cd project_name
vue inspect
```

### Deployment:
https://cli.vuejs.org/guide/deployment.html
```bash
npm run build
```

### Resources:
* https://vuejsexamples.com/generate-a-vue-form-with-validation-and-bulma-style-from-json/
* https://scotch.io/tutorials/create-a-single-page-app-with-go-echo-and-vue
* https://scotch.io/courses/build-an-online-shop-with-vue

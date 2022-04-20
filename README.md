# vue-rick-and-morty

# 1 - Creare il progetto con Vue cli
Dopo aver creato la repository nuova su GitHub, la cloniamo sul pc e apriamo la cartella con VS Code
Utilizzare,poi, il terminale nella cartella del progetto per eseguire il comando:

```
vue create .
```

# 2 - Importare Bootstrap
Lanciare da terminale dentro la cartella del progetto i due comandi
```
npm install --save bootstrap
npm install --save @popperjs/core
```

Dopo aver installato le 2 dipendenze di bootstrap 5 dobbiamo importare i file CSS e JS di riferimento dentro app.vue

Dentro la sezione "script" scriviamo:
```
import "bootstrap"
```

Dentro la sezione style scriviamo: 
```
@import "bootstrap/dist/css/bootstrap.min.css";
```

# 3 - Creare un componente
Creare un file all'interno della cartella "components", il nome del file deve essere con la prima lettera maiuscola e di due parole in camelcase (HeaderComp.vue)

La struttura del componente deve essere all'inizio la seguente:
```javascript
<template>
<template/>

<script>
<script/>

<style>
<style/>
```

Successivamente, andare in App.vue per importare il componente nello "script"
```javascript
import HeaderComp from './components/HeaderComp.vue'

export default {
  name: 'App',
  components: {
    HeaderComp
  }
}
```

Utilizzare il componente dentro App.vue
```javascript
<HeaderComp/>
```
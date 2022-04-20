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

# 4 - Utilizzare axios nel progetto

Per utilizzarlo, bisogna importare axios nel terminale con il seguente comando:

```javascript
npm i axios
```

Successivamente, bisogna importarlo nel componente di utilizzo nella sezione "script" in questo modo:

```javascript
<script>

import axios from 'axios';

export default {
    //Cambiare il nome con quello del componente cretao
    name:'AvatarsComp',
    data(){
        return{
            //Creaiamo un array in cui salviamo i data della chiamata axios e modificare il nome a piacere
            avatarsArray: []
        }
    },
    created(){
        //Modificare il link con l'api che si vuole usare
        axios.get('https://api.sampleapis.com/rickandmorty/characters')
            .then((res) => {
                //Controllo delle informazioni che otteniamo dalla chiamata
                console.log(res.data);
                //Modifica dell'array dove salveremo i dati
                this.avatarsArray = res.data;
            })
            //Salvataggio in console di possibili errori
            .catch ((error) => {
                console.log(error)
            })
    }
}

</script>
```
# 5 - come usare i props tra componente padre e figlio

I props ci servono quando vogliamo passar ele informazioni tra due componenti, e il componente padre è colui che ha i dati da passare al componente figlio.

Componente Padre:
```javascript
<template>
  <div class="row">
    <!--Questo è il componente figlio a cui passare i dati-->
    <CardAvatar
      v-for="( element, index ) in avatarsArray"
      :key="index"
      //Qui sotto abbiamo i props dei dati che vogliamo passare al figlio "CardAvatar"
      //Questi dati sono ottenuti tramite axios e salavti in un array nei "Data"
      //Sono alcune informazioni del JSON dell'API
      :image="element.image"
      :name="element.name"
      :species="element.species"
      :origin="element.origin"
    />

  </div>
</template>

<script>

import axios from 'axios';

import CardAvatar from './partials/CardAvatar.vue'

export default {
  //Cambiare il nome con quello del componente creato
  name: 'AvatarsComp',
  components: {
    CardAvatar
  },
  data(){
    return{
      avatarsArray: []
    }
  },
  created(){
    //Qui utiliziamo axios
    axios.get( 'https://api.sampleapis.com/rickandmorty/characters' )
         .then( ( res )=>{
           console.log( res.data );
           this.avatarsArray = res.data
         } )
         .catch( (error) => {
           console.log( error )
         } )
  }
}
</script>
```
Il componente figlio:
```javascript
<template>
  <div class="col-3 text-center my-5">
    <!--inserire contenuto componente-->
    <!--Il contenuto del componente richiama le informazioni dei props-->
      <img :src="image" alt="" class="rounded-circle">
      <h3 class="my-3">{{name}}</h3>
      <div class="divider my-3"></div>
      <h4 class="my-3">{{origin}}</h4>
      <span class="fw-bolder my-3">{{species}}</span>
  </div>
</template>

<script>
export default {
  //Cambiare il nome con quello del componente creato
  name: 'CardAvatar',
  //Sezione dove riportare i props e la loro tipologia
  props: {
    image: String,
    name: String,
    species: String,
    origin: String,
  }
}
</script>

<style scoped lang="scss">
 /*Inserire style componente*/
 .divider{
   width: 30%;
   height: 1px;
   background-color: #1a1a1a;
   margin: 0 auto;
 }
</style>
```
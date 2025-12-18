<script setup>
import { ref} from 'vue';
import { useFetch } from '../composables/useFetch';


const url=ref(`http://localhost:3000/songs`)

const {data, error,loading, fetchData}=useFetch(url);
const idItem=ref(null)
</script>

<template>
  <div v-if="loading">
      <p>loading</p>
  </div>

  <div v-else-if="error">
    <p>Error: {{ error }}</p>
  </div>

  <div v-else>
      <!--Aquí ya se cargó los datos de la api-->
      <p>{{ idItem }}</p>
      <div id="buscardor">
           <input type="number" v-model="idItem"/> 
           <button type="button" >Buscar</button>
      </div>
   
    <div  v-if="data && data.songs" class="containerMeals">
        <div v-for="song in data.songs" >
            <p><strong>Titulo: </strong>{{ song.title }}</p>
            <p><strong>Cantante: </strong>{{ song.singer }}</p>
        </div>
    </div>
    </div>
</template>
<style  scoped>
    
</style>
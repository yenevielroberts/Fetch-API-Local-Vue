<script setup>
import { ref} from 'vue';
import { useFetch } from '../composables/useFetch';


const url=ref(`http://localhost:3000/songs`)

const {data, error,loading, fetchData}=useFetch(url);



</script>

<template>
  <div v-if="loading">
      <p>loading</p>
  </div>

  <div v-else-if="error">
    <p>Error: {{ error }}</p>
  </div>

  <div v-else>
    <p>Hola</p>
    <!--Aquí ya se cargó los datos de la api-->
    <div  v-if="data && data.songs" class="containerMeals">
      <div v-for="song in data.songs" >
       <p>{{ song.title }}</p>
       <p>{{ song.singer }}</p>
      
      </div>
    </div>
  </div>
</template>

<style>

</style>
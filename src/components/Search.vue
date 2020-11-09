<template>
 <div class='search'>
  <h1>Search</h1>
  <input type='text' v-model='query' @keyup='getResult(query)'>
  <div v-for='result in results' :key='result.id'>
   <p>{{result.title}}</p>
   <img v-bind:src="'http://image.tmdb.org/t/p/w500/' +    result.poster_path" width='100px'>
  </div>
 </div>
</template>
<script>
import axios from 'axios'
export default {
 name: 'search',
 data () {
  return {
   query: '',
   results: ''
  }
 },
 methods: {
  getResult(query) {
   axios.get('https://api.themoviedb.org/3/search/movie?api_key=556b76195b45a0a80dab2c28f97a97e0&query=' + query).then(response => { this.results = response.data.results })
     console.log(this.results)
   }
 }
}
</script>
<template>
  <div id="app">
    <Header title="Find a Movie!" />
    <Search @search-phrase="fetchMovies" />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Search from './components/Search.vue';

export default {
  name: 'App',
  components: {
    Header,
    Search,
  },
  data() {
    return {
      results: [],
      apiKey: "a1851be38bmshc3fa68bafe8f5a7p1db595jsnf532076fd47a",
    }
  },
  methods: {
    fetchMovies(title) {
      fetch(`https://movie-database-imdb-alternative.p.rapidapi.com/?s=${title}&page=1&r=json`, {
        "method": "GET",
        "headers": {
          "x-rapidapi-key": this.apiKey,
          "x-rapidapi-host": "movie-database-imdb-alternative.p.rapidapi.com"
        }
      })
      .then(async response => {
        const data = await response.json();

        if (!response.ok) {
          const error = (data && data.message) || response.statusText;
          return Promise.reject(error)
        }

        console.log('data', data)
      })
      .catch(error => console.error('error', error))
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

// async fetchMovies() {
//       const response = await fetch('https://cat-fact.herokuapp.com/facts');
//       const data = response.json();
//       this.results = data;
//       console.log('data', data)
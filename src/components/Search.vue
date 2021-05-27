<template>
  <div>
    <form @submit.prevent="searchForMovie()">
      <input v-model="searchInfo" type="search" placeholder="Search by movie title" id="searchBar" />
      <label for="searchBar"></label>
      <p>{{ searchInfo}}</p>
    </form>

  </div>
</template>

<script>
export default {
  data() {
    return {
      searchInfo: ''
    }
  },
  methods: {
    searchForMovie() {
      this.$emit('search-phrase', this.searchInfo);
      this.searchInfo = '';
    }
  }
}

</script>

// fix inner padding for text/placeholder
<style scoped>
#searchBar {
  width: 80vw;
  height: 6vh;
  background-color: aquamarine;
  border: none;
}
</style>
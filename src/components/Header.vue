<template>
  <header class="header">
    <h1 class="title">{{ title }}</h1>
  </header>
</template>

<script>
export default {
  name: 'app-header',
  props: {
    title: String
  }
}
</script>

<style scoped>
.header {
  margin: 50px 20px;
}

.title {
  margin: 0;
}
</style>
<template>
  <ul v-for="(item, index) in items" :key="index">
    <li>{{item}}</li>
  </ul>
</template>

<script>
export default {
  name: 'NavBar',
  data() {
    return {
      items: ['home', 'about', 'works', 'blog', 'hire me']
    }
  }
}
</script>

<style scoped>

</style>
<template>
  <NavBar />
  <br>
  <Welcome />
  <br>
  <Footer />
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import NavBar from './components/NavBar.vue';
import Welcome from './components/Welcome.vue';
import Footer from './components/Footer.vue';

@Options({
  components: {
    NavBar,
    Welcome,
    Footer
  },
})
export default class App extends Vue {}
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

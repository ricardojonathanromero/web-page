<template>
  <h2>This is my blog</h2>
  <button @click="getPokes">Get pokemon</button>&nbsp;&nbsp;<button @click="clear">Clear</button>
  <hr>
  <div class="row justify-content-center">
    <div class="col-auto">
      <table class="table">
        <thead class="thead-dark" v-if="pokeList.length > 0">
        <tr>
          <th scope="col">#</th>
          <th scope="col">Name</th>
          <th scope="col">Info</th>
        </tr>
        </thead>
        <tbody v-for="(poke, index) in pokeList" :key="index">
        <tr>
          <th scope="row">{{ index + 1 }}</th>
          <td>{{ poke.name.toUpperCase() }}</td>
          <td>
            <router-link :to="`/blog/${ index + 1 }`">{{ poke.name }} info</router-link>
          </td>
        </tr>
        </tbody>
      </table>
    </div>
  </div>
  <Footer/>
</template>

<script>
import Footer from '@/components/Footer.vue'

export default {
  name: 'Blog',
  components: {
    Footer
  },
  data() {
    return {
      pokeList: []
    };
  },
  methods: {
    async getPokes() {
      try {
        const data = await fetch('https://pokeapi.co/api/v2/pokemon?limit=150');
        const pokeList = await data.json();
        this.pokeList = pokeList.results;
      } catch (e) {
        console.error(e);
      }
    },
    clear() {
      this.pokeList = [];
    }
  },
  created() {
    this.getPokes();
  }
}
</script>
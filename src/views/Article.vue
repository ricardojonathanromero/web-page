<template>
  <Title :msg="info.name.toUpperCase()" />
  <img :src="info.sprites.front_default" :alt="info.name">
  <Footer/>
</template>

<script>
import Title from '@/components/Title.vue'
import Footer from '@/components/Footer.vue'

export default {
  name: "Article",
  components: {
    Title,
    Footer
  },
  data() {
    return {
      info: {}
    };
  },
  methods: {
    async pokeDetail() {
      try {
        const data = await fetch(`https://pokeapi.co/api/v2/pokemon/${this.$route.params.id}/`);
        this.info = await data.json();
      } catch (e) {
        console.error(e);
      }
    }
  },
  created() {
    this.pokeDetail();
  }
}
</script>
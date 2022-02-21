<template>
  <div id="app">
    <h1>PHOTOzzz</h1>
    <PhotoContainer :items="loaded" />
    <button @click="fetchPage">more</button>
  </div>
</template>

<script>
import PhotoContainer from './components/PhotoContainer.vue'
export default {
  name: 'App',
  components: {
    PhotoContainer,
  },
  data: function() {
    return {
      page: 1,
      loaded: []
    }
  },
  methods: {
    fetchPage: async function() {
      const page = await fetch(`https://jsonplaceholder.typicode.com/photos?_page=${this.page}&_limit=9`);
      const pageJSON = await page.json();
      pageJSON.forEach(element => {
        this.loaded.push(element);
      });
      this.page++;
    }
  },
  mounted() {
    this.fetchPage();
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  background-color: #333;
  color: rgb(238, 238, 238);
  width: 100vw;
  height: 100vh;
  padding-top: 60px;
  display: flex;
  flex-direction: column;
  align-items: center;

}
</style>

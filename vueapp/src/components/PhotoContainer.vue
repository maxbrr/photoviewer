<template>
  <div id="photoContainer">
    <div id="photoContainerPage" v-if="!detail">
        <div v-for="item in items" :key="item.id">
          <img :src="item.thumbnailUrl" @click="select(item)">
        </div>
    </div>
    <div id="photoContainerSingle" v-if="detail">
      <h3>ID: {{ currentItem.id }}</h3>
      <h3>TITLE: {{ currentItem.title }}</h3>
      <img :src="currentItem.url" width="300" height="300">
      <button @click="back">BACK</button>
    </div>
  </div>
  
</template>

<script>
export default {
  data: function() {
      return {
        detail: false,
        currentItem: null
      }
  },
  props: ['items'],
  methods: {
    select: function(item) {
      this.currentItem = item;
      this.detail = true;
    },
    back: function() {
      this.detail = false;
    }
  }
}
</script>

<style>
  #photoContainerPage {
    background-color: rgb(75, 75, 75);
    width: 550px;
    height: 550px;
    display: flex;
    justify-content: space-around;
    align-items: center;
    flex-wrap: wrap;
    overflow-y: scroll;
  }

  #photoContainerSingle {
    background-color: rgb(75, 75, 75);
    width: 550px;
    height: 550px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-around;
  }
</style>
<template>
  <div class="home">
    <h1>Test API Evento</h1>
    <button @click="loadCats">Give me cats</button>
    <div v-for="cat in cats" :key="cat.id" class="cat">
      <img :src="cat.url"/>
    </div>
  </div>
</template>
<script>
  import axios from 'axios';
export default {
  date() {
    return {
      cats: []
    };
  },
  methods: {
    loadCats() {
      axios
        .get("https://api.thecatapi.com/v1/images/search?limit=6", {
          headers: {
            "x-api-key": "DEMO-API-KEY"
          }
        })
        .then(response => {
          console.log(response.headers);
          console.log(response.data);
          this.cats = response.data;
        })
        .catch(error => {
          console.log(error);
        });
    }
  }
};
</script>
<style>
.cat {
  width: 300px;
}
img.cat {
  width: 100%;
}
</style>
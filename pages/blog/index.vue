<template>
  <div class="container mt-5 row">
    <div class="card my-2" v-for="(item, index) in articulos" :key="index">
      <div class="card-body">
        <nuxt-link :to="`blog/${item.id}`">
          <h3>{{item.title}}</h3>
        </nuxt-link>
        <p>{{item.body}}</p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  data() {
    return {
      articulos: []
    };
  },
  async created(){
    const res = await axios.get("https://jsonplaceholder.typicode.com/posts?_limit=10");
    this.articulos = res.data;
  }
};
</script>
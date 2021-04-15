<template>
<v-container fluid grid-list-md>
<v-layout row wrap>
  <v-btn v-on:click='created()' type="submit">Post</v-btn>
<v-flex v-for="(post, index) in posts" :key="index">
  <v-card
    class="mx-auto"
    tile
  >
    <v-list-item>
      <v-list-item-content>
        <!-- <v-list-item-title>{{post.albumId}}</v-list-item-title> -->
        <v-list-item-subtitle><strong>{{post.id}}</strong>
        </v-list-item-subtitle>
        <div>
        <img :src="post.url">
        </div>
        <p>{{post.title}}</p><button :id="post.id" v-on:click='updatePosts(post.id)'>Update</button>
        <v-btn v-on:click='deletePost(post.id)' >Delete</v-btn>
      </v-list-item-content>
    </v-list-item>
  </v-card>
</v-flex>
</v-layout>
</v-container>
</template>

<script>
import axios from 'axios';
export default {
  name: 'Requests',
  data() {
    return {
      posts: [],
    };
  },
  mounted() {
    this.getPosts();
  },
  methods: {
    async getPosts() {
      const response = await axios.get('https://jsonplaceholder.typicode.com/albums/1/photos');
      this.posts = response.data;
      // eslint-disable-next-line no-console
      console.log(this.posts);
    },
    async created() {
      // POST request using axios with async/await
      const article = {
        albumId: 55,
        id: 80,
        title: 'Post method using Axious',
        url: 'https://via.placeholder.com/600/24f355',
        thumbnailUrl: 'https://via.placeholder.com/150/24f355',
      };
      const headers = {
        'Content-type': 'application/json',
        charset: 'UTF-8',
      };
      const myResponse = await axios.post('https://jsonplaceholder.typicode.com/albums/1/photos', article, { headers });
      // eslint-disable-next-line no-console
      console.log(myResponse);
      this.getPosts();
    },
    async updatePosts(id) {
      // eslint-disable-next-line no-console
      console.log(id);
      const newUpdate = {
        albumId: 55,
        id: 43,
        title: 'Put method using Axious',
        url: 'https://via.placeholder.com/600/24f355',
        thumbnailUrl: 'https://via.placeholder.com/150/24f355',
      };
      const headers = {
        'Content-type': 'application/json',
        charset: 'UTF-8',
      };
      const url = 'https://jsonplaceholder.typicode.com/photos';
      const newResponse = await axios.put(`${url}/${id}`, newUpdate, { headers });
      // eslint-disable-next-line no-console
      console.log(newResponse);
    },
    async deletePost(id) {
      const url = 'https://jsonplaceholder.typicode.com/photos';
      const newResponse = await axios.put(`${url}/${id}`);
      // eslint-disable-next-line no-console
      console.log(newResponse);
    },
  },
};
</script>

<style scoped>
img{
  max-width: 250px;
  max-height: 250px;
  text-align: center;
}
</style>
<template>
  <div id="app">
    <h1>{{ postsCount }}</h1>
    <PostForm />
    <div class="post" v-for="post in validPost" :key="post.id">
      <h2>{{ post.title }}</h2>
      <p>{{ post.body }}</p>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex';
import PostForm from './components/PostForm.vue';

export default {
  name: 'app',
  computed: mapGetters(['validPost', 'postsCount']),
  methods: mapActions(['fetchPosts']),
  components: { PostForm },
  async mounted() {
    this.fetchPosts(6);
  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px auto;
  width: 400px;
}
.post{
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-bottom: 25px;
}
</style>

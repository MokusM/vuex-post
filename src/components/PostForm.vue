<template>
  <form @submit.prevent="submit">
    <input type="text" placeholder="title" required v-model="title">
    <input type="text" placeholder="body" required v-model="body">
    <button type="submit">Create Post</button>
    <hr>
  </form>
</template>
<script>
import { mapMutations } from 'vuex';

export default {
  data() {
    return {
      title: '',
      body: '',
    };
  },
  methods: {
    ...mapMutations(['createPost']),
    submit() {
      this.createPost({
        title: this.title,
        body: this.body,
        id: Date.now(),
      });
      this.title = '';
      this.body = '';
    },
  },
};
</script>
<style>
form{
  margin-bottom: 45px;
}
input{
  display: block;
  width: 100%;
  border: 1px solid #ccc;
  border-radius: 2px;
  font-size: 18px;
  line-height: 45px;
  margin-bottom: 15px;
  padding: 5px 15px;
}
button{
  width: 150px;
  height: 40px;
}
</style>

<template>
  <div>
    <h1>記事個別ページ{{ post.id }}</h1>
    <h2>{{ post.title }}</h2>
    <p>{{ post.body }}</p>
  </div>
</template>

<script>
// import axios from 'axios';

export default {
  // asyncData({ route }) {
  //   return axios.get(`https://jsonplaceholder.typicode.com/posts/${route.params.id}`)
  //       .then(response => {
  //         return {
  //           post: response.data,
  //           title: response.data.title,
  //         };
  //       });
  // }, 同じ内容をasync で書き換えてみる
  // async asyncData({ params }) {
  //   const response = await axios.get(`https://jsonplaceholder.typicode.com/posts/${params.id}`);
  //   return { 
  //     post: response.data,
  //     title: response.data.title
  //   };
  // }, 同じ内容をnuxt組み込みの@nuxt/axiosで書き換えてみる。
  async asyncData({ $axios, params }) {
    const post = await $axios.$get(`/posts/${params.id}`);
    return { post };
  },
  head() {
    return {
      title: this.post.title,
    };
  },
  // data() {
  //   return {
  //     post: {},
  //   };
  // },
  // mounted() {
  //   axios.get(`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`)
  //           .then(response => this.post = response.data);
  // },
};
</script>

<style>

</style>

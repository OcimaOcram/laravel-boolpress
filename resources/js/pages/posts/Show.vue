<template>
  <div class="container m-4">
      <h1 class="dark">{{ post.title }}</h1>
      <img class="img-fluid" :src="post.image" alt="">
      <p class="card-text bg-light mt-4" v-html="post.content"></p>
      <a href="/" class="btn btn-secondary">Back</a>
  </div>
</template>

<script>
import axios from "axios";
export default {
    data() {
        return {
            post: {}
        }
    },
methods: {
    async getPost() {
        try {
        const resp = await axios.get("/api/posts/" + this.$route.params.post);
        this.post = resp.data;
      } catch (er) {
        this.$router.replace({name: "error"})
      }
}
},
mounted() {
    this.getPost();
    console.log(this.post);
}
}

</script>

<style lang="scss" scoped>
</style>
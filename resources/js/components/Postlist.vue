<template>
  <div class="row">
      <Post v-for="(post,index) in posts" :key="index" :post="post"/>
    </div>
</template>

<script>
import Post from './Post.vue'
export default {
  name:"PostList",
  components:{
    Post
  },
  data(){
    return{
      posts:[]
    }
  },
  methods:{
    getPosts(){
      axios.get('http://localhost:8000/api/posts')
      .then(resp => {
        this.posts = resp.data.posts;
    })
    .catch((error)=>{
      console.warn(error);
    })
    }
  },
  created(){
    this.getPosts();
  }
}
</script>

<style scoped>

</style>
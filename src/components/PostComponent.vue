<template>
  <div>
      <form @submit="postData" method="post">
          <label for=""></label> <input type="text" placeholder="author" name="author" v-model="posts.author"> <br> <br>
          <label for=""></label> <input type="text" placeholder="title" name="title" v-model="posts.title"> <br> <br>
          <button type="submit">Post</button>
      </form>
  </div>
</template>

<script>
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'

Vue.use(VueAxios, axios)

export default {
    name: "PostComponent",
    data(){
        return {
            posts:{
                title:null,
                author:null
            }
        }

    },
    methods:{
        postData(e){
            // console.warn(this.posts)
            this.axios.post("http://localhost:3000/posts",this.posts)
            .then((result)=>{
                console.warn(result)
            })
            e.preventDefault();
                        
        }
    }
}
</script>

<style>

</style>
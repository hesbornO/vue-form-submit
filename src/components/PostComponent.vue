<template>
  <div>
      <form @submit="postData" method="post">
          <label for="author">Author: </label> 
          <input type="text" placeholder="author" name="author" v-model="posts.author"> <br> <br>
          
          <label for="title">Title: </label> 
          <input type="text" placeholder="title" name="title" v-model="posts.title"> <br> <br>
          
          <label for="production">Production year: </label> 
          <input type="text" placeholder="production" name="production_year" v-model="posts.release_data.production_year"> <br> <br>          
          
          <label for="publication-year">Publication year: </label> 
          <input type="text" placeholder="1998" name="publication_year" v-model="posts.release_data.publication.publication_year"> <br> <br>          
          
          <label for="production">Publication month : </label> 
          <input type="text" placeholder="" name="publication_month" v-model="posts.release_data.publication.publication_month"> <br> <br>          
          
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
                author:null,
                release_data:{
                    "production_year": null,
                    publication : {
                        publication_year: null,
                        publication_month: null
                    }
                }
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
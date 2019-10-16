<template>
  <div class="blog" id="blog">
    <div class="container">
      <div class="row justify-content-center">
        <h1>This is an Blog </h1>
      </div>
      <div class="row justify-content-center">
          <div class="col-md-3">
                  Title
          </div>
          <div class="col-md-3">
                  Content
          </div>
      </div>
      <div v-for="blog in blogs" :key="blog" >
        <div class="row justify-content-center" v-for="blg in blog" :key="blg">
          
          <div class="col-md-3 text-left">
              {{blg.title}}
          </div>
          <div class="col-md-3 text-left">
              {{blg.content}}
          </div>
        </div>
        
      </div>
    </div>  
  </div>
</template>


<script>
import axios from 'axios'
export default {
    name:'blog',
  data () {
    return {
      yourname: "septe",
      blogs: []
    };
  },
  async created() {
      try{
          const res = await axios.get(`http://nasution.dev/api/blog`);
          this.blogs = res.data
      }catch( e ){
          console.log(e)
      }
  },
}
</script>
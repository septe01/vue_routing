<template>
  <div class="blog" id="blog">
    <ul>
        <li v-for="blog in blogs" :key="blog.id">
            {{blog.name}}
        </li>
    </ul>
    
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
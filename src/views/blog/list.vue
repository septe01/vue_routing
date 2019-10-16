<template>
  <div class="blog" id="blog">
     
    <div class="container">
      <div class="row justify-content-center">
        <h1>This is an Blog </h1>
      </div>
      <div class="row justify-content-center">
          <div class="col-md-">
            <table class="table table-bordered">
              <thead>
                <tr>
                  <th>#</th>
                  <th>Title</th>
                  <th>Content</th>
                </tr>
              </thead>
              <tbody>
                <tr  v-for="(blog, index) in blogs" :key="blog.id">
                  <td >{{index + 1}}</td>
                  <td class="text-left">{{blog.title}}</td>
                  <td class="text-left">{{blog.content}}</td>
                </tr>
              </tbody>
            </table>
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
          this.blogs = res.data.data
      }catch( e ){
          console.log(e)
      }
  },
}
</script>
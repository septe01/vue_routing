<template>
  <div class="task" >
    
    <div class="container">
      <div class="row justify-content-center">
        <h1>This is an task </h1>
      </div>
      <div class="row justify-content-center">
          <div class="col-md-">
            <table class="table table-bordered">
              <thead>
                <tr>
                  <th>#</th>
                  <th>Nama</th>
                  <th>Description</th>
                </tr>
              </thead>
              <tbody>
                <tr  v-for="(task, index) in Tasks" :key="task.id">
                  <td >{{index + 1}}</td>
                  <td class="text-left">{{task.name}}</td>
                  <td class="text-left">{{task.description}}</td>
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
    name:'task',
  data () {
    return {
      yourname: "septe",
      Tasks: []
    };
  },
  async created() {
      try{
          const res = await axios.get(`http://nasution.dev/api/tasks`);
          this.Tasks = res.data
      }catch( e ){
          console.log(e)
      }
  },
}
</script>
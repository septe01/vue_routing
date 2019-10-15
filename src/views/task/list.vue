<template>
  <div class="task" >
    <h1>This is an task page</h1>
    <ul>
        <li v-for="task in Tasks" :key="task.id">
            {{task.name}}
        </li>
    </ul>
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
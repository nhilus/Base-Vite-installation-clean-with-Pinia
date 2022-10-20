<template>
  <div>
    <TaskList/>
  </div>


</template>

<script>
import {RouterView, RouterLink} from 'vue-router'
import TaskList from './components/TaskList.vue';

  export default {
    components: { TaskList,
                  RouterLink,
                  RouterView, }
}

</script>



<style scoped>

</style>

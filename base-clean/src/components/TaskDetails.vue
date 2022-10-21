<template>
    <div class="task">
        <input v-model = task.title type="text" :disabled="task.disabled">
        <div class="icons">
        <i 
            class="material-symbols-outlined"
            @click="task.disabled = !task.disabled"
        >edit</i>
        <i 
            class="material-symbols-outlined"
            :class="{ disable: task.isComp}"
            @click="taskStore.deleteTask(task.id)"
        >delete</i>
        <i 
        class="material-symbols-outlined"
        :class="{active:task.isComp}"
        @click="taskStore.toggleComplete(task.id)"
        >check_circle</i>
        </div>
    </div>
</template>

<script>
import { useTaskStore } from '../stores/TaskStore';
import {ref} from 'vue'

    export default {
        props:['task'],

        setup(){
            const taskStore = useTaskStore()

            return {taskStore}
        }

    }
</script>

<style scoped>

.disable{
   cursor: not-allowed;
   pointer-events: none;
}

</style>
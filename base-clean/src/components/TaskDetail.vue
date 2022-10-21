<template>
    <div>
        <h1>{{this.getTask($route.params.id)}}</h1>

        <div class="task">
        <input v-model = task.title type="text" :disabled="task.disabled">
        <div class="icons">
        <i 
            class="material-symbols-outlined"

            :class="{ isActive: !task.disabled}"
            @click="task.disabled = !task.disabled"
        >edit</i>
        <i 
            class="material-symbols-outlined"
            :class="{ disable: task.isComp}"
            id="delete"
            @click="deleteTask(task.id)"
        >delete</i>
        <i 
        class="material-symbols-outlined"
        :class="{active:task.isComp}"
        @click="toggleComplete(task.id)"
        >check_circle</i>
        </div>
        </div>


    </div>
</template>

<script>
import { mapActions } from 'pinia';
import { useTaskStore } from '../stores/TaskStore';

    export default {

        data(){
            return{
                task: this.getTask(this.$route.params.id)
            }
        },
        
        methods:{
            ...mapActions(useTaskStore, ["getTask", "toggleComplete", "deleteTask"])
        },

        computed:{
            
        }

        
    }
</script>

<style scoped>

.disable{
   cursor: not-allowed;
   pointer-events: none;
   color:red;
}

.isActive{
    color:goldenrod;
}

.material-symbols-outlined { font-size: 24px; }

</style>
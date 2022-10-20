<template>
    <div class="task">
        <input v-model = task.title type="text" :disabled="task.disabled">
        <button>
            <RouterLink to="/details" class="link">Detalhes</RouterLink>
        </button>
    </div>
    <RouterView />
</template>

<script>
import {RouterView, RouterLink} from 'vue-router'

import { useTaskStore } from '../stores/TaskStore';

    export default {
        components: {
            RouterLink,
            RouterView,
        },

        props:['task'],

        setup(){
            const taskStore = useTaskStore()


            return {taskStore}
        }

    }
</script>

<style scoped>

</style>
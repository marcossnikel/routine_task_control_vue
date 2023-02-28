<template>
<BoxContainer>
    <div class="columns">
        <div class="column is-7">
            {{ task.description || 'NO__DESCRIPTION__PROVIDED' }}
        </div>
        <div class="column">
            <TaskTimer :timeSeconds="task.secondsDuration"/>
        </div>
    </div>
</BoxContainer>
</template>

<script lang="ts">
import { defineComponent, PropType} from 'vue';
import TaskTimer from './TaskTimer.vue'
import ITask from '@/interface/ITask';
import BoxContainer from './BoxContainer.vue';
export default defineComponent({
    name: 'TaskContainer',
    components:{
        TaskTimer,
        BoxContainer
    },
    props:{
        task:{
            type: Object as PropType<ITask>,
            required : true
        },
    }
})
</script>

<style scoped>
</style>
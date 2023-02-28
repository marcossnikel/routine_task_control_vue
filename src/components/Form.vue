<template>
  <div class="box task-form">
    <div class="columns">
      <div class="column is-8" role="form" aria-label="New Task Form">
        <input
          type="text"
          class="input"
          placeholder="which task do you want to start ?"
          v-model="taskDescription"
        />
      </div>
      <div class="column">
        <TimerContainer @whenTimerIsFinished="finishTask"/>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TimerContainer from './TimerContainer.vue'

export default defineComponent({
  name: "FormRegister",
  emits: ['whenTaskIsSaved'],
  data:() => ({
    taskDescription: ''
  }),
  components:{
    TimerContainer,
  },
  methods:{
    finishTask(timeSeconds : number) : void{
        this.$emit('whenTaskIsSaved',{
          secondsDuration : timeSeconds,
          description : this.taskDescription
        })
        this.taskDescription = ''
    }
  }
});
</script>

<style>
.task-form{
  color: var(--text-primary);
  background-color: var(--bg-primary);
}
</style>
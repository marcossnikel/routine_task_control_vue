<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <TaskTimer :timeSeconds="timeSeconds" />
    <ButtonActions :enabled="runningTimer" buttonText="start" icon="fas fa-play" @click="start"/>
    <ButtonActions :enabled="!runningTimer" buttonText="stop" icon="fas fa-stop" @click="stop"/>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TaskTimer from './TaskTimer.vue'
import ButtonActions from "./ButtonActions.vue";
export default defineComponent({
  name: "TimerContainer",
  emits: ['whenTimerIsFinished'],
  components:{
    TaskTimer,
    ButtonActions
  },
  data : () => ({
    timeSeconds: 0,
    counter: 0,
    timer: 0,
    runningTimer: false
  }),

  methods: {
    start(){
       this.runningTimer = true
       this.timer = setInterval(() =>{
            this.timeSeconds += 1
        }, 1000)
    },
    stop(){
        this.runningTimer = false
        clearInterval(this.timer)
        this.$emit('whenTimerIsFinished',this.timeSeconds)
        this.timeSeconds = 0
    }
  }
});
</script>

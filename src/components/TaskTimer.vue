<template>
  <section>
    <strong class="time--display">{{ timePassed }}</strong>
  </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'TaskTimer',
    props:{
        timeSeconds: {
            type: Number,
            default: 0
        }
    },
    computed:{
    //monitora x info e se atualiza com base nisso
    timePassed() : string {
        return new Date(this.timeSeconds * 1000).toISOString().substring(11,19)
    }
  },
})

</script>

<style>
.time--display{
  color: var(--text-primary); 
}
</style>
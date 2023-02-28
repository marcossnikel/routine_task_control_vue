<template>
    <button class="button" :disabled="enabled">
      <span class="icon">
        <i :class="icon"></i>
      </span>
      <span>{{ buttonText }}</span>
    </button>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'ButtonActions',
    props:{
        enabled:{
            type: Boolean,
            default: false
        },
        icon:{
            type:String,
            default: ""
        },
        buttonText:{
            type: String,
            default: ""
        }
    }
})
</script>
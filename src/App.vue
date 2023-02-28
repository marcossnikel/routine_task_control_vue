<template>
  <main class="columns is-gapless is-multiline" :class="{'dark-mode': darkMode}">
    <div class="column is-one-quarter">
      <SideBar @onThemeChanged="changeTheme"/>
    </div>
    <div class="column is-three-quarter content">
      <FormRegister @whenTaskIsSaved="saveTask"/>
      <div class="list">
        <TaskContainer v-for="(task,index) in tasks" :key="index" :task="task"/>
      <BoxContainer v-if="listIsEmpty">
        Any task provided yet , go to work !!! :(
      </BoxContainer>
      </div>

    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import FormRegister from './components/Form.vue'
import SideBar from "./components/SideBar.vue"
import TaskContainer from './components/TaskList.vue'
import ITask from "./interface/ITask";
import BoxContainer from "./components/BoxContainer.vue";
export default defineComponent({
  name: "App",
  components:{
    SideBar,
    FormRegister,
    TaskContainer,
    BoxContainer
  },
  data: () => ({
    tasks: [] as ITask[],
    darkMode: false
  }),
  computed:{
    listIsEmpty() : boolean{
      return this.tasks.length === 0
    }
  },
  methods:{
    saveTask(task: ITask){
      this.tasks.push(task)
    },
    changeTheme(darkModeActivated : boolean){
      this.darkMode = darkModeActivated
    }
  }
});
</script>

<style>
main{
--bg-primary: #fff;
--text-primary: #000;
}

main.dark-mode{
  --bg-primary: #2b2d42;
--text-primary: #ddd;
}

.content{
  background-color: var(--bg-primary);
}
.list{
    padding: 1.25rem;
}
</style>
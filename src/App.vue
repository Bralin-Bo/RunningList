
<template>
  <div class="container">
    <h1 class="title">Welcome back <span>Bo</span>!</h1>
    <Additionalmenu :addTask="addTask"/>
    <div class="tasks-box" v-bind:key="task.id" v-for="task in tasks">
      <Task :name="task.name" :checked="task.checked" :id="task.id" @changingName="changingName" @changeChecked="changeChecked"/>
    </div>
    <button @click="clear">Clear</button>
  </div>
</template>


<script>
import Task from './components/Task.vue'
import Additionalmenu from './components/Additionalmenu.vue'
export default{
  components:{ Task, Additionalmenu },
  created(){
    document.addEventListener("DOMContentLoaded", this.load)
    window.addEventListener('beforeunload', this.save)
  },
  data(){
    return{
      tasks:[
        {id:1, name:"", checked: [false,false,false,false,false,false,false]}
      ]
    };
  },
  methods:{
    addTask(){
      this.tasks.push({id:Date.now(), name:"", checked:[false,false,false,false,false,false]})
    },
    changingName(id, name){
      this.tasks.forEach(task => {
        if(task.id == id){
          task.name = name;
          if(task.name.length === 0){
            this.tasks = this.tasks.filter(oldtask => oldtask.name !== task.name)
          }
        }
      });
      this.save()
    },
    changeChecked(id, i, value){
      this.tasks.forEach(task => {
        if(task.id == id){
          task.checked[i-1]=value;
        }
      })
      this.save()
    },
    save(){
      localStorage.setItem('tasks', JSON.stringify(this.tasks))
    },
    load(){
      this.tasks = JSON.parse(localStorage.getItem('tasks'));
      if (this.tasks == null) {
        this.tasks = [{id:1, name:"", checked: [false,false,false,false,false,false,false]}]
      }       
    },
    clear(){
      localStorage.clear()
      this.save()
    }
  }
}
</script>
<style lang="sass">
  .container
    max-width: 1200px
    margin: 0 auto
    text-align: center
  .title
    font-size: 74px
    margin: 0
    span
      font-weight: bold
      color: purple
      text-shadow: 1px 1px 10px purple
</style>
  

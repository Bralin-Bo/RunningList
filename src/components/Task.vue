<template>
   <div class="task-container">
      <textarea 
         type="text" class="task" 
         v-model="name" @input="autoSize($event)" @change="changeName"
         placeholder="Name">
      </textarea>
      <!--  -->
      <div class="checkboxes" :key="i" v-for="i in 7">
         <Checkbox :check="checked[i-1]" :index="i" @changeCheck="changeCheck"/>
      </div>
   </div>
</template>

<script>
import Checkbox from './checkbox.vue';
export default {
    props:{
      name:{},
      checked:{},
      id:{}
    },
    methods: {
        autoSize: function (e) {
            e.target.style.height = "5px";
            e.target.style.height = (e.target.scrollHeight) + "px";
        },
        changeName(){
          this.$emit('changingName', this.id, this.name);
        },
        changeCheck(i, value){
          this.$emit('changeChecked', this.id, i, value)
        },
        changeCheckaa(i, value){
          this.checked[i-1] = value;
          this.$emit('changeChecked', this.id, this.checked)
        }
    },
    components: { Checkbox }
}
</script>

<style lang="sass" scoped>
.task-container
   display: flex
   max-width: 1000px
   margin: 0 auto
   text-align: center
.task
   height: 65px
   max-width: 300px
   font-size: 40px
   padding: 10px
   border: none
   resize: none
   overflow: hidden
   text-align: right

</style>
<style>
.check-container {
  position: relative;
  padding-left: 63px;
  margin-bottom: 12px;
  cursor: pointer;
  font-size: 22px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

/* Hide the browser's default checkbox */
.check-container input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
}

/* Create a custom checkbox */
.checkmark {
  position: absolute;
  top: 0;
  left: 0;
  height: 60px;
  width: 60px;
  background-color: #eee;
}

/* On mouse-over, add a grey background color */
.check-container:hover input ~ .checkmark {
  background-color: #ccc;
}

/* When the checkbox is checked, add a blue background */
.check-container input:checked ~ .checkmark {
  background-color: #2196F3;
}

/* Create the checkmark/indicator (hidden when not checked) */
.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}

/* Show the checkmark when checked */
.check-container input:checked ~ .checkmark:after {
  display: block;
}

/* Style the checkmark/indicator */
.check-container .checkmark:after {
  left: 9px;
  top: 5px;
  width: 5px;
  height: 10px;
  border: solid white;
  border-width: 0 3px 3px 0;
  -webkit-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  transform: rotate(45deg);
}
</style>
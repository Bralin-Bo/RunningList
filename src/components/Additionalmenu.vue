<template>
  <div class="additional-menu">
      <button class="btn" @click="addTask()">Add</button>
      <div class="week">
        <h3>M</h3>
        <h3>T</h3>
        <h3>W</h3>
        <h3>T</h3>
        <h3>F</h3>
        <h3>S</h3>
        <h3>S</h3>
      </div>
   </div>
</template>

<script>
export default {
   props:{
      addTask:{}
   }
}
</script>

<style lang="sass">
.additional-menu
   display: flex
   justify-content: space-between
   max-width: 600px
   margin: 0 auto
.btn
   align-self: center
   border: 2px solid gray
   border-radius: 5px
   background-color: transparent
   font-size: 20px
   padding: 15px
   text-transform: uppercase
   transition: .4s
   &:hover
      cursor: pointer
      background-color: gray
      color: white
   &:active
      background-color: black
.week
   display: flex
   margin-right: 30px
h3
   display: block
   box-sizing: border-box
   width: 60px
   margin-right: 5px
   font-size: 30px
   color: #000000

</style>
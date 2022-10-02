<template>
  <label class="check-container">
      <input type="checkbox" v-model="check" @change="changeCheck">
      <span class="checkmark"></span>
   </label>
</template>


<script>
export default {
   props:{
      check:{default: false},
      index:{}
   },
   methods:{
      changeCheck(){
         this.$emit("changeCheck", this.index, this.check)
      }
   }
}
</script>

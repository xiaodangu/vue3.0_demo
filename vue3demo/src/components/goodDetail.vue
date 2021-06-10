<template>
  <div></div>
</template>
<script>
export default {
  props:{
    dName:{
      type:String,
      default:''
    }
  },
  methods:{
    changNum(){
      this.dName="改变了！"
      console.log(this.dName)
    }
  }
}
</script>
<style scoped>

</style>
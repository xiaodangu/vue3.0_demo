<template>
  <div>
    <span>新蜂超市</span>
    <div v-for="item in dataList" :key="item">
      <span @click="getDetail(item.categoryName)">{{item.categoryName}}</span>
      <!-- <span>{{type}}</span>
      <span>{{age}}</span> -->
    </div>
    <span>{{name}}</span>
    <button @click="getNum()">点击</button>
    <good-detail :dName="'姓名'" ref="goodDetail"></good-detail>
  </div>
</template>
<script>
import { reactive, onMounted, toRefs } from 'vue'
import { getCategory } from '@/service/good'
import goodDetail from '@/components/goodDetail'
export default{
  components: { goodDetail },
  //请求数据的接口声明为异步不会阻碍进程
  setup(){
    const state = reactive({
      name: '姓名',
      type: '',
      age: '',
      dataList:[]
    })
    onMounted(async()=>{
      let data = await getCategory()
      console.log(data)
      state.dataList = data.data
    })
    const getDetail = (val) => {
      console.log(val)
    }
    const getNum = async() => {
      console.log(this.$refs.goodDetail.changeNum)
    }
    return{
      ...toRefs(state),
      getDetail,
      getNum
    }
  }
}
</script>
<style scoped>

</style>

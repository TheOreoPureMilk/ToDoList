<template>
  <div id="app">
    <div class="input"><input_item @submit_item="handleSubmit"></input_item></div>
    <div class="table"><table_item :table_data='data' @delete="deleteRow"></table_item></div>
  </div>
</template>

<script>
import input_item from './components/input.vue'
import table_item from './components/table.vue'

export default {
  components:{
    input_item,
    table_item
  },
  data(){
    return{ 
      data:[],
      is_done:[],
      unDOne:[]
    }
  },
  methods:{
    handleSubmit(item){
      this.data.splice(1,0,item)
      let Data = {
        strData: this.data
      }
      let json_data = JSON.stringify(Data)
      localStorage.setItem("datas",json_data)
    },
    getItems(){
      if (localStorage.getItem("datas"))
      {
        let str_data = localStorage.getItem("datas")
        // eslint-disable-next-line
        console.log(str_data)
        let Data = JSON.parse(str_data)
        this.data = Data.strData
      }
    },
    deleteRow(index){
      alert("刪除成功")
      this.data.splice(index,1)
      let Data = {
        strData: this.data
      }
      let json_data = JSON.stringify(Data)
      localStorage.setItem("datas",json_data)
    },
  },
  mounted(){
    this.getItems()
  }
}
</script>

<style>
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  width: 100%;
}

.input {
  width: 80%
}

.table {
  width: 80%
}
</style>

<template>
  <div id="app">
    <div class="input">
      <input_item 
      @submit_item="handleSubmit">
      </input_item>
    </div>
    <div class="lable">未完成的</div>
    <div class="table">
      <table_item 
      :table_data='data'
      @thingDone="complete"
      @edit="editThing"
      @delete="deleteRow">
      </table_item>
    </div>
    <div class="lable">已完成的</div>
      <div class="table">
        <table_item 
        :table_data='is_done'
        @thingDone="cancle_complete"
        @edit="edit_is_done"
        @delete="delete_is_done">
        </table_item>
      </div>
  </div>
</template>

<script>
import input_item from './components/input.vue'
import table_item from './components/EditableTable.vue'

export default {
  components:{
    input_item,
    table_item
  },
  data(){
    return{ 
      data:[],
      is_done:[]
    }
  },
  methods:{
    handleSubmit(item){
      this.data.splice(1,0,item)
      this.sendthing(this.data, "datas")
    },
    sendthing(send_data, name){
      let Data = {
        strData: send_data
      }
      let json_data = JSON.stringify(Data)
      localStorage.setItem(name, json_data)
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
      if (localStorage.getItem("isdone"))
      {
        let str_data = localStorage.getItem("isdone")
        // eslint-disable-next-line
        console.log(str_data)
        let Data = JSON.parse(str_data)
        this.is_done = Data.strData
      }
    },
    deleteRow(index){
      alert("刪除")
      this.data.splice(index,1)
      this.sendthing(this.data, "datas")
    },
    delete_is_done(index){
      alert("刪除")
      this.is_done.splice(index,1)
      this.sendthing(this.is_done, "isdone")
    },
    editThing(thing){
      this.data = thing
      this.sendthing(this.data, "datas")
    },
    edit_is_done(thing){
      this.is_done = thing
      this.sendthing(this.is_done, "isdone")
    },
    complete(index){
      let item = this.data[index]
      this.is_done.splice(1,0,item)
      this.sendthing(this.is_done, "isdone")

      this.data.splice(index,1)
      this.sendthing(this.data, "datas")
    },
    cancle_complete(index){
      let item = this.is_done[index]
      this.data.splice(1,0,item)
      this.sendthing(this.data, "datas")

      this.is_done.splice(index,1)
      this.sendthing(this.is_done, "isdone")
    }
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

.lable {
  margin-top: 20px;
  width: 50%;
  color:rgb(22, 230, 202);
}

.input {
  width: 80%;
}

.table {
  margin-top: 20px;
  width: 80%
}
</style>

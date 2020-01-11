<template>
  <div class="card">
  <div class="Aitem" v-for="(item, index) in table_data"  @keyup="edit" :key="index">
    <div class="sequence">
      <span>
        {{ index+1 }}
      </span>
    </div>
    
    <div class="names">
      <span>
        <input v-model="item.items" type="text" value="item.items">
      </span>
    </div>
    
    <div class="ddl">
      <span>
        <input v-model="item.ddl" type="text" value="item.ddl">
      </span>
    </div>
    
    <div class="description">
      <span>
        <input  v-model="item.description" type="text" value="item.description">
      </span>
    </div>

    <div class="delete">
      <span>
        <el-button size="small" @click="deleteRow(index)">删除</el-button>
      </span>
    </div>

  </div>
  </div>
</template>

<script>
export default {
  name:'table_item',
  props:['table_data'],
  methods:{
    deleteRow(index){
      this.$emit("delete",index)
    },
    edit(){
      this.$emit("edit",this.table_data)
    }
  },
}
</script>

<style>
  .card {
    display: flex;
    justify-content: space-around;
    align-content: center;
    flex-wrap: wrap;

    width: 80%;
  }

  .Aitem {
    display: flex;
    justify-content: space-between;
    align-content: center;

    height: 25px;
  }

  .sequence, .names, .ddl, .description {
    display: flex;
    justify-content: center;
    align-content: center;
    
    width: 20%;
    height: 100%;
  }

  span {
    display: flex;
    align-content: center;

    width: 100%
  }
  
  input {
    width: 100%;
    height: 90%;

    border:none;
  }
</style>
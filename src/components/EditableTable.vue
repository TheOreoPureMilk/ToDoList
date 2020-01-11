<template>
  <div class="card">
    
    <div class="sequence">
      <span v-for="(index) in table_data" :key="index">
        <input type="text" value="index+1">
      </span>
    </div>
    
    <div class="names">
      <span v-for="(index, item)in table_data" :key="index">
        <input v-model="item.items" type="text" value="item.items">
      </span>
    </div>
    
    <div class="ddl">
      <span v-for="(index, item)in table_data" :key="index">
        <input v-model="item.ddl" type="text" value="item.ddl">
      </span>
    </div>
    
    <div class="description">
      <span v-for="(index, item)in table_data" :key="index">
        <input v-model="item.description" type="text" value="item.description">
      </span>
    </div>

    <div class="delete">
      <span v-for="(index) in table_data" :key="index">
        <el-button @click="deleteRow(index)"></el-button>
      </span>
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
    }
  }
}
</script>

<style>
  .card {
    display: flex;
    justify-content: space-between;
    align-content: center;

    width: 80%;
  }

  .sequence, .names, .ddl, .description {
    display: flex;
    justify-content: center;
    align-content: center;
    
    width: 20%
  }
  
  input {
    border:none;
  }
</style>
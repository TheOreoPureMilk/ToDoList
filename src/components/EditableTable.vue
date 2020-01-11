<template>
  <div class="card">
  <div class="Aitem">
    <div class="sequence">
      <span class="item_span">
        序号
      </span>
    </div>
    
    <div class="names">
      <span class="item_span">
        名称
      </span>
    </div>
    
    <div class="ddl">
      <span class="item_span">
        截止日期
      </span>
    </div>
    
    <div class="description">
      <span class="item_span">
        描述
      </span>
    </div>
  </div>
  <div class="Aitem" v-for="(item, index) in table_data"  @keyup="edit" :key="index">
    <div class="sequence">
      <span class="item_span">
        {{ index+1 }}
      </span>
    </div>
    
    <div class="names">
      <span class="item_span">
        <input v-model="item.items" type="text" value="item.items">
      </span>
    </div>
    
    <div class="ddl">
      <span class="item_span">
        <input v-model="item.ddl" type="text" value="item.ddl">
      </span>
    </div>
    
    <div class="description">
      <span class="item_span">
        <input  v-model="item.description" type="text" value="item.description">
      </span>
    </div>
    <div class="function">
      <span>
        <el-button size="mini" @click="deleteRow(index)">删除</el-button>
      </span>
      <span>
        <el-button size="mini" @click="done(index)">switch</el-button>
      </span>
    </div>
  </div>
  </div>
</template>

<script>
export default {
  name:'table_item',
  props:['table_data'],
  data(){
    return {
      numbers:0
    }
  },
  methods:{
    deleteRow(index){
      this.$emit("delete",index)
    },
    edit(){
      this.$emit("edit",this.table_data)
    },
    done(index){
      this.$emit('thingDone',index)
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

  .head {
    width: 100%
  }
  
  .head_span {
  }

  .Aitem {
    display: flex;
    justify-content: space-between;
    align-content: center;

    width: 100%;
    height: 25px;
  }

  .sequence, .names, .ddl, .description {
    display: flex;
    justify-content: center;
    align-content: center;
    
    width: 18%;
    height: 100%;
  }

  p {
    width:150px
  }

  .item_span {
    display: flex;
    align-content: center;

    text-align: left;

    width: 100%
  }
  
  input {
    width: 100%;
    height: 90%;

    border:none;
  }

</style>
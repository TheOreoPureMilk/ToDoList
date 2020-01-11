<template>
  <div>
    <el-table :data="table_data" style="width:100%">
      <el-table-column label="序号">
        <template slot-scope="scope">
          {{scope.$index+1}} 
        </template>
      </el-table-column>
      <el-table-column prop="items" label="项目" width="300px"></el-table-column>
      <el-table-column prop="ddl" label="截止日期" width="180px"></el-table-column>
      <el-table-column prop="description" label="描述" ></el-table-column>
      <el-table-column>
        <template slot-scope="scope">
          <el-button
          size="mini"
          @click="handleEdit(scope.$index)">编辑</el-button>
          <el-button
          size="mini"
          type="danger"
          @click="deleteRow(scope.$index)">删除</el-button>
        </template>
      </el-table-column>
    </el-table>
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
  
</style>
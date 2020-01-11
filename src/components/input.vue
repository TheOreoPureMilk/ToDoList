<template>
  <div>
    <el-card>
      <el-input v-model="items" class='input-item' placeholder="项目名称" />
      <el-input v-model="ddl" class='input-item' placeholder="截止日期" />
      <el-input v-model="description" class='input-item' placeholder="描述" />
      <el-button @click="handleSubmit()" type="primary">提交</el-button>
    </el-card>
  </div>
</template>

<script>
export default {
  name:'input_item',
  data(){
    return {
      items:'',
      ddl:'',
      description:'',
    }
  },
  methods:{
    handleSubmit(){
      let Anew_item = {
        items:this.items,
        ddl:this.ddl,
        description:this.description,
      }
      this.$emit('submit_item',Anew_item)
      this.clear()
    },
    clear(){
      this.items = ""
      this.ddl = ""
      this.description = ""
    },
  }
}

</script>

<style>

</style>
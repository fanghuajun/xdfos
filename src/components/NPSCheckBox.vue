<template>
  <div>
      <div class="title">{{question.title}}</div>
       <el-checkbox-group v-model="selectList">
        <template v-for="item in question.items">
          <el-checkbox :key="item.value">{{item.text}}</el-checkbox>
        </template>
       </el-checkbox-group>
  </div>

</template>
<script>
export default {
  name:'NPSCheckBox',
  props:{
    question:Object
  },
  data(){
    return {
      selectList:null
    }
  }

}
</script>


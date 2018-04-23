<template>
  <div>
    <div>{{question.title}}
        <span style="color:#FF8C00;font-family:microsoft yahei">{{question.remark}}</span>
        <el-input v-model="answers" 
        type="textarea"
        :rows="4"></el-input>
    </div>
  </div>

</template>
<script>
import Vue from 'vue';
import Element from 'element-ui';
import 'element-ui/lib/theme-chalk/index.css';
Vue.use(Element);
export default {
  name:'QandA',
  props:{
      question:Object
  },
  data(){
      return {
          answers:""
      }
  }
}
</script>


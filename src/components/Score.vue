<template>
  <div id="socre">
    <div class="title">{{question.title}}</div>
    <img src="../assets/scop.png"/>
    <div>
      <el-radio-group v-model="selectScope">
        <el-radio-button v-for="item in question.items" :key="item" :label="item"/>
      </el-radio-group>
    </div>
    <qand-a v-if="selectScope<=question.showQandACondition" :question="question.question"/>
  </div>
</template>

<script>
import Vue from 'vue';
import Element from 'element-ui';
import 'element-ui/lib/theme-chalk/index.css';
Vue.use(Element);
import QandA from './QandA';

export default {
  name: 'Socre',
  props:{
    question:Object,
  },
  data () {
    return {
     selectScope:10
    }
  },
  components:{
      QandA
  }
}
</script>
<style>

</style>



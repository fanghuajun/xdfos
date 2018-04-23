<template>
 <div>
      <div class="title">{{question.title}}</div>
       <el-radio-group v-model="value" @change="valuechange">
         <template v-for="item in question.items" >
           <el-radio :label="item.value" :key="item.value">{{item.text}}</el-radio>
        </template>
        <el-radio v-if="question.needOther" label="99" key="99" >其他
          <el-input v-if="value==='99'" v-model="otherText" placeholder="请输入内容" @focus="changeselect('99')"></el-input>
        </el-radio>
      </el-radio-group>

  </div>

</template>
<script>
export default {
  name:'NPSRadio',
  props:{
    question:Object
  },
  data(){
    return {
      value:"1",
      otherText:"",
      isSelectOther:false
    }
  },
  methods:{
    changeselect:function(v){
      this.value=v;
    },
    valuechange:function(value){
      console.log("qvaluechange");
      this.$emit("qvaluechange",this.question,value);
    }
  }

}
</script>

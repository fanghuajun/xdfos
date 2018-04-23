<template>
  <div id="sign">
    <p>同学/同学家长您好！ 感谢您选择新东方前途出国。我们一直致力于留学服务体验的不断提升，
          您的意见对我们来说非常重要。调查问卷将严格保密，谢谢您的支持和理解！</p>
    <br>
    <template v-for="que in questions">
        <score v-if="que.type === 'score'" :question="que" :key="que.id"/>
        <n-p-s-radio v-if="que.type === 'signselect'" 
            :question="que" :key="que.id" 
            @qvaluechange="qvaluechange"
            v-show="isshow(que.condtion)"/>
        <qand-a v-if="que.type === 'qanda'" :question="que" :key="que.id"/>
        <n-p-s-check-box v-if="que.type === 'mulselect'" :question="que" :key="que.id"/>
    </template>
    <p>为了方便以后更好的为您服务，需要您回答以下几个问题，再次感谢您的支持和理解！</p>
    <template v-for="stu in stuInfo">
        <score v-if="stu.type === 'score'" :question="stu" :key="stu.id"/>
        <n-p-s-radio v-if="stu.type === 'signselect'" 
            :question="stu" :key="stu.id" 
            @qvaluechange="qvaluechange"
            v-show="isshow(stu.condtion)"/>
        <qand-a v-if="stu.type === 'qanda'" :question="stu" :key="stu.id"/>
        <n-p-s-check-box v-if="stu.type === 'mulselect'" :question="stu" :key="stu.id"/>
    </template>
  </div>

</template>

<script>
import Score from '@/components/Score'
import NPSRadio from '@/components/NPSRadio'
import QandA from '@/components/QandA'
import NPSCheckBox from '@/components/NPSCheckBox'
import Vue from 'vue'
// import { Vue } from 'vue/types/vue';
export default {
    name: 'Sign',
    methods:{
        qvaluechange(question,value){
             Vue.set(this.model,question.prop,value);
        },
        isshow(condtion){
            if(condtion==null || condtion==""){
                return true;
            }
            let ishow=eval(condtion);
            return ishow;
        }
        
    },
    data () {
      return {
        model:{q6:"2"},
        stuInfo:[{
            id:'s1',
            prop:'s1',
            type:'signselect',
            title:"1您方便沟通联系的方式是？ ",
            items:[
               {value:1,text:"电话"},
               {value:2,text:"面谈"},
               {value:3,text:"微信"},
               {value:4,text:"邮件"},
               { value:5,text:"QQ"},
               {value:6,text:"以上均可"},
               {value:7,text:"沟通频次"},
               {value:8,text:" 材料准备"},
            ],
        },{
            id:'s2',
            prop:'s2',
            type:'signselect',
            title:"2.您觉得比较理想沟通的频次",
            items:[
               {value:1,text:"每天/次电话"},
               {value:2,text:"每周/次"},
               {value:3,text:"半个月/次"},
               {value:4,text:"每月/次"},
               { value:5,text:"有问题随时联系"}
            ],
        },{
            id:'s3',
            prop:'s3',
            type:'signselect',
            title:"3.您方便联系的时间段是？",
            items:[
               {value:1,text:"工作日"},
               {value:2,text:"周末"},
               {value:3,text:"早上"},
               {value:4,text:"中午"},
               { value:5,text:"晚上"},
               { value:6,text:"随时"}
            ],
        },{
            id:'s4',
            prop:'s4',
            type:'signselect',
            title:"4.您能接受最长的回复时间是？",
            items:[
               {value:1,text:"2小时以内"},
               {value:2,text:"6小时以内"},
               {value:3,text:"12小时以内"},
               {value:4,text:"24小时以内"},
               { value:5,text:"48小时以内"}
            ],
        },{
            id:'s5',
            prop:'s5',
            type:'signselect',
            title:"5.后续留学事宜主要联系人",
            items:[
               {value:1,text:"学生本人"},
               {value:2,text:"家长"},
               {value:3,text:"学生&家长"}
            ],
        },{
            id:'s6',
            prop:'q1',
            type:'qanda',
            title:"6.如您对服务有其他建议，请说明具体原因，我们将竭力改进！",
             value:'',
             remark:"（反馈内容将严格保密，请放心填写！非必填）"
        },
        
        ],
        questions:[{
            id:'1',
            prop:'q1',
            type:'score',
            title:"1.您有多大可能向您的亲朋好友推荐新东方前途的出国留学服务？请打分!",
            items:[1,2,3,4,5,6,7,8,9,10],
            question:{
                value:'',
                title:"您打（0-6分）不会推荐的原因是？",
                remark:"（反馈内容将严格保密，请放心填写！必填）"
            },
            showQandACondition:6
        },
        {
            id:'2',
            prop:'q2',
            type:'signselect',
            title:"2.您是根据以下哪个原因给出上题的分数？(单选)",
            items:[
               {value:1,text:"服务态度"},
               {value:2,text:"选校申请"},
               {value:3,text:"服务价格"},
               {value:4,text:"专业知识"},
               { value:5,text:"签证辅导"},
               {value:6,text:"服务流程"},
               {value:7,text:"沟通频次"},
               {value:8,text:" 材料准备"},
               {value:9,text:"合作机构"},                
               {value:10,text:"工作衔接"},
               {value:11,text:"留学规划"},
               {value:12,text:"境外服务"},
               {value:13,text:"人员配置"},
               {value:14,text:"录取结果"},
               {value:15,text:"品牌知名度"},
               {value:16,text:"个性化指导"},
               {value:17,text:" 服务效率"},
               {value:18,text:"背景提升"}               
               ],
               needOther:true
        }, {
            id:'3',
            prop:'q3',
            type:'signselect',
            title:"3.您最希望新东方前途在哪些方面有所提升？(单选)",
            items:[
               {value:1,text:"服务态度"},
               {value:2,text:"选校申请"},
               {value:3,text:"服务价格"},
               {value:4,text:"专业知识"},
               { value:5,text:"签证辅导"},
               {value:6,text:"服务流程"},
               {value:7,text:"沟通频次"},
               {value:8,text:" 材料准备"},
               {value:9,text:"合作机构"},                
               {value:10,text:"工作衔接"},
               {value:11,text:"留学规划"},
               {value:12,text:"境外服务"},
               {value:13,text:"人员配置"},
               {value:14,text:"录取结果"},
               {value:15,text:"品牌知名度"},
               {value:16,text:"个性化指导"},
               {value:17,text:" 服务效率"},
               {value:18,text:"背景提升"}               
               ],
               needOther:true
        },{
            id:'4',
            prop:'q4',
            type:'signselect',
            title:"4.前期申请服务（请对前期老师的选校面谈、院校信息、沟通效率进行打分  ）",
            items:[
               {value:1,text:"9~10分（满意）"},
               {value:2,text:"7~8分(一般）"},
               {value:3,text:"0~6分（不满意）"}    
               ],
               needOther:false
        },{
            id:'6',
            prop:'q6',
            type:'signselect',
            title:"6.签约后老师联系您的次数（1-2月内）",
            items:[
               {value:1,text:"0次"},
               {value:2,text:"1-2次"},
               {value:3,text:"3-5次"},
               {value:4,text:"6-10次"},
               {value:5,text:"10次以上"}        
               ],
               needOther:false
        },{
            id:'7',
            prop:'q6',
            type:'signselect',
            title:"7.目前您是否进入选校阶段？",
            items:[
               {value:1,text:"是"},
               {value:2,text:"否"}      
               ],
               needOther:false
        },{
            id:'8',
            prop:'q8',
            type:'signselect',
            title:"8.老师提供的院校信息是否客观、全面、真实？",
            condtion:'this.model.q6=="1"',
           items:[
               {value:1,text:"是"},
               {value:2,text:"否"}      
               ],
               needOther:false
        },{
            id:'9',
            prop:'q9',
            type:'signselect',
             title:"9.顾问老师提供的选校方案是否符合您的实际情况和需求？",
            condtion:'this.model.q6=="1"',
           items:[
               {value:1,text:"符合"},
               {value:2,text:"一般"},
                {value:3,text:"不符合"}         
               ],
               needOther:false
        },{
            id:'10',
            prop:'q10',
            type:'signselect',
             title:"10.您是根据哪方面原因给出上题的选项？",
            condtion:'this.model.q6=="1"',
           items:[
               {value:1,text:"院校排名"},
               {value:2,text:"专业匹配度"},
               {value:3,text:"地理位置环境"},
               {value:4,text:"师生配比"},
               {value:5,text:"留学生占比"},
               {value:6,text:"以上全部"}                     
               ],
               needOther:false
        },{
            id:'11',
            prop:'q11',
            type:'signselect',
             title:"11.进入选校阶段后，您认为多久给出院校信息和选校方案较为合理？",
            condtion:'this.model.q6=="1"',
           items:[
               {value:1,text:"一周"},
               {value:2,text:"半个月"},
               {value:3,text:"一个月"},
               {value:4,text:"两个月"}                   
               ],
               needOther:false
        }
        ]
        
      };
    },
    components:{
       Score,
       NPSRadio,
       QandA,
       NPSCheckBox
    }
}
</script>

<style>

</style>


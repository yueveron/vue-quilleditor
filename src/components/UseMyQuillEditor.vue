<template>
  <div class="UseMyQuillEditor">
    <h1>{{msg}}</h1>
    <div class="block">
      <div>
        <h2>使用 v-model 语法糖实现</h2>
        <!-- 
          v-model 在 vue 中只是语法糖，以下语句的完整表述应该是： 给 MyQuillEditor 添加 v-model 属性时，默认会把 value 作为 MyQuillEditor 的 props，然后子组件内 emit "input" 就能执行 "content = inputVal"，实现更新父层 data。  
          <MyQuillEditor v-bind:value="content" v-on:input="content = inputVal" />
        -->
        <MyQuillEditor v-model="content"></MyQuillEditor>
        {{content}}
      </div>  
      <br><br>
      <div>
        <h2>常规实现方法</h2>
        <MyQuillEditorTest v-bind:initText="content2" v-on:textchange="onTextChange"></MyQuillEditorTest>
        {{content2}}
      </div>
      
    </div>
    <div>
      
    </div>
  </div>
</template>

<script>
import MyQuillEditor from '@/components/custom/MyQuillEditor.vue'
import MyQuillEditorTest from '@/components/custom/MyQuillEditorTest.vue'
export default {
  name: 'UseMyQuillEditor',
  components:{
    MyQuillEditor,
    MyQuillEditorTest  
  },
  data(){
    return {
      msg : '手动编写嵌入 Quill Editor 的 Vue Component',
      content : '<p>editor :: Quill Editor Basic 应用</p>',
      content2 : '<p>editor :: Quill Editor Basic 应用</p>',
      detail : '测试 v-model'
    }
  },
  methods:{
    onTextChange(val){
      this.content2 = val
    }
  }
}
</script>

<style scoped lang="scss">
.UseMyQuillEditor{
  width:850px;
  margin:0 auto;
}
.block{
  margin:30px 0;
  padding:20px 0;
  border-bottom:1px solid #eaecef;
}
.btn-wrapper{
  margin:20px 0;
}
</style>

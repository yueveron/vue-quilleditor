<template>
  <div class="UseDevVue2Editor">
    <h1>{{msg}}</h1>
    <div class="block">
      <h2>Example - Basic Setup</h2>
      <div class="quill-editor-wrapper">
        <VueEditor id="editor1" v-model="editor1Content" placeholder="请输入内容" :editorToolbar="customToolbar1"></VueEditor>
      </div>
      <div class="btn-wrapper">
        <button @click="clickGetQuillContent1">Get Quill</button>
      </div>
    </div>
    
    <div class="block">
      <h2>Example - Custom Toolbar and Event</h2>
      <div class="quill-editor-wrapper">
        <VueEditor id="editor2" v-model="editor2Content" 
        :editorToolbar="customToolbar2"
        @blur="onEditorBlur"
        @focus="onEditorFocus"
        @ready="onEditorReady"
        @selection-change="onSelectionChange"
        >
        </VueEditor>
      </div>
      <div class="btn-wrapper">
        <button @click="clickGetQuillContent2">Get Quill</button>
      </div>
    </div>

  </div>
</template>

<script>

// 必须有花括号 {}
import { VueEditor, Quill } from "@/utils/dev-vue-editor/index.js"; 
// import { VueEditor } from "vue2-editor";

export default {
  name: 'UseDevVue2Editor',
  components:{
    VueEditor
  },
  data(){
    return {
      msg : 'UseDevVue2Editor',
      editor1Content : '<p>editor1 :: Quill Editor Basic 应用</p>',
      editor2Content : '<p>editor2 :: Quill Editor Custom ToolBar应用</p>',
      customToolbar1 :[
        ['bold', 'italic', 'underline'],
        [{ 'color': [] }], 
        ['clean']
      ],
      customToolbar2 :[
        ['bold', 'italic', 'underline'],
        [{ 'list': 'ordered'}, { 'list': 'bullet' }],
        ['clean']
      ]
    }
  },
  methods:{
    onEditorBlur(quill) {
      console.debug("editor blur!", quill);
    },
    onEditorFocus(quill) {
      console.debug("editor focus!", quill);
    },
    onEditorReady(quill) {
      console.debug("editor ready!", quill);
    },
    onEditorChange({ quill, html, text }) {
      console.debug("editor change!", quill, html, text);
      this.content = html;
    },
    onSelectionChange(range, oldRange, source) {
      console.debug("Selection change!", range);
    },
    clickGetQuillContent1(){
      console.debug(this.editor1Content)
    },
    clickGetQuillContent2(){
      console.debug(this.editor2Content)
    }
  }
}
</script>

<style scoped lang="scss">
.UseDevVue2Editor{
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

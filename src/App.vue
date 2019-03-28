<template>
  <div id="app">
    <!-- <DemoVue2Editor></DemoVue2Editor> -->
    <!-- <UseDevVue2Editor></UseDevVue2Editor> -->
    <UseMyQuillEditor></UseMyQuillEditor>
  </div>
</template>

<script>
import DemoVue2Editor from './components/DemoVue2Editor.vue'
import UseDevVue2Editor from './components/UseDevVue2Editor.vue'
import UseMyQuillEditor from './components/UseMyQuillEditor.vue'

export default {
  name: 'app',
  components: {
    DemoVue2Editor,
    UseDevVue2Editor,
    UseMyQuillEditor
  },
  data(){
    return {}
  },
  mounted(){

  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

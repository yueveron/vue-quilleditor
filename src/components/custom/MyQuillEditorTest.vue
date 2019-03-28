<template>
  <!-- ref : for new Quill Instance(ref)  -->
  <div ref="quillContainer"></div>
</template>

<script>
import Quill from 'quill';  
export default {
  name: 'MyQuillEditorTest',
  props: {
    initText: {
      type: String,
      default: ''
    }
  }, 
  data(){
    return {
      editor: null
    }
  },
  mounted(){
    // console.debug(this.$refs.quillContainer)
    this.editor = new Quill(this.$refs.quillContainer,{
      modules: {
        toolbar : [
          [{ header: [1, 2, 3, 4, false] }],
          ['bold', 'italic', 'underline']  
        ]
      },
      theme : 'snow',
      formats: ['bold', 'underline', 'header', 'italic']
    })

    this.editor.root.innerHTML = this.initText;
    this.editor.on('text-change', () => this.update())
  },
  methods:{
    update(){
      const inputVal = this.editor.getText()?this.editor.root.innerHTML : ''
      this.$emit('textchange', inputVal)
    }
  }
}
</script>

<style scoped lang="scss">
</style>

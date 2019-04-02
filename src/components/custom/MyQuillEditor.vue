<template>
  <!-- ref : for new Quill Instance(ref)  -->
  <div ref="quillContainer"></div>
</template>

<script>
import Quill from 'quill';
export default {
  name: 'MyQuillEditor',
  props: {
    //当父层定义组件，并且添加 v-model 属性时，默认会把 value 作为组件的属性，所以必须子层属性名必须也是 value
    value: {
      type: String,
      default: ''
    }
  },
  data () {
    return {
      editor: null
    }
  },
  mounted () {
    // console.debug(this.$refs.quillContainer)
    this.editor = new Quill(this.$refs.quillContainer, {
      modules: {
        toolbar: [
          [{ header: [1, 2, 3, 4, false] }],
          ['bold', 'italic', 'underline']
        ]
      },
      theme: 'snow',
      formats: ['bold', 'underline', 'header', 'italic']
    })

    this.editor.root.innerHTML = this.value;
    this.editor.on('text-change', () => this.update())
  },
  methods: {
    update () {
      const inputVal = this.editor.getText() ? this.editor.root.innerHTML : ''
      //emit : 通知父层修改 props.value
      this.$emit('input', inputVal)
    }
  }
}
</script>

<style scoped lang="scss">
</style>

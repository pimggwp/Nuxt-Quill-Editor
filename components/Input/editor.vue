<template>
  <section class="container">
    <client-only>
      <input id="getFile" type="file" hidden @change="uploadFunction($event)">
      <quill-editor
        ref="editor"
        v-model="content"
        :options="editorOption"
        @change="$emit('change', $event)"
        @blur="$emit('blur', $event)"
        @focus="$emit('focus', $event)"
        @ready="$emit('ready', $event)"
      />
    </client-only>
  </section>
</template>

<script>
// import { Quill } from 'vue-quill-editor'
import ImageResize from '@taoqf/quill-image-resize-module'
// Quill.register('modules/imageResize', ImageResize)
  export default {
    name: 'quill-example-nuxt',
    data () {
      return {
        content: '<p>I am Example</p>',
        editorOption: {
          // Some Quill options...
          theme: 'snow',
          modules: {
            toolbar: [
              ['bold', 'italic', 'underline', 'strike'],
              ['blockquote', 'code-block'],
              [{ header: 2 }],
              [{ list: 'ordered' }, { list: 'bullet' }],
              [{ script: 'sub' }, { script: 'super' }],
              [{ indent: '-1' }, { indent: '+1' }],
              [{ header: [1, 2, 3, 4, 5, 6, false] }],
              [{ color: [] }, { background: [] }],
              [{ align: [] }],
              ['clean'],
              ['link', 'image', 'video']
            ],
            // imageResize: {
            //   modules: ['Resize', 'DisplaySize'],
            //   handleStyles: {
            //     backgroundColor: 'black'
            //   }
            // }
          }
        }
      }
    },
    mounted() {
      setTimeout(() => {
        this.content = 'I was changed!'
      }, 3000)
    },
    methods: {
      onEditorBlur(editor) {
        console.log('editor blur!', editor)
      },
      onEditorFocus(editor) {
        console.log('editor focus!', editor)
      },
      onEditorReady(editor) {
        console.log('editor ready!', editor)
      }
    }
  }
</script>

<style lang="scss">
  .editor-container {
    margin: 0 auto;
    blockquote, h1, h2, h3, h4, h5, h6, ol, p, pre, ul {
        margin: 0 0 15px!important;
        padding: 0;
        counter-reset: list-1 list-2 list-3 list-4 list-5 list-6 list-7 list-8 list-9;
    }
    .ql-video {
      padding: 0px 2px;
      width: 560px;
      height: 315px;
      margin: 0 auto;
    }
    h2 {
      font-size: 1.5rem !important;
      font-weight: bold;
    }
    h3 {
      font-size: 1.35rem !important;
      font-weight: bold;
    }
    h4 {
      font-size: 1.25rem !important;
      font-weight: bold;
    }
    h5 {
      font-size: 1.15rem !important;
      font-weight: bold;
    }
    h6 {
      font-size: 1.1rem !important;
      font-weight: bold;
    }
    .quill-editor.ql-container {
      font-size: 17px;
      font-family: 'Sarabun-Light';
      height: 550px;
      .ql-tooltip.ql-editing {
        left: 0px !important;
      }
    }
  }
  .ql-editor{
    height: 500px;
  }
</style>
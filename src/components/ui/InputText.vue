<template>
  <div class="container">
    <div class="form-group">
        <input type="text" placeholder value />
    </div>
    <div class="row">
        <div class="col-12">
            <quill-editor
                v-model="content"
                ref="myQuillEditor"
                :options="editorOption"
            />
        </div>
    </div>
  </div>
</template>

<script>
import "quill/dist/quill.core.css"
import "quill/dist/quill.snow.css"
import { quillEditor } from "vue-quill-editor"

export default {
  name: "InputText",
  components: {
    quillEditor
  },
  data() {
    return {
      content: "<p>example content</p>",
      editorOption: {
        /* quill options */
      }
    }
  }
}
</script>

<style scope>
    
</style>
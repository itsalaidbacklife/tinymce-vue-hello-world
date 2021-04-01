<template>
  <div class="editor">
    <h1>Tiny MCE + Vue Hello World</h1>
    <editor
      v-model="editorVal"
      :api-key="apiKey"
       :init="{
         height: 300,
         menubar: false,
         plugins: [
           'advlist autolink lists link image charmap print preview anchor',
           'searchreplace visualblocks code fullscreen',
           'insertdatetime media table paste code help wordcount'
         ],
         toolbar:
           'undo redo | formatselect | bold italic backcolor | \
           alignleft aligncenter alignright alignjustify | \
           bullist numlist outdent indent | removeformat | help'
       }"

    />
    <h3>Captured html:</h3>
    {{ editorVal }}
  </div>
</template>

<script>
import Editor from '@tinymce/tinymce-vue';

export default {
  name: "HelloWorld",
  components: {
    Editor,
  },
  props: {
    msg: String,
  },
  data() {
    return {
      editorVal: null,
    }
  },
  computed: {
    apiKey() {
      return process.env.VUE_APP_TINY_MCE_KEY || 'no-api-key'
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

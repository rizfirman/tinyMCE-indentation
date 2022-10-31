<!-- Please remove this file from your project -->
<template>
  <div>
    <editor
      api-key="4b9so3l9rz3qp7sztucy8em7h74bc8ntqrzdo66osna8atsq"
      :init="{
        plugins: 'lists link image paste help wordcount',
        nonbreaking_force_tab: true,
        init_instance_callback: tabAction,
        toolbar:
          'nonbreaking | undo redo | blocks | bold italic | alignleft aligncenter alignright alignjustify | bullist numlist outdent indent | help',
      }"
      initial-value="Once upon a time..."
      v-model="editor"
    />
    <div style="display: flex; justify-content: center">
      <button
        @click="onSubmit"
        style="
          background-color: black;
          color: white;
          padding: 4px;
          border-radius: 4px;
          margin-top: 10px;
          width: 200px;
        "
      >
        submit
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'NuxtTutorial',
  data() {
    return {
      editor: null,
    }
  },
  methods: {
    tabAction(editor) {
      editor.on('keydown', function (e) {
        if (e.keyCode == 9) {
          e.preventDefault()
          tinymce.activeEditor.execCommand(
            'mceInsertContent',
            false,
            '&nbsp;&nbsp;&nbsp;&nbsp;'
          )
        }
      })
    },
    onSubmit() {
      console.log(this.editor)
    },
  },
}
</script>

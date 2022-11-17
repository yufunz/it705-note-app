<template>
  <div id="note-editor" class="h-75">
    <textarea
      v-bind:value="activeNoteText"
      v-on:input="editNote"
      class="form-control"
      rows="45"
    ></textarea>
  </div>
</template>

<script>
export default {
  computed: {
    activeNoteText() {
      return this.$store.getters.activeNote.text
    }
  },
  methods: {
    editNote(e) {
      this.$store.dispatch("editNote", e.target.value)
    }
  }
}
</script>

<style type="text/css">
#note-editor {
  padding: 0;
}

textarea {
  resize: none;
  height: 100%;
}

.form-control:focus {
  border-color: #017ba9;
}
</style>

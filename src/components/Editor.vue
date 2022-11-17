<template>
  <div id="note-editor">
    <textarea
      v-bind:value="activeNoteText"
      v-on:input="editNote"
      class="form-control"
      placeholder="Please click + or select an existing note."
      rows="15"
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
      this.$store.dispatch(
        "updateTimeStamp",
        new Date().toLocaleString("en-NZ")
      )
    }
  }
}
</script>

<style type="text/css">
#note-editor {
  padding: 0;
  padding-bottom: 40px;
}

textarea {
  resize: none;
  height: 100%;
}

.form-control:focus {
  border-color: #017ba9;
}
</style>

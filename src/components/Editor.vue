<template>
  <div id="note-editor">
    <textarea
      v-bind:value="activeNoteText"
      v-on:input="editNote"
      class="form-control"
    ></textarea>

    <a
      id="weather"
      class="weatherwidget-io"
      href="https://forecast7.com/en/n46d41168d35/invercargill/"
      data-label_1="INVERCARGILL"
      data-label_2="WEATHER"
      data-theme="original"
      >INVERCARGILL WEATHER</a
    >
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

<script>
!(function (d, s, id) {
  var js,
    fjs = d.getElementsByTagName(s)[0]
  if (!d.getElementById(id)) {
    js = d.createElement(s)
    js.id = id
    js.src = "https://weatherwidget.io/js/widget.min.js"
    fjs.parentNode.insertBefore(js, fjs)
  }
})(document, "script", "weatherwidget-io-js")
</script>

<style type="text/css">
#note-editor {
  height: 100%;
  margin-left: 380px;
}

#note-editor textarea {
  resize: none;
  height: 90%;
  border: 0;
  border-radius: 0;
}
</style>

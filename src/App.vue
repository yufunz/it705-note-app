<template>
  <div id="app">
    <toolbar></toolbar>
    <note-list></note-list>
    <el-container>
      <el-main height="90%">
        <editor></editor>
      </el-main>
      <el-footer>
        <widget></widget>
      </el-footer>
    </el-container>
  </div>
</template>

<script>
import Toolbar from "./components/Toolbar"
import NoteList from "./components/NoteList"
import Editor from "./components/Editor"
import Widget from "./components/Widget.vue"

export default {
  components: {
    Toolbar,
    NoteList,
    Editor,
    Widget
  }
}
</script>
<style type="text/css">
html,
#app {
  height: 100%;
}

body {
  margin: 0;
  padding: 0;
  border: 0;
  height: 100%;
  max-height: 100%;
  position: relative;
}
</style>

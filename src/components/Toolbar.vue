<template>
  <div id="toolbar" class="text-center">
    <i id="add" @click="addOne" class="el-icon-circle-plus"></i>
    <i
      id="star"
      @click="toggleFavorite"
      class="el-icon-star-on"
      v-bind:class="{ starred: activeNote.favorite }"
    ></i>
    <i id="remove" @click="deleteNote" class="el-icon-delete-solid"></i>
  </div>
</template>

<script>
export default {
  computed: {
    activeNote() {
      return this.$store.getters.activeNote
    }
  },
  methods: {
    addOne() {
      //AddNote distributed to actions via dispatch
      this.$store.dispatch("addNote")
    },
    toggleFavorite() {
      this.$store.dispatch("toggleFavorite")
    },
    deleteNote() {
      this.$store.dispatch("deleteNote")
    }
  }
}
</script>
<style type="text/css">
#toolbar {
  float: left;
  width: 80px;
  height: 100%;
  background-color: #003d54;
  padding: 35px 25px 25px 25px;
}

#toolbar i {
  font-size: 40px;
  margin-bottom: 35px;
  margin-left: -5px;
  cursor: pointer;
  opacity: 0.6;
  transition: opacity 0.5s ease;
}

#add {
  color: #30d401;
}

#star {
  color: #d4ba01;
}

#remove {
  color: #d43b01;
}

#toolbar i:hover {
  opacity: 1;
}

.starred {
  color: #d4ba01;
}
</style>

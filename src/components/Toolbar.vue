<template>
  <div id="toolbar">
    <i id="add" @click="addOne" class="glyphicon glyphicon-plus"></i>
    <i
      id="star"
      @click="toggleFavorite"
      class="glyphicon glyphicon-star"
      v-bind:class="{ starred: activeNote.favorite }"
    ></i>
    <i id="remove" @click="deleteNote" class="glyphicon glyphicon-remove"></i>
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
  background-color: #30414d;
  color: #767676;
  padding: 35px 25px 25px 25px;
}

#toolbar i {
  font-size: 30px;
  margin-bottom: 35px;
  cursor: pointer;
  opacity: 0.4;
  transition: opacity 0.5s ease;
}

#add {
  color: green;
}

#star {
  color: yellow;
}

#remove {
  color: red;
}

#toolbar i:hover {
  opacity: 1;
}

.starred {
  color: #f7ae4f;
}
</style>

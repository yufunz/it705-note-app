<template>
  <div id="notes-list">
    <div id="list-header">
      <div class="text-center">
        <i class="brand el-icon-notebook-2"></i>
      </div>
      <div class="btn-group btn-group-justified" role="group">
        <!-- All Notes button -->
        <div class="btn-group" role="group">
          <button
            @click="show = 'all'"
            type="button"
            class="btn btn-default"
            v-bind:class="{ active: show == 'all' }"
          >
            All Notes <span class="badge">{{ noteCount }}</span>
          </button>
        </div>

        <!-- Favorites Button -->
        <div class="btn-group" role="group">
          <button
            @click="show = 'favorites'"
            type="button"
            class="btn btn-default"
            v-bind:class="{ active: show == 'favorites' }"
          >
            Favorites <span class="badge">{{ favNoteCount }}</span>
          </button>
        </div>
      </div>
    </div>

    <!-- render notes in a list -->
    <div class="container">
      <div class="list-group">
        <a
          v-for="(item, index) in notes"
          class="list-group-item"
          v-bind:class="{ active: activeNote == item }"
          v-bind:key="index"
          v-on:click="updateActiveNote(item)"
          href="#"
        >
          <h4 class="list-group-item-heading">
            <i
              class="el-icon-star-on"
              v-if="item.favorite"
              style="color: #d4ba01"
            ></i
            >{{ item.text }}
          </h4>
          <small>{{ item.timestamp }}</small>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      show: "all"
    }
  },
  computed: {
    notes() {
      if (this.show == "all") {
        return this.$store.getters.notes
      } else if (this.show == "favorites") {
        return this.$store.getters.notes.filter((note) => note.favorite)
      }
    },
    activeNote() {
      return this.$store.getters.activeNote
    },
    noteCount() {
      return this.$store.getters.getNoteCount
    },
    favNoteCount() {
      return this.$store.getters.getFavNoteCount
    }
  },
  methods: {
    updateActiveNote(note) {
      console.log(note)
      this.$store.dispatch("updateActiveNote", note)
    }
  }
}
</script>
<style type="text/css">
.brand {
  font-size: 100px;
  margin: 20px 20px;
  color: #003d54;
}

#notes-list {
  float: left;
  width: 300px;
  height: 100%;
  background-color: #f5f5f5;
  font-family: "Rubik", sans-serif;
  font-weight: 400;
}

#list-header {
  padding: 5px 25px 25px 25px;
}

#list-header h2 {
  font-weight: 300;
  text-transform: uppercase;
  text-align: center;
  font-size: 22px;
  padding-bottom: 8px;
}

#notes-list .container {
  overflow: auto;
  width: 100%;
  padding: 0;
}

#notes-list .container .list-group-item {
  border-radius: 0;
}

.list-group-item-heading {
  font-weight: 300;
  font-size: 15px;
  overflow-wrap: break-word;
}

.list-group-item.active {
  background-color: #017ba9;
}
</style>

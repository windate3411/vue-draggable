<template>
  <div id="app" class="min-h-screen w-screen bg-gray-200 flex items-center justify-center">
    <div class="w-full max-w-md">
      <h1 class="mb-2 text-gray-700 font-semibold font-sans tracking-wide">A Draggable List</h1>
      <draggable
        tag="ul"
        class="w-full max-w-md"
        ghost-class="moving-card"
        :list="users"
        :animation="200"
      >
        <user-card
          v-for="user in users"
          :user="user"
          :key="user.id"
          @on-edit="onEdit"
          @on-delete="onDelete"
        ></user-card>
      </draggable>
    </div>
  </div>
</template>

<script>
import { EditIcon, Trash2Icon } from "vue-feather-icons";
import Draggable from 'vuedraggable';
import UserCard from './components/UserCard.vue'

export default {
  name: 'app',
  data() {
    return {
      users: [
        {
          id: 1,
          name: "Adrian Schubert",
          avatar: "https://pickaface.net/gallery/avatar/unr_sample_161118_2054_ynlrg.png"
        },
        {
          id: 2,
          name: "Violet Gates",
          avatar: "https://pickaface.net/gallery/avatar/freud51c8b3f65e7dc.png"
        },
        {
          id: 3,
          name: "Steve Jobs",
          avatar: "https://pickaface.net/gallery/avatar/Opi51c74d0125fd4.png"
        },
        {
          id: 4,
          name: "Yassine Smith",
          avatar: "https://pickaface.net/gallery/avatar/unr_yassine_191124_2012_3gngr.png"
        },
        {
          id: 5,
          name: "Senior Saez",
          avatar: "https://pickaface.net/gallery/avatar/elmedinilla541c03412955c.png"
        }
      ]
    }
  },
  components: {
    Draggable,
    UserCard
  },
  methods: {
    onEdit(user) {
      alert(`Editing ${user.name}`);
    },
    onDelete(user) {
      alert(`Deleting ${user.name}`);
    }
  }
}
</script>

<style lang="scss">
.moving-card {
  border: 1px solid lightblue;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

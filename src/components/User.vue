<template>
  <div :class="[edit ? '' :'user-box']">
    <div v-if="!edit">
      <h3>{{ user.name }}</h3>
      <p>{{ user.email }}</p>
    </div>
    <div v-else>
      <input class="user-input" v-model="user.name" />
      <input class="user-input" v-model="user.email" />
    </div>
    <button class="btn btn-edit" v-on:click="handleEditBtn">
      Edit
    </button>
    <button class="btn btn-delete" @click="$emit('del-user', user.id)">
      Delete
    </button>
  </div>
</template>

<script>
export default {
  name: "User",
  props: {
    user: Object,
    userSelection: Array
  },
  data() {
    return {
      edit: false,
    };
  },
  methods: {
    handleEditBtn() {
      this.edit = !this.edit;
    }
  }
};
</script>

<style scoped>
.user-box {
  background: #f8f8f8;
  padding: 10px;
  width: 300px;
  margin: 5px;
  border: 1px #ccc solid;
}

.btn-edit {
  background: #42b983;
}

.btn-edit:hover {
  background: #33b074;
}

.btn-delete {
  background: #eb9080;
}

.btn-delete:hover {
  background: #c27669;
}
</style>

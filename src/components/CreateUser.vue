<template>
  <div>
    <input class="user-input" placeholder="New user name" v-model="name" />
    <input class="user-input" placeholder="New user name" v-model="email" />
    <button class="btn btn-create" @click="handleCreateBtn" :disabled="noUserData">
      Create
    </button>
  </div>
</template>

<script>
export default {
  name: "CreateUser",
  data() {
    return {
      name: null,
      email: null
    };
  },
  computed: {
    noUserData() {
      return !this.name || !this.email;
    }
  },
  methods: {
    handleCreateBtn() {
      const newUser = {
        id: null,
        name: this.name,
        email: this.email
      };
      this.$emit("create-user", newUser);
      this.name = this.email = null;
    }
  }
};
</script>

<style scoped>
.btn-create {
  background: #8090eb;
  margin-left: 5px;
}

.btn-create:hover {
  background: #7669c2;
}
</style>

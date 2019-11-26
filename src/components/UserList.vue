<template>
  <div class="user-list">
    <user
      v-for="user in users"
      :key="user.id"
      :user="user"
      @del-user="deleteUser"
    />
  </div>
</template>

<script>
import User from "@/components/User.vue";
export default {
  name: "UserList",
  props: {
    users: {
      type: Array,
      required: true
    }
  },
  components: {
    User
  },
  methods: {
    deleteUser(id) {
      const newUsers = this.users.filter(user => user.id !== id);
      this.$emit("update:users", newUsers);
    }
  }
};
</script>

<style scoped>
.user-list {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>

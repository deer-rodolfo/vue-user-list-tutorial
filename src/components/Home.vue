<template>
  <div>
    <h1>{{ title }}</h1>
    <user-list v-bind:users.sync="users"></user-list>
    <create-user @create-user="createUser" />
  </div>
</template>

<script>
import UserList from "./UserList";
import CreateUser from "./CreateUser.vue";
import axios from "axios";

export default {
  name: "Home",
  data() {
    return {
      title: "User List",
      users: [
        {
          id: 1,
          name: "Dieter",
          email: "dieter@d25.io"
        },
        {
          id: 2,
          name: "Klaus",
          email: "klaus@d25.io"
        },
        { id: 3, name: "Ema", email: "ema@d25.io" }
      ]
    };
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/users")
      // eslint-disable-next-line no-console
      .then(response => {
        this.users = response.data;
      });
  },
  methods: {
    createUser(newUser) {
      const newId = this.users[this.users.length - 1].id + 1;
      newUser.id = newId;
      this.users.push(newUser);
    }
  },
  components: {
    UserList,
    CreateUser
  }
};
</script>

<style>
.btn {
  background: gray;
  color: white;
  border: none;
  padding: 5px 9px;
  margin: 5px;
  cursor: pointer;
}
.user-input {
  margin: 5px;
}
</style>

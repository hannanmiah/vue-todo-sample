<template>
  <h1>{{ msg }}</h1>
  <h6>{{ numberOfUsers }} user is availble right now!</h6>

  <ul v-for="user in users">
    <li>
      {{ user.name }} ({{ user.age }})
      <button class="delete" @click="deleteUser">Delete</button>
    </li>
  </ul>
</template>

<script>
import { ref, computed, reactive, toRefs } from "vue";
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  setup() {
    const user = reactive({
      users: [
        {
          name: "Hannan Miah",
          age: 24,
          email: "hannanhridoy@gmail.com",
        },
        {
          name: "Mustakim Sharkar",
          age: 22,
          email: "mustakimsharkar@gmail.com",
        },
      ],

      numberOfUsers: computed(() => user.users.length),

      deleteUser() {
        user.users.pop();
      },
    });

    return toRefs(user);
  },
};
</script>

<style scoped>
button {
  background: blue;
  color: white;
  border: 3px solid #ddd;
  padding: 5px;
}

.delete {
  background: red;
  border: 1px solid orange;
}
</style>

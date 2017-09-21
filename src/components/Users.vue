<template>
  <div class="users">
    <h1>Users</h1>
      <form v-on:submit="addUser">

        <div>
          <label for="name">Name</label>
          <input type="text" name="name" id="name" v-model="newUser.name" placeholder="Enter Name">
        </div>

        <div>
          <label for="email">Email</label>
          <input type="text" name="email" id="email" v-model="newUser.email" placeholder="Enter Email">
        </div>

        <div>
          <input type="submit" value="Submit">
        </div>

      </form>
    <ul>
      <li v-bind:key="user.id" v-for="user in users">
        <input type="checkbox" class="toggle" v-model="user.contacted">
        <span :class="{contacted: user.contacted}">
          {{ user.name }} {{ user.email }}
          <button v-on:click="deleteUser(user)">x</button>
        </span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'users',
  props: {
    
  },
  data() {
    return {
      newUser: {},
      users: []
    }
  },
  methods: {
    addUser: function(e) {
      this.users.push({
        name: this.newUser.name,
        email: this.newUser.email,
        contacted: false
      })
      e.preventDefault()
    },
    deleteUser: function(user) {
      this.users.splice(this.users.indexOf(user), 1)
    }
  },
  computed: {
    
  },
  created: function() {
    this.$http.get('https://jsonplaceholder.typicode.com/users')
      .then(function(response) {
        this.users = response.data
      })
  }
}
</script>

<style scoped>
.contacted {
  text-decoration: line-through
}
</style>

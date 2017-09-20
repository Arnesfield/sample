<template>
  <div class="test">
    <input type="text" v-model="title"><br>
    <h1>{{ title }}</h1>
    <p v-if="showName">{{ user.fname }}</p>
    <p v-else>Nobody</p>
    <p>{{ user.lname }}</p>
    <ul>
      <li
        v-for="item in items"
        v-bind:key="item.id">{{ item.title }}</li>
    </ul>

    <button v-on:click="greet('Hello World')">Greet</button>
    <input type="text" v-on:keyup="pressKey" v-on:keyup.enter="enterHit">
  </div>
</template>

<script>
export default {
  name: 'test',
  data () {
    return {
      title: 'Hello world',
      user: {
        fname: 'Jefferson',
        lname: 'Rylee'
      },
      showName: true,
      items: [
        { id: 1, title: 'Apple' },
        { id: 2, title: 'Banana' },
        { id: 3, title: 'Orange' }
      ]
    }
  },
  methods: {
    greet: function(greeting) {
      alert(greeting)
    },
    pressKey: function(e) {
      console.log(e.target.value)
    },
    enterHit: function() {
      console.log('You hit enter')
    }
  }
}
</script>

<style scoped>

</style>

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
  }
}
</script>

<style scoped>

</style>

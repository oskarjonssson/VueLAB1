<template>
  <div id="app">
    <users></users>
  </div>
</template>

<script>


import list from './components/list.vue'
import users from './components/users.vue'

export default {
  name: 'app',
  components: {
    //list,
    users
  }
}

</script>

<style>
#app{

  display: flex;
  justify-content: center;
  /*height: 100vh; */
  margin: 0;
  padding: 0;
  background:linear-gradient(135deg, #7367F0 0%,#CE9FFC 100%);
}

</style>

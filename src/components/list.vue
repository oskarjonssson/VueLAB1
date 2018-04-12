<template>
  <div class="list">
    <h1>{{title}}</h1>
    <input type="text" v-model="title"><br />
    <ul>
      <li v-for="item in items">{{item.output}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'list',
  data(){
    return{
      title: "Hello World",
      items: [
        {output: 'Item One'},
        {output: 'Item Two'},
        {output: 'Item Three'}
      ]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

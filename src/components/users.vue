<template>
  <div class="users">
    <h1>Users</h1>
    <input type="Text" v-model="newUser.name" placeholder="Enter a string" />
    <button v-on:click="addItem">ADD</button>
    <ul>
      <li v-for="item in users" v-bind:class="{back: item.marked}">
        <input type="checkbox" class="toggle" v-model="item.marked"/>
        <span v-bind:class="{ marked: item.marked}">
        {{item.str}}<button v-on:click="deleteItem(item)">x</button>
        </span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'users',
  data(){
    return{
      newUser: {},
      users: [
        {
          str: "Mjölk",
          marked: false
        },
        {
          str: "Bröd",
          marked: false
        },
        {
          str: "Smör",
          marked: false
        }
      ]
    }
  },
  methods: {
    addItem: function(event){
      this.users.push({
        str: this.newUser.name,
        marked: false
      })
      this.newUser.name="";
      console.log(this.users);
    },
    deleteItem: function(item){
      this.users.splice(this.users.indexOf(item), 1)
    }
  }
}
</script>


<style scoped>
.users{
  text-align: center;
}
ul{
  margin: 0 auto;
  padding: 0;
  width: 50%;
  list-style: none;
}
li{
  margin: 5px 0 0 0;
  background-color: #4BC2C5;

  border: 1px solid black;
}
.marked{
  text-decoration: line-through;
}
.back{
  background-color: #78FEE0;
}
</style>

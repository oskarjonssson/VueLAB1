<template>
  <div class="users">
    <h1>Users</h1>
    <div class="inputWrap">
      <input type="Text" v-model="newUser.name" placeholder="Movie name" />
      <!--<button v-on:click="addItem">ADD</button> -->
      <add-poster v-on:adding-poster="addItem" /> <!-- Komponent som lägger till text och bild -->
    </div>
    <ul>
      <li v-for="item in users" v-bind:class="{back: item.marked}">
        <div>
          <input type="checkbox" class="toggle" v-model="item.marked"/>
          <span  v-bind:class="{ marked: item.marked}">
            <p v-if="item.edit == false">{{item.str}}</p>
            <input type="text" v-else v-model="item.str"></input>
            <button v-on:click="deleteItem(item)">x</button>
            <button  v-if="item.edit == false" v-on:click="editItem(item)">Edit</button>
            <button v-else v-on:click="saveEdit(item)">Save</button>
          </span>
        </div>
        <div class="mediaWrap">
          <add-img v-bind:url="item.urlList" /> <!-- Komponent bild-->
          <add-video v-bind:video="item.videoList" /> <!-- Komponent video -->
        </div>
      </li>
    </ul>
  </div>
</template>


<script>
import addImg from './addImg.vue';
import addVideo from './addVideo.vue';
import addPoster from './addPoster.vue';

export default {
  name: 'users',
  components: {
    'add-img': addImg,
    'add-video': addVideo,
    'add-poster': addPoster
  },
  data(){
    return{
      newUser: {},
      users: [
        {
          str: "Avengers: Age of Ultron (2015)",
          marked: false,
          edit: false,
          urlList: 'https://ia.media-imdb.com/images/M/MV5BMTM4OGJmNWMtOTM4Ni00NTE3LTg3MDItZmQxYjc4N2JhNmUxXkEyXkFqcGdeQXVyNTgzMDMzMTg@._V1_UX182_CR0,0,182,268_AL_.jpg',
          videoList: "https://www.youtube.com/embed/tmeOjFno6Do"
        },
        {
          str: "Avengers (2012)",
          marked: false,
          edit: false,
          urlList: 'https://ia.media-imdb.com/images/M/MV5BMTk2NTI1MTU4N15BMl5BanBnXkFtZTcwODg0OTY0Nw@@._V1_UX182_CR0,0,182,268_AL_.jpg',
          videoList: "https://www.youtube.com/embed/zatgnqdIefs"

        },
        {
          str: "Doctor Strange (2016)",
          marked: false,
          edit: false,
          urlList: 'https://ia.media-imdb.com/images/M/MV5BNjgwNzAzNjk1Nl5BMl5BanBnXkFtZTgwMzQ2NjI1OTE@._V1_UX182_CR0,0,182,268_AL_.jpg',
          videoList: "https://www.youtube.com/embed/HSzx-zryEgM"

        }
      ]
    }
  },
  methods: {
    addItem: function(posterUrl){
      this.users.push({
        str: this.newUser.name,
        marked: false,
        edit: false,
        urlList: posterUrl
      })
      this.newUser.name="";
      console.log(this.users);
    },
    deleteItem: function(item){
      this.users.splice(this.users.indexOf(item), 1)
    },
    editItem: function(item){
      item.edit = true;
      console.log(item);
    },
    saveEdit: function(item){
      item.edit = false;
      console.log(item);
    },
    addPosterToList: function(posterUrl) {
			console.log('addPosterToList', posterUrl);
			item.urlList.push(posterUrl);
		}
  }//methods
}
</script>


<style scoped>
.users{
  text-align: center;
}
ul{
  margin: 0 auto;
  padding: 0;
  width: 700px;
  list-style: none;
}
li{
  margin: 15px 0 0 0;
  background-color: #4BC2C5;
  border: 1px solid black;
}
li div {
  padding: 10px 0 0 0;
}
p{
  margin: 0;
  padding: 0;
  display: inline;
}
.marked{
  text-decoration: line-through;
}
.back{
  background-color: #78FEE0;
}
.mediaWrap{
  display: flex;
  justify-content: center;
  padding: 20px 0 20px 0;
}
.inputWrap{
  display: flex;
  justify-content: center;
  padding: 10px 10px 10px;
}
.inputWrap input{
  margin: 0 10px 0 0;
}
</style>

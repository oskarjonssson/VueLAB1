<template>
  <div class="users">
    <h1>Movies</h1>
    <div class="inputWrap">
      <input type="Text" v-model="newUser.name" placeholder="Movie name" />
      <input type="text" v-model="newUser.year" placeholder="Release year" />
      <message  errorMessage="Hur får man ett meddelande hit?" ></message>
      <!--<button v-on:click="addItem">ADD</button> -->
      <add-poster v-on:adding-poster="addItem" /> <!-- Komponent som lägger till text och bild -->
    </div>
    <ul>
      <li v-for="item in users" v-bind:class="{back: item.marked}" v-on:click="marked(item)">
        <div class="mediaWrap">
          <add-img v-bind:url="item.urlList" /> <!-- Komponent bild-->
        <!--  <add-video v-bind:video="item.videoList" />  Komponent video -->
        </div>
        <div id="containerText">
          <div class="textWrap">
            <!--<label><input type="checkbox" class="toggle" v-model="item.marked"/>-->
              <span  v-bind:class="{ marked: item.marked}">
                <p v-if="item.edit == false">{{item.str}}</p>
                <input type="text" v-else v-model="item.str"><br>
                <p v-if="item.edit == false">{{item.strYear}}</p>
                <input type="text" v-else v-model="item.strYear">
              </span>
              <div class="btnWrap">
                <button class="btnDelete" v-on:click="deleteItem(item)">x</button>
                <button class="btnEdit" v-if="item.edit == false" v-on:click="editItem(item)">Edit</button>
                <button class="btnSave" v-else v-on:click="saveEdit(item)">Save</button>
              </div>
            <!--</label> -->
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>


<script>
import addImg from './addImg.vue';
//import addVideo from './addVideo.vue';
import addPoster from './addPoster.vue';
import message from './message.vue';

export default {
  name: 'users',
  newMessage: 'hej',
  components: {
    'add-img': addImg,
    //'add-video': addVideo,
    'add-poster': addPoster,
    'message': message
  },
  data(){
    return{
      newUser: {},
      users: [
        {
          str: "Avengers: Age of Ultron ",
          strYear: " (2015)",
          marked: false,
          edit: false,
          urlList: 'https://ia.media-imdb.com/images/M/MV5BMTM4OGJmNWMtOTM4Ni00NTE3LTg3MDItZmQxYjc4N2JhNmUxXkEyXkFqcGdeQXVyNTgzMDMzMTg@._V1_UX182_CR0,0,182,268_AL_.jpg',
          //videoList: "https://www.youtube.com/embed/tmeOjFno6Do"
        },
        {
          str: "Avengers ",
          strYear: " (2012)",
          marked: false,
          edit: false,
          urlList: 'https://ia.media-imdb.com/images/M/MV5BMTk2NTI1MTU4N15BMl5BanBnXkFtZTcwODg0OTY0Nw@@._V1_UX182_CR0,0,182,268_AL_.jpg',
          //videoList: "https://www.youtube.com/embed/zatgnqdIefs"
        },
        {
          str: "Doctor Strange ",
          strYear:" (2016)",
          marked: false,
          edit: false,
          urlList: 'https://ia.media-imdb.com/images/M/MV5BNjgwNzAzNjk1Nl5BMl5BanBnXkFtZTgwMzQ2NjI1OTE@._V1_UX182_CR0,0,182,268_AL_.jpg',
          //videoList: "https://www.youtube.com/embed/HSzx-zryEgM"
        },
        {
          str: "Incredibles 2 ",
          strYear:" (2018)",
          marked: false,
          edit: false,
          urlList: 'https://ia.media-imdb.com/images/M/MV5BMTEzNzY0OTg0NTdeQTJeQWpwZ15BbWU4MDU3OTg3MjUz._V1_UX182_CR0,0,182,268_AL_.jpg',
          //videoList: "https://www.youtube.com/embed/HSzx-zryEgM"
        },
        {
          str: "Spider-Man: Homecoming ",
          strYear:" (2017)",
          marked: false,
          edit: false,
          urlList: 'https://ia.media-imdb.com/images/M/MV5BNTk4ODQ1MzgzNl5BMl5BanBnXkFtZTgwMTMyMzM4MTI@._V1_UX182_CR0,0,182,268_AL_.jpg',
          //videoList: "https://www.youtube.com/embed/HSzx-zryEgM"
        },
        {
          str: "Fight Club  ",
          strYear:" (1999)",
          marked: false,
          edit: false,
          urlList: 'https://ia.media-imdb.com/images/M/MV5BMzFjMWNhYzQtYTIxNC00ZWQ1LThiOTItNWQyZmMxNDYyMjA5XkEyXkFqcGdeQXVyNzkwMjQ5NzM@._V1_UX182_CR0,0,182,268_AL_.jpg',
          //videoList: "https://www.youtube.com/embed/HSzx-zryEgM"
        },
        {
          str: "The Matrix ",
          strYear:" (1999)",
          marked: false,
          edit: false,
          urlList: 'https://ia.media-imdb.com/images/M/MV5BNzQzOTk3OTAtNDQ0Zi00ZTVkLWI0MTEtMDllZjNkYzNjNTc4L2ltYWdlXkEyXkFqcGdeQXVyNjU0OTQ0OTY@._V1_UX182_CR0,0,182,268_AL_.jpg',
          //videoList: "https://www.youtube.com/embed/HSzx-zryEgM"
        },
        {
          str: "Pulp Fiction ",
          strYear:" (1994)",
          marked: false,
          edit: false,
          urlList: 'https://ia.media-imdb.com/images/M/MV5BMTkxMTA5OTAzMl5BMl5BanBnXkFtZTgwNjA5MDc3NjE@._V1_UX182_CR0,0,182,268_AL_.jpg',
          //videoList: "https://www.youtube.com/embed/HSzx-zryEgM"
        },
        {
          str: "Doctor Strange ",
          strYear:" (2016)",
          marked: false,
          edit: false,
          urlList: 'https://ia.media-imdb.com/images/M/MV5BNjgwNzAzNjk1Nl5BMl5BanBnXkFtZTgwMzQ2NjI1OTE@._V1_UX182_CR0,0,182,268_AL_.jpg',
          //videoList: "https://www.youtube.com/embed/HSzx-zryEgM"
        }
      ]
    }
  },
  methods: {
    addItem: function(posterUrl){
      if(isNaN(this.newUser.year) || this.newUser.year == ''){
        console.log("detta var inget nummer")
        this.iMessage(name);
      }else{
        this.users.push({
          str: this.newUser.name,
          strYear: " ("+ this.newUser.year +")",
          marked: false,
          edit: false,
          urlList: posterUrl
        })
        this.newUser.name='';
        this.newUser.year='';
        console.log("this.newUser.year", this.strYear)
        console.log(this.users);
      }
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
		},
    marked: function(item){
      if(item.marked == false){
        item.marked = true;
      }else if(item.marked == true){
        item.marked = false;
      }
      console.log(item.marked);
    },
    iMessage: function(message){
      this.newMessage = message;
      console.log("detta fungerar??")
    }
  }//methods
}
</script>


<style scoped>
/* For Firefox */
input[type='number'] {
    -moz-appearance:textfield;
}

/* Webkit browsers like Safari and Chrome */
input[type=number]::-webkit-inner-spin-button,
input[type=number]::-webkit-outer-spin-button {
    -webkit-appearance: none;
    margin: 0;
}

h1{
  color: white;
  margin: 20px 0 50px 0;
  padding: 0;
  font-family: 'Montserrat', sans-serif;
}
.users{
  text-align: center;
}
ul{
  background-color: gren;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  margin: 0 auto;
  padding: 0;
  width: 700px;
  list-style: none;
}
li{
  font-family: 'Montserrat', sans-serif;
  color: white;
  margin: 15px 0 0 0;
  width: 200px;
  flex-wrap: wrap;
  background-color: transparent;
  border-radius: 5px;
  -webkit-box-shadow: -1px 4px 28px -1px rgba(0,0,0,0.2);
  -moz-box-shadow: -1px 4px 28px -1px rgba(0,0,0,0.2);
  box-shadow: -1px 4px 28px -1px rgba(0,0,0,0.2);
  display: flex;
  justify-content: center;
}

p{
  margin: 0;
  padding: 0;
  display: inline;
  font-family: arial;
  font-size: 18px;
  color: #3b3b3b;
}
.marked{
  text-decoration: line-through;
}
.back{
  background-color: #78FEE0;
}
.mediaWrap{
  display: flex;
  align-items: center;

  justify-content: center;
  padding: 0;
}
.inputWrap{
  width: 700px;
  display: flex;

  justify-content: space-between;
  padding: 10px 10px 10px;
}
.inputWrap input{
  font-family: 'Montserrat', sans-serif;
  margin: 0 10px 0 0;
  width: 170px;
  border-radius: 20px;
  outline: none;
  border: none;
  padding: 0 0 0 10px;
  height: 25px;

}
.textWrap{

}
#containerText{
  display: flex;
  align-items: center;
}
.btnWrap{
  display: flex;
}
.btnDelete {
  border: none;
  height: 25px;
  border-radius: 20px;
  width: 50px;
  color: white;
  background-color: #f64545;
  font-family: 'Montserrat', sans-serif;
  margin: 10px;
  font-size: 1em;
  font-weight: bold;
}
.btnDelete:hover {
  cursor: pointer;
  background: #dd3b3b;;
}

.btnEdit, .btnSave {
  border: none;
  height: 25px;
  border-radius: 20px;
  width: 100px;
  color: white;
  background-color: #adadad;
  font-family: 'Montserrat', sans-serif;
  margin: 10px;
}
.btnEdit:hover{
  cursor: pointer;
  background: #999;
}

span > input{
  font-family: 'Montserrat', sans-serif;
  border-radius: 20px;
  outline: none;
  border: none;
  padding: 0 0 0 10px;
  height: 18px;
  width: 160px;
}


</style>

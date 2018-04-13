<template>
  <div class="users">
    <h1>Movies</h1>
    <div class="inputWrap">
      <input type="Text" v-model="newUser.name" placeholder="Movie name" />
      <input type="Text" v-model="newUser.year" placeholder="Release year" />
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
                <input type="text" v-else v-model="item.str">
                <p v-if="item.edit == false">{{item.strYear}}</p>
                <input type="text" v-else v-model="item.strYear">
                <button v-on:click="deleteItem(item)">x</button>
                <button  v-if="item.edit == false" v-on:click="editItem(item)">Edit</button>
                <button v-else v-on:click="saveEdit(item)">Save</button>
              </span>
            </label>
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

export default {
  name: 'users',
  components: {
    'add-img': addImg,
    //'add-video': addVideo,
    'add-poster': addPoster
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

        }
      ]
    }
  },
  methods: {
    addItem: function(posterUrl){
      this.users.push({
        str: this.newUser.name,
        strYear: " ("+ this.newUser.year +")",
        marked: false,
        edit: false,
        urlList: posterUrl
      })
      this.newUser.name="";
      this.newUser.year="";
      console.log("this.newUser.year", this.newUser.year)
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
		},
    marked: function(item){
      if(item.marked == false){
        item.marked = true;
      }else if(item.marked == true){
        item.marked = false;
      }

      console.log(item.marked);
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
  border-radius: 5px;
  -webkit-box-shadow: -1px 4px 28px -1px rgba(0,0,0,0.2);
  -moz-box-shadow: -1px 4px 28px -1px rgba(0,0,0,0.2);
  box-shadow: -1px 4px 28px -1px rgba(0,0,0,0.2);
  display: flex;
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
  align-items: center;

  justify-content: center;
  padding: 0;
}
.inputWrap{
  display: flex;
  justify-content: center;
  padding: 10px 10px 10px;
}
.inputWrap input{
  margin: 0 10px 0 0;
}
.textWrap{
  padding: 0px 0 0 5px;
}
#containerText{
  display: flex;
  align-items: center;
}
</style>

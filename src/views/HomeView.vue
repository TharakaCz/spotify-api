<script>
import axios from 'axios';

const key = "Bearer BQABI_C-PwH2-yFyNZTZP6yiMDcYM5HUzRyCh7LYe3Mb1U_vzhpF6rk17s-ec-UqC0_quSnVJKB0wl4EIE77eFeiY9EcKjtT4pBQ3w9ArSNJShazF769SezZHls8LiP2K5qatfeUtMoQ6iaY3CsuGwvLmNVjRmVEGZ5FyOSKIFpxxur6GTHDEi8EU-_e1SOnwpLoynE0BqkrjS4Y-il6MYWeT4yd_l6JWt3DRlZBhnUcL6fIJcpP7tJtDgp0g_yffKK82BsCc6jyRsyi9y8vJ2Rjk4I"

export default{
  data(){
    return{
      tracks : [],

    }
  },
  methods :{

    track(){
      var data = this.serached
      axios.get("https://api.spotify.com/v1/search?q="+data+"&type=track%2Cartist&limit=20", {
        headers :{
          'Accept' : 'application/json',
          'Content-Type' : 'application/json',
          'Authorization' : key
        }
      })
      .then((res) =>{
        console.log(res.data.tracks.items);
        this.tracks = res.data.tracks.items;
        
      })
      .catch((error) =>{
        console.log(error);
      })
      .finally(() =>{

      });
    },

    listen(e){
    
      var audio = new Audio();
      // audio.pause();
      axios.get("https://api.spotify.com/v1/tracks/"+e,{
       headers :{
          'Accept' : 'application/json',
          'Content-Type' : 'application/json',
          'Authorization' : key
        }
      })
      .then((res) => {
        // console.log(res.data.preview_url);
          audio.src = res.data.preview_url;
          audio.play();
      })
      .catch((error) => {
        console.log(error);
      })
      .finally(() =>{

      });
    },
  }
}
</script>

<template>
  <main>
    <div class="containter">
      <div class="col-md-12">
        <div>
          <input v-model="serached" class="form-controll" type="text" placeholder="Enter Name" />
          <button class="btn btn-success" @click="track">Find</button>
        </div>
        <div class="row pt-5">

          <div class="card col-md-3" v-for="item in tracks">
            <div class="bg-image hover-overlay ripple" data-mdb-ripple-color="light">
              <img v-bind:src="item.album.images[0].url" class="img-fluid"/>
              <a href="#!">
                <div class="mask" style="background-color: rgba(251, 251, 251, 0.15);"></div>
              </a>
            </div>
            <div class="card-body">
              <h5 class="card-title">{{item.name}}</h5>
              <p class="card-text">{{item.album.name}}</p>
              <iframe style="border-radius:12px" v-bind:src="'https://open.spotify.com/embed/track/'+item.id+'?utm_source=generator'" width="100%" height="80" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture"></iframe>
            <!-- <button v-bind:id="item.id" @click="listen(item.id)" class="btn btn-primary">Play</button> -->
            </div>
          </div>

        </div>
      </div>
    </div>
    <!-- <TheWelcome /> -->
  </main>
</template>
<style scoped>
.listn{
  width:200px;
}
</style>

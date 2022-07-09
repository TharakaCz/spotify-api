<script>
import axios from 'axios';

  export default{
    data(){
      return {
        email:'',
        password:''
      };
    },
    methods:{
        onPost(){
          var array = {
            "email": this.email,
            "password": this.password
          }

          axios.post('http://localhost:5000/login', array)
          .then((res)=>{
            console.log(res);
          })
          .catch((error)=>{
            console.log(error);
          })
          .finally(() =>{

          });
          console.log("Email :"+this.email+"\n"+"Password :"+this.password);
        }
    }
  };
</script>
<template>
    <!-- Section: Design Block -->
<section class="background-radial-gradient overflow-hidden">
  <div class="container px-4 py-5 px-md-5 text-center text-lg-start my-5">
    <div class="row gx-lg-5 align-items-center mb-5">
      <div class="col-lg-6 mb-5 mb-lg-0" style="z-index: 10">
        <h1 class="my-5 display-5 fw-bold ls-tight" style="color: hsl(218, 81%, 95%)">
          The Spotify music finder <br />
          <span style="color: hsl(218, 81%, 75%)">Feel the music</span>
        </h1>
        <p class="mb-4 opacity-70" style="color: hsl(218, 81%, 85%)">
         easiest way to find globle music. in one place
        </p>
        <iframe width="360" height="215" src="https://www.youtube.com/embed/2FZYSyvLqnY?controls=0&amp;start=12" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope"></iframe>
      </div>

      <div class="col-lg-6 mb-5 mb-lg-0 position-relative">
        <!-- <div id="radius-shape-1" class="position-absolute rounded-circle shadow-5-strong"></div>
        <div id="radius-shape-2" class="position-absolute shadow-5-strong"></div> -->

        <div class="card bg-glass">
          <div class="card-body px-4 py-5 px-md-5">
            
            <form @submit.prevent="onPost">
              <div class="row">
                <div class="col-md-6 mb-4">
                  <div class="form-outline">
                    <input type="email" id="email" class="form-control"  v-model="email" required/>
                    <label class="form-label" for="email">Enter your email</label>
                  </div>
                </div>

                <div class="col-md-6 mb-4">
                  <div class="form-outline">
                    <input type="password" id="password" class="form-control" v-model="password" required/>
                    <label class="form-label" for="password">Enter password</label>
                  </div>
                </div>
              </div> 
              <button type="submit" class="btn btn-primary btn-block mb-4">
                Sign up
              </button>
            </form>

          </div>
        </div>
      </div>
    </div>
  </div>
</section>
<!-- Section: Design Block -->
</template>
<style scoped>
.background-radial-gradient {
      background-color: hsl(218, 41%, 15%);
      background-image: radial-gradient(650px circle at 0% 0%,
          hsl(218, 41%, 35%) 15%,
          hsl(218, 41%, 30%) 35%,
          hsl(218, 41%, 20%) 75%,
          hsl(218, 41%, 19%) 80%,
          transparent 100%),
        radial-gradient(1250px circle at 100% 100%,
          hsl(218, 41%, 45%) 15%,
          hsl(218, 41%, 30%) 35%,
          hsl(218, 41%, 20%) 75%,
          hsl(218, 41%, 19%) 80%,
          transparent 100%);
    }

    #radius-shape-1 {
      height: 220px;
      width: 220px;
      top: -60px;
      left: -130px;
      background: radial-gradient(#44006b, #ad1fff);
      overflow: hidden;
    }

    #radius-shape-2 {
      border-radius: 38% 62% 63% 37% / 70% 33% 67% 30%;
      bottom: -60px;
      right: -110px;
      width: 300px;
      height: 300px;
      background: radial-gradient(#44006b, #ad1fff);
      overflow: hidden;
    }

    .bg-glass {
      background-color: hsla(0, 0%, 100%, 0.9) !important;
      backdrop-filter: saturate(200%) blur(25px);
    }
</style>
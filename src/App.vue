<template>
<div class="container">
  <div v-for="waifu of image.slice(0,20)" :key="waifu.image"> 
    <img :src="waifu.image"/>
    <h1>{{waifu.name}}</h1>
    <p>{{waifu.anime}}</p>
  </div>
</div>
</template>

<script>
import axios from "axios";

export default {
  name: 'App',
  components: {

  },
  data() {
    return {
      image: [],
    };
  },
  created(){
    axios.get('https://waifu-generator.vercel.app/api/v1').then((res) =>{
      this.image = res.data;
      console.log(res.data);
    }).catch((err) =>{
      console.log(err);
    });
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body{
  background:#2D3142

}
.container{
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  padding:20px

}
.container > div{
  flex: 1 1 500px;
  padding:20px;
  color:#f9f9f9; 
}

img {
  max-width:100%;
  max-height:100%;
  display: block;
  min-height:400px;
  object-fit: cover;
  border-radius:20px;
}
</style>

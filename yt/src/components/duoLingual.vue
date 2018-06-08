<template>

  <div class='all'>
    <div class='buttons'>
    <button @click="changeLanguageENG()">ENG</button>
    <button @click="changeLanguageSRB()">SRB</button>
    </div>
    <div class='list'>
    <ul>
      <li v-for="video in info" 
      v-bind:key="video.youtubeId">      
      <img :src="generateThumbnailUrl(video.youtubeId)" alt="">
      <a href="">{{video.title}}</a>

     </li>
    </ul>
    </div>

    </div>

</template>

<script>

export default {
  name: 'duoLingual',
  data(){
    return{ 
        info:[],
        url:'https://api.myjson.com/bins/13mms5',
        urlSRB: "https://api.myjson.com/bins/99ixh",
        urlENG: "https://api.myjson.com/bins/13mms5"
    }
  },
mounted(){

if(agCookie.read("language") === "english"){
  this.axios.get(this.urlENG).then(response => {
  this.info = response.data.videos;
      
    })}else{
  this.axios.get(this.urlSRB).then(response => {
  this.info = response.data.videos;
      
    })}





},
methods:{

    generateThumbnailUrl(id){
      return youtube.generateThumbnailUrl(id)
    },
    createCookie(name, value, days){
      agCookie.create(name,value,days);
    },
     readCookie(name){
      return agCookie.read(name);
    },
    changeLanguageSRB(){
      this.url = this.urlSRB;
      this.axios.get(this.url).then(response => {
      this.info = response.data.videos;
        })
       agCookie.create("language","serbian",10);


    },
    changeLanguageENG(){
    this.url = this.urlENG;
     this.axios.get(this.url).then(response => {
      this.info = response.data.videos;
        })
      agCookie.create("language","english",10);


    }

}

}
</script>





<style scoped lang="scss">

.all{


    .buttons{
         display: flex;
         justify-content: center;

       button{
          background: red;
          border: none;
          color: black;
          margin-left: 10px;
          padding: 20px;
        }
    }



  .list{
      display: flex;
      justify-content: center;
      ul{
        list-style-type: none;
        text-align: left;
         li{ 
          margin-bottom: 20px;
          background: white;
             a{
              margin-left: 70px;
              color: red;
              text-decoration: none;
             }
             img{
                width: 150px;
                margin-top: 10px;
                margin-left: 10px;
              }
          }
        }
      }
}


</style>

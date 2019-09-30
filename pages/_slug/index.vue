<template>
  <div class="urls-area">  

    <input type="text" id="txt">

    <ul>
      <li v-for="url in urls"><a target="_blank" rel="nofollow" :href="url">{{ url }}</a></li>
    </ul>


    <form @submit.prevent="unlockTime">
      
      <input type="submit" class="shortme" value="Unlock!">
      
    </form>


  </div>
</template>

<script>

  import axios from 'axios';

  export default{    

      components: {
     
    },


    data(){

      return{
        urls: []
      }
    },

    async created(){
      

    },

    methods: {
      
      async unlockUrl(){

        const config = {
          headers: {
            Accept: "application/json"
          }
        };

        console.log(window.location.pathname)

        await axios.get('https://nodejs-practice-252711.appspot.com' + window.location.pathname, config)
        .then(res => {
          this.urls = res.data[0].urls
        })
        .catch(err => {
          console.log(err);
        })

      },

      unlockTime(){
        setTimeout(this.unlockUrl, 3000); 
        var x = document.getElementById("txt");
        setTimeout(function(){ x.value="1 seconds" }, 1000)
        setTimeout(function(){ x.value="2 seconds" }, 2000)
        setTimeout(function(){ x.value="3 seconds" }, 3000)
        
      }

    },

    head(){
      return{
        title: 'All Jokes'
      }
    }
  }
</script>

<style>

</style>
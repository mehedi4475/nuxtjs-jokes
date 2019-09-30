<template>
  <div class="urls-area">  
 

    <h1>{{ urlId }}</h1>

    <ul>
      <li v-for="url in urls"><a target="_blank" rel="nofollow" :href="url">{{ url }}</a></li>
    </ul>
  </div>
</template>

<script>

  import axios from 'axios';

  export default{    

      components: {
     
    },


    data(){

      return{
        jokes: [],
        urls: [],
        newUrl:"",
        urlId: ""
      }
    },

    async created(){
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

    head(){
      return{
        title: 'All Jokes'
      }
    }
  }
</script>

<style>

</style>
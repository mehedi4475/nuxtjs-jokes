<template>
  <div class="urls-area">
   
    <!--<SearchJoke v-on:search-text="searchText" />-->
    <form @submit.prevent="submitUrl">
      <textarea rows="15" class="urls-textarea"  type="text" v-model="newUrl" placeholder="Paste your URL's..."></textarea>
      <input type="submit" class="shortme" value="Short Me!">
      
    </form>

    <h1><a v-if="urlId" target="_blank" :href="urlId">http://localhost:3000/{{ urlId }}</a></h1>

    <ul>
      <li v-for="url in urls"><a :href="url">{{ url }}</a></li>
    </ul>
  </div>
</template>

<script>

  import axios from 'axios';
  import Url from '../components/Url'
  import SearchJoke from '../components/SingleUrl'

  export default{    

      components: {
      Url,
      SearchJoke
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
      
    },

    methods: {
      
      async submitUrl(){
        const config = {
          headers: {
            Accept: "application/json"
          }
        };

        await axios.post('https://nodejs-practice-252711.appspot.com/', {
          "urls": this.newUrl
        }, config)
        .then(res => {
          this.urlId = res.data._id,
          this.newUrl = ""
        })
        .catch(err => {
          console.log(err);
        })
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
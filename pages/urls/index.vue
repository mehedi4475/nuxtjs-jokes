<template>
	<div>
		<h1>URL</h1>
		<SearchJoke v-on:search-text="searchText" />
		<Joke v-for="joke in jokes" :key="joke.id" :id="joke.id" :joke="joke.joke"/>

		<h2>dd</h2>
	</div>

</template>

<script>

	import axios from 'axios';
	import Joke from '../../components/Url'
	import SearchJoke from '../../components/SingleUrl'

	export default{

		components: {
			Joke,
			SearchJoke
		},


		data(){

			return{
				jokes: [],
				urls: []
			}
		},

		async created(){
			const config = {
				headers: {
					Accept: "application/json"
				}
			};

			try{
				const res = await axios.post("https://nodejs-practice-252711.appspot.com", config);
				this.jokes = res.data.results
			}
			catch(err){
				console.log(err)
			}

		},

		methods: {
			async searchText(text){
				const config = {
					headers: {
						Accept: "application/json"
					}
				};

				try{
					const res = await axios.get('https://nodejs-practice-252711.appspot.com/' + text, config);
					this.urls = res.data
				} 
				catch(err){
					console.log(err)
				}
			},

			async createUrl(text){
				const config = {
					headers: {
						Accept: "application/json"
					}
				};

				try{
					const res = await axios.get('https://nodejs-practice-252711.appspot.com/' + text, config);
					this.jokes = res.data.results
				} 
				catch(err){
					console.log(err)
				}
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
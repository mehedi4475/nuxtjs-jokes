<template>
	<div>
		<h1>Jokes</h1>
		<SearchJoke v-on:search-text="searchText" />
		<Joke v-for="joke in jokes" :key="joke.id" :id="joke.id" :joke="joke.joke"/>
	</div>
</template>

<script>

	import axios from 'axios';
	import Joke from '../../components/Joke'
	import SearchJoke from '../../components/SearchJoke'

	export default{

		components: {
			Joke,
			SearchJoke
		},


		data(){

			return{
				jokes: []
			}
		},

		async created(){
			const config = {
				headers: {
					Accept: "application/json"
				}
			};

			try{
				const res = await axios.get("https://icanhazdadjoke.com/search", config);
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
					const res = await axios.get('https://icanhazdadjoke.com/search?term=' + text, config);
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
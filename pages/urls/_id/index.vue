<template>
	<div>
		<nuxt-link to="/jokes">Back to Jokes</nuxt-link>
		<h2>{{ joke.joke }}</h2>
		<p>Joke ID: {{ $route.params.id }}</p>
	</div>
</template>

<script>
	import axios from 'axios';
	export default{

		data(){
			return{
				joke: {}
			};
		},

		async created(){

			const config = {
				headers: {
					Accept: "application/json"
				}
			};

			try{
				const res = await axios.get('https://icanhazdadjoke.com/j/${this.$route.params.id}', config);
				this.joke = res.data
			}
			catch(err){
				console.log(err)
			}


		}



	}

</script>

<style>

</style>
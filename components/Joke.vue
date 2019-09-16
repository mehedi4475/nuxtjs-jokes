<template>
	<nuxt-link :to="'/jokes/' + id">
		<div class="joke">
			<p>{{ joke }}</p>
		</div>	
	</nuxt-link>
</template>

<script>

export default{
	name: 'Joke',
	props: ['joke', 'id']
}

</script>

<style>

.joke{
	padding: 1rem;
	border: 1px solid black;
}

.joke p:hover{
	cursor: pointer;
}

</style>
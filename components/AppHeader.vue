<template>
	<header class="header">
		<h1>Dad Jokes</h1>
		<ul>
			<li><nuxt-link to="/">Home</nuxt-link></li>
			<li><nuxt-link to="/jokes">Jokes</nuxt-link></li>
			<li><nuxt-link to="/about">About Us</nuxt-link></li>
			<li><nuxt-link to="/contact">Contact Us</nuxt-link></li>
		</ul>
	</header>
</template>

<script>
	export default{
		name: 'AppHeader'

	}
</script>

<style>

.header{
	background-color:gray;
	display: block;
	min-height: 150px;
}

.header h1{
	display: block;
	float: left;
	color: white;
	margin: 40px 20px;
}

.header ul{
	float: right;
	margin: 40px;
}

.header ul li{
	display: inline-block;	

}

.header ul li a{
	margin: 15px 20px;
	color: white;
	text-decoration: none;
}

.header ul li a:hover{
	color:black;

}

</style>
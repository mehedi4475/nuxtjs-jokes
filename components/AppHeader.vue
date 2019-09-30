<template>
	<header class="header">
		<h1 class="logo-text">URL Shortner</h1>
		<ul>
			<li><nuxt-link to="/">Home</nuxt-link></li>
			<li><nuxt-link to="/about-us">About Us</nuxt-link></li>
			<li><nuxt-link to="/dmca">DMCA</nuxt-link></li>
			<li><nuxt-link to="/faq">FAQ</nuxt-link></li>
			<li><nuxt-link to="/terms-and-condition">Terms and Condition</nuxt-link></li>
			<li><nuxt-link to="/privacy-policy">Privacy Policy</nuxt-link></li>
			<li><nuxt-link to="/contact-us">Contact Us</nuxt-link></li>
		</ul>
	</header>
</template>

<script>
	export default{
		name: 'AppHeader'
	}
</script>
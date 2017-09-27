<template>
	<md-card>
		<md-card-media>
			<img v-bind:src="imageUrl" alt="">
		</md-card-media>
		
		<md-card-header>
			<div class="md-title">{{ fullName }}</div>
			<div class="md-subheader">@{{ userName }}</div>
		</md-card-header>
		
		<md-card-content>
			{{ contents }}
		</md-card-content>
	</md-card>
</template>

<script>
	export default {
		name: 'Feed',
		props: ['imageUrl', 'fullName', 'userName', 'contents']
	}
</script>

<style>
	.md-card {
		margin-bottom: 20px;
	}
</style>
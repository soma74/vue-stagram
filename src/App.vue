<template>
	<div id="app">
		<md-toolbar>
			<md-button class="md-icon-button" v-on:click="toggle">
				<md-icon>menu</md-icon>
			</md-button>
			<h2 class="md-title">
				VueStagram
			</h2>
		</md-toolbar>

		<md-sidenav class="md-left" md-swipeable ref="sidenav">
			<md-list>
				<md-list-item v-on:click.native="toggle" v-for="menu in menus" v-bind:key="menu.path">
					<router-link v-bind:to="menu.path">
						<md-icon>{{ menu.icon }}</md-icon>
						<span>{{ menu.title }}</span>
					</router-link>
				</md-list-item>
			</md-list>
		</md-sidenav>

		<div id="contents">
			<router-view></router-view>
		</div>
	</div>
</template>

<script>
	export default {
		name: 'app',
		data() {
			return {
				menus: [
					{
						path: '/vue-stagram/me',
						icon: 'person',
						title: '내 정보'
					},
					{
						path: '/vue-stagram/feeds',
						icon: 'list',
						title: '내 피드'
					},
					{
						path: '/vue-stagram/search',
						icon: 'search',
						title: '태그 검색'
					}
				]
			}
		},
		methods: {
			toggle () {
				this.$refs.sidenav.toggle()
			}
		}
	}
</script>

<style>
	#contents {
		padding: 16px;
	}
</style>
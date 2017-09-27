<template>
	<div>
		<md-input-container>
			<label for="">태그 검색</label>
			<md-input v-on:input.native="tagName = $event.target.value" v-on:keydown.native.enter="search" ref="inputDom"></md-input>
		</md-input-container>

		<feed v-for="feed in feeds" v-bind:key="feed.id" 
			v-bind:image-url="feed.images.standard_resolution.url" 
			v-bind:full-name="feed.caption.from.full_name" 
			v-bind:user-name="feed.caption.from.username" 
			v-bind:contents="feed.caption.text">
		</feed>
	</div>
</template>

<script>
	import jsonp from 'jsonp'
	import Feed from './Feed'

	export default {
		name: "TagSearch",
		data() {
			return {
				tagName: '',
				feeds: []
			}
		},
		mounted() {
			// this.$refs.inputDom.focus()
		},
		methods: {
			search() {
				if(this.tagName === '')
				{
					return
				}

				const token = localStorage.getItem('token')
				jsonp(`https://api.instagram.com/v1/tags/${this.tagName}/media/recent?access_token=${token}`, null,
					(_, response) => {
						this.feeds = response.data
						console.log(response.data)
					})
			}
		},
		components: {
			Feed
		}
	}
</script>
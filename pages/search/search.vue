<template>
	<view class="page">
		<view class="search-block">
			<view class="search-ico-wrapper">
				<image src="../../static/logo.png" class="search-ico"></image>
			</view>
			<input
				type="text"
				placeholder="搜索预告"
				maxlength="10"
				class="search-text"
				confirm-type="search"
				@confirm="searchMe"
				/>
		</view>
		<view class="movie-list page-block">
			<view class="movie-wrapper" v-for="(movie,index) in movieList" :key="'movie_'+index">
				<image :src="movie.cover" @click="showTrailer(movie.id)" class="like-movie"></image>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				originList: [],
				movieList: [
					{
						id: 1,
						name: "雷神",
						poster: "http://122.152.205.72:88/superhero/MARVEL/Thor3/poster.jpg",
						cover: "http://122.152.205.72:88/superhero/MARVEL/CaptainMarvel/cover.jpg",
						trailer: "http://122.152.205.72:88/superhero/MARVEL/Thor3/trailer.mp4",
						score: 8.3,
						detail: "2018 / 美国 / 科幻 动作",
						actors: "盖尔加朵"
					},
					{
						id: 2,
						name: "雷神2",
						poster: "http://122.152.205.72:88/superhero/MARVEL/Thor3/poster.jpg",
						cover: "http://122.152.205.72:88/superhero/MARVEL/Thor3/cover.jpg",
						trailer: "http://122.152.205.72:88/superhero/MARVEL/Thor3/trailer.mp4",
						score: 8.3,
						detail: "2018 / 美国 / 科幻 动作",
						actors: "盖尔加朵"
					},
					{
						id: 3,
						name: "雷神3",
						poster: "http://122.152.205.72:88/superhero/MARVEL/Thor3/poster.jpg",
						cover: "http://122.152.205.72:88/superhero/MARVEL/Thor3/cover.jpg",
						trailer: "http://122.152.205.72:88/superhero/MARVEL/Thor3/trailer.mp4",
						score: 8.3,
						detail: "2018 / 美国 / 科幻 动作",
						actors: "盖尔加朵"
					},
					{
						id: 4,
						name: "雷神4",
						poster: "http://122.152.205.72:88/superhero/MARVEL/Thor3/poster.jpg",
						cover: "http://122.152.205.72:88/superhero/MARVEL/Thor3/cover.jpg",
						trailer: "http://122.152.205.72:88/superhero/MARVEL/Thor3/trailer.mp4",
						score: 8.3,
						detail: "2018 / 美国 / 科幻 动作",
						actors: "盖尔加朵"
					}
				]
			}
		},
		onLoad() {
			for (var i = 0; i < 3; i++) {
				this.movieList = this.movieList.concat(this.movieList)
			}
			this.originList = this.movieList.concat()
		},
		onReachBottom() {
			uni.showLoading({
				title:"请稍等",
				mask: true
			});
			setTimeout(() => {
				this.pagedTrailerList()
				uni.hideLoading()
			}, 1000);
		},
		methods: {
			pagedTrailerList(){
				if (this.movieList.length < 100){
					this.movieList = this.movieList.concat(this.movieList)
				}
			},
			searchMe(e){
				console.log(e.detail.value)
				if (!e.detail.value){
					this.movieList = this.originList.concat()
				}else{
					this.movieList.splice(Math.random(3), 3)
				}
			},
			showTrailer(id){
				uni.navigateTo({
					url:"../movie/movie?trailerId="+id
				})
			}
		}
	}
</script>

<style>
	@import url("search.css");
</style>

<template>
	<view class="page">
		<view class="player">
			<video
				:src="trailerInfo.trailer"
				:poster="trailerInfo.poster"
				class="movie"
				controls
				>
			</video>
		</view>
		<view class="movie-info">
			<image
				:src="trailerInfo.cover"
				class="cover">
			</image>
			<view class="movie-desc">
				<view class="title">
					{{trailerInfo.name}}
				</view>
				<view class="basic-info">
					{{trailerInfo.detail}}
				</view>
				<view class="basic-info">
					{{trailerInfo.actors}}
				</view>
				<view class="score-block">
					<view class="big-score">
						<view class="socre-words">综合评分:</view>
						<view class="movie-score">{{trailerInfo.score}}</view>
					</view>
					<view class="score-stars">
						<block v-if="trailerInfo.score >= 0">							
							<trailer-stars :rate="trailerInfo.score" :showNum="0"></trailer-stars>
						</block>
						<view class="prise-counts">
							{{trailerInfo.prisedCounts}} 人点赞
						</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import trailerStars from "../../components/tarilerStars.vue"
	export default {
		components:{
			trailerStars
		},
		data() {
			return {
				trailerInfo: {}
			}
		},
		onLoad(params) {
			let traillerId = params.id
			this.trailerInfo = {
				id: 3,
				name: "雷神3",
				poster: "http://122.152.205.72:88/superhero/MARVEL/Thor3/poster.jpg",
				cover: "http://122.152.205.72:88/superhero/MARVEL/Thor3/cover.jpg",
				trailer: "http://122.152.205.72:88/superhero/MARVEL/Thor3/trailer.mp4",
				score: 8.3,
				prisedCounts: 99,
				detail: "2018 / 美国 / 科幻 动作",
				actors: "盖尔加朵"
			}
		},
		methods: {
			
		}
	}
</script>

<style>
	@import url("movie.css");
</style>

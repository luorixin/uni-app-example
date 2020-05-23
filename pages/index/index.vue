<template>
	<view class="page">
		<swiper :indicator-dots="true" :autoplay="true" class="carousel">
			<swiper-item v-for="item in carouselList" :key="item.id">
				<image :src="item.image" class="carousel"></image>
			</swiper-item>
		</swiper>
		<view class="page-block super-hot">
			<view class="hot-title-wrapper">
				<image src="../../static/logo.png" class="hot-ico"></image>
				<view class="hot-title">
					热门电影
				</view>
			</view>
		</view>
		
		<scroll-view scroll-x="true" class="page-block hot">
			<view class="single-poster" v-for="poster in posterList" :key="poster.id">
				<view class="poster-wrapper">
					<image :src="poster.image" class="poster"></image>
					<view class="movie-name">
						{{poster.title}}
					</view>
					<tariler-stars :rate="poster.rate"></tariler-stars>
				</view>
			</view>
		</scroll-view>
		
		<view class="page-block super-hot">
			<view class="hot-title-wrapper">
				<image src="../../static/logo.png" class="hot-ico"></image>
				<view class="hot-title">
					热门预告
				</view>
			</view>
		</view>
		
		<view class="hot-movies page-block">
			<video
				v-for="trailer in movieList"
				:key="trailer.id"
				:src="trailer.trailer"
				:poster="trailer.poster"
				class="hot-movie-single"
				controls>
			</video>
		</view>
		
		<view class="page-block super-hot">
			<view class="hot-title-wrapper">
				<image src="../../static/logo.png" class="hot-ico"></image>
				<view class="hot-title">
					猜你喜欢
				</view>
			</view>
		</view>
		
		<view class="page-block guess-u-like">
			<view class="single-like-movie" v-for="(trailer,index) in movieList" :key="trailer.id">
				<image :src="trailer.cover" class="like-movie"></image>
				<view class="movie-desc">
					<view class="movie-title">
						{{trailer.name}}
					</view>
					<tariler-stars :rate="trailer.score" :showNum="0"></tariler-stars>
					<view class="movie-info">
						{{trailer.detail}}
					</view>
					<view class="movie-info">
						{{trailer.actors}}
					</view>
				</view>
				<view class="movie-opt" :data-gIndex="index" @click="praiseMe">
					<image src="../../static/logo.png" class="praise-ico"></image>
					<view class="praise-me">
						点赞
					</view>
					<view :animation="animationDataArr[index]" class="praise-me animation-opacity">
						+1
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import tarilerStars from "../../components/tarilerStars.vue"
	export default {
		components:{
			tarilerStars
		},
		data() {
			return {
				title: '首页',
				animationData:{},
				animationDataArr: [
					{},{},{},{},{}
				],
				carouselList: [
					{
						id: "1",
						movieId:"marvel-1011",
						image:"http://122.152.205.72:88/group1/M00/00/03/CpoxxFw1ZSiAaDteAAdT5PsVWXs099.png",
						sort: 1,
						isShow:1
					},
					{
						id: "2",
						movieId:"xman-1004",
						image:"http://122.152.205.72:88/group1/M00/00/03/CpoxxFw1ZHiASu_7AAfGb_KNy8Y861.png",
						sort: 2,
						isShow: 1
					}
				],
				posterList:[
					{
						id: 1,
						image:"http://122.152.205.72:88/group1/M00/00/03/CpoxxFw1ZSiAaDteAAdT5PsVWXs099.png",
						title: "蝙蝠侠",
						rate: 10
					},
					{
						id: 2,
						image:"http://122.152.205.72:88/group1/M00/00/03/CpoxxFw1ZHiASu_7AAfGb_KNy8Y861.png",
						title: "神奇女侠",
						rate: 10
					},
					{
						id: 3,
						image:"http://122.152.205.72:88/group1/M00/00/03/CpoxxFw1ZSiAaDteAAdT5PsVWXs099.png",
						title: "蝙蝠侠",
						rate: 9
					},
					{
						id: 4,
						image:"http://122.152.205.72:88/group1/M00/00/03/CpoxxFw1ZHiASu_7AAfGb_KNy8Y861.png",
						title: "蝙蝠侠",
						rate: 6
					},
					{
						id: 5,
						image:"http://122.152.205.72:88/group1/M00/00/03/CpoxxFw1ZSiAaDteAAdT5PsVWXs099.png",
						title: "蝙蝠侠",
						rate: 8
					}
				],
				movieList: [
					{
						id: 1,
						name: "雷神",
						poster: "http://122.152.205.72:88/superhero/MARVEL/Thor3/poster.jpg",
						cover: "http://122.152.205.72:88/superhero/MARVEL/Thor3/cover.jpg",
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
			// uni.request({
			// 	url:'',
			// 	method:'POST',
			// 	success: (res) => {
					
			// 	}
			// })
			// #ifdef APP-PLUS || MP-WEIXIN || H5
				this.animation = uni.createAnimation()
			// #endif
			
		},
		onUnload() {
			this.animationData = {}
			this.animationDataArr = [
				{},{},{},{},{}
			]
		},
		onPullDownRefresh() {
			console.log("刷新")
			uni.showLoading({
				mask:true,
			})
			setTimeout(()=>{
				uni.stopPullDownRefresh()
				uni.hideLoading()
			},1000)
		},
		methods: {
			praiseMe(e){
				// #ifdef APP-PLUS || MP-WEIXIN || H5
				let gIndex = e.currentTarget.dataset.gindex
				
				this.animation.translateY(-60).opacity(1).step({
					duration:400
				})
				// 导出动画到view组件，实现组件的动画效果
				// this.$set(this.animationDataArr, gIndex, this.animation.export())
				this.animationDataArr.splice(gIndex, 1, this.animation.export())
				// this.animationDataArr[gIndex] = this.animationData.export() //不触发响应
				setTimeout(()=>{
					this.animation.translateY(0).opacity(0).step({
						duration:0
					})
					this.$set(this.animationDataArr, gIndex, this.animation.export())
				}, 500)
				//#endif
			}
		}
	}
</script>

<style>
	@import url("index.css");
</style>

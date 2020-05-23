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
					<view class="movie-score-wrapper">
						<image src="../../static/logo.png" class="star-ico"></image>
						<image src="../../static/logo.png" class="star-ico"></image>
						<image src="../../static/logo.png" class="star-ico"></image>
						<image src="../../static/logo.png" class="star-ico"></image>
						<image src="../../static/logo.png" class="star-ico"></image>
						<view class="movie-score">
							{{poster.rate}}
						</view>
					</view>
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: '首页',
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
						rate: 9
					},
					{
						id: 2,
						image:"http://122.152.205.72:88/group1/M00/00/03/CpoxxFw1ZHiASu_7AAfGb_KNy8Y861.png",
						title: "神奇女侠",
						rate: 9
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
						rate: 8
					},
					{
						id: 5,
						image:"http://122.152.205.72:88/group1/M00/00/03/CpoxxFw1ZSiAaDteAAdT5PsVWXs099.png",
						title: "蝙蝠侠",
						rate: 8
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
		},
		methods: {

		}
	}
</script>

<style>
	@import url("index.css");
</style>

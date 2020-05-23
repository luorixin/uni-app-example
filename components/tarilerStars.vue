<template name="tarilerStars">
	<view class="movie-score-wrapper">
		<image 
			v-for="(yellow,index) in yellowScore"
			:key="'yellow'+index"
			src="../static/logo.png" 
			class="star-ico">
		</image>
		<image
			v-for="(gray,index) in grayScore"
			:key="'gray'+index"
			src="../static/logo.png" 
			class="star-ico visibleHide">
		</image>
		<view class="movie-score" v-show="showNum">
			{{rate}}
		</view>
	</view>
</template>

<script>
	export default {
		name: 'tarilerStars',
		props:{
			rate: 0,
			showNum: {
				default: 1,
				type: Number
			}
		},
		data(){
			return {
				yellowScore: 0,
				grayScore: 5,
				totalScore: 5,
			}
		},
		created() {
			let tempScore = 0;
			if(this.rate !== null && this.rate !== undefined && this.rate!==''){
				tempScore = this.rate
			}
			let yellowScore = parseInt(tempScore / 2);
			let grayScore = this.totalScore - yellowScore
			this.yellowScore = yellowScore
			this.grayScore = grayScore
		}
	}
</script>
	
<style>
	
	.movie-score-wrapper{
		display: flex;
		flex-direction: row;
	}
	.star-ico{
		width: 20upx;
		height: 20upx;
		margin: 6upx 1upx 0 1upx;
	}
	.movie-score{
		font-size: 12px;
		color: grey;
		margin-left: 8upx;
	}

</style>

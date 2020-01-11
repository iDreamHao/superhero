<template>
	<view class="page" >
		<swiper :indicator-dots="true" :autoplay="true" class="carousel">
			<swiper-item v-for="carousel in carouselList" :key="carousel.id" >
				<image :src="carousel.image" class="carousel"></image>
			</swiper-item>
		</swiper>
		<view class="page-block super-hot">
			<view class="hot-title-wrapper">
				<image src="../../static/icos/hot.png" class="hot-ico"></image>
				<view class="hot-title">
					热门超英
				</view>
			</view>
		</view>
		<scroll-view scroll-x="true" class="page-block hot">
			<view class="single-poster" v-for="superhero in hotSuperheroList" :key="superhero.id">
				<view class="poster-wrapper">
					<image :src="superhero.cover" class="poster"></image>
					<view class="movie-name">
						{{superhero.name}}
					</view>
					<view class="movie-score-wrapper">
						<image src="../../static/icos/star-yellow.png" class="star-ico"></image>
						<image src="../../static/icos/star-yellow.png" class="star-ico"></image>
						<image src="../../static/icos/star-yellow.png" class="star-ico"></image>
						<image src="../../static/icos/star-yellow.png" class="star-ico"></image>
						<image src="../../static/icos/star-gray.png" class="star-ico"></image>
						<view class="movie-score">
							9.1
						</view>
					</view>
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	import common from "../../common/common.js"
	
	export default {
		data() {
			return {
				carouselList:[],
				hotSuperheroList:[],
			}
		},
		onLoad() {
			var serverUrl = common.serverUrl
			uni.request({
			    url: serverUrl+'json/index-carousel-list.json', 
				method:'GET',
			    success: (res) => {
					// 获取数据之前的判断
					if(res.data.status == 200){
						this.carouselList = res.data.data;
					}
					
			    }
			});
			uni.request({
				url:serverUrl+'json/index-movie-hot-superhero.json',
				method:'GET',
				success: (res) => {
					// 获取数据之前的判断
					if(res.data.status == 200){
						this.hotSuperheroList = res.data.data;
					}
				}
			})
		},
		methods: {

		}
	}
</script>

<style>
	@import url("index.css");

</style>

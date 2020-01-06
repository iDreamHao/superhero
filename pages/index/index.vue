<template>
	<view class="page" >
		<swiper :indicator-dots="true" :autoplay="true" class="carousel">
			<swiper-item>
				<image src="../../static/carousel/spiderman.png" class="carousel"></image>
			</swiper-item>
			<swiper-item>
				<image src="../../static/carousel/batmanvssuperman.png" class="carousel"></image>
			</swiper-item>
		</swiper>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		onLoad() {
			uni.request({
			    url: 'http://next-hero.oss-cn-shanghai.aliyuncs.com/json/index-carousel-list.json', 
				method:'GET',
			    success: (res) => {
			        console.log(res.data);
			    }
			});
		},
		methods: {

		}
	}
</script>

<style>
	@import url("index.css");

</style>

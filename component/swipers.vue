<template>
		<view class="swipers">	
	<view>
	    <view class="uni-padding-wrap">
	        <view class="page-section swiper">
	            <view class="page-section-spacing">
	                <swiper class="swiper" :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval" :duration="duration">
	                    <swiper-item class="a">
	                        <view class="swiper-item uni-bg-red">
								<image style="width: 100%;" mode="widthFix" src="../../static/dinner_food1.jpg"></image>
							</view>
	                    </swiper-item>
	                    <swiper-item class="a">
	                        <view class="swiper-item uni-bg-green">
								<image style="width: 100%;"   src="../../static/dinner_food2.jpg"></image>
							</view>
	                    </swiper-item>
	                    <swiper-item  class="a">
	                        <view class="swiper-item uni-bg-blue">
								<image style="width: 100%;" mode="widthFix" src="../../static/dinner_food3.jpg"></image>
							</view>
	                    </swiper-item>
	                </swiper>
	            </view>
	        </view>
	    </view>
	</view>
		</view>
</template>

<script>
	export default {
		data() {
			 return {
	        background: ['color1', 'color2', 'color3'],
	        indicatorDots: true,
	        autoplay: true,
	        interval: 2000,
	        duration: 500
	    }
	},
	methods: {
	    changeIndicatorDots(e) {
	        this.indicatorDots = !this.indicatorDots
	    },
	    changeAutoplay(e) {
	        this.autoplay = !this.autoplay
	    },
	    intervalChange(e) {
	        this.interval = e.target.value
	    },
	    durationChange(e) {
	        this.duration = e.target.value
	    }
		}
	}
</script>

<style>
	.content {
			text-align: center;
			height: 400upx;
		}
		.swipers{
			/* margin-top:20upx ; */
		}
		.swiper-item{
			width: 100%;
		}
		.a {
			width: 100%;
			height:250upx;
		}
		swiper{
	height:200px
	}
	swiper-item{
	height:200px 
	}
</style>

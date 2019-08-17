<template>
	<view>
		<view class="title">
			<p>订单</p>
		</view>
		<view class="num">
			<p>订单号: 1950013-17/11/2017-369 <br>{{time}}</p>
		</view>
		<view class="jagged">
			<p>原味板烧鸡腿堡中套餐</p>
			<p>原味板烧鸡腿堡</p>
			<p>小玉米杯</p>
			<p>海盐柠檬苏打风味汽水</p>
		</view>
		<view class="infos">
			<p>实际价格以在餐厅结账时为准</p>
		</view>
		<p>共计{{nums}}元</p>
		 <button type="warn">确认下单</button>
		<!-- <view class="jagged"></view> -->
	</view>
</template>

<script>
	export default {
		data() {
			return {
				nums:0,
				tiem:'2017-11-17,19:42:39'
			}
		},
		computed: {
			time(){
				var date = new Date();
				console.log(date)
				return date
			},
			nums(){
				return this.$store.state.count
			}
		},
		methods: {
			
		}
	}
</script>

<style>
	page{
		background:#F5F5F5;
		font-size: 15rpx;
	}
</style>
<style lang="scss">
.title {
	padding: 2%;
	// border:1px solid;
p {
	text-align: center;
	font-size: 36upx;
}
}
.num {
	width: 75%;
	margin: 2% auto;
	padding: 2%;
	line-height:40rpx;
	background: white;
	 border: 2px solid #ccc;
}
.content{
	width: 75%;
	margin: 2% auto;
	padding: 2%;
	line-height:40rpx;
	background: white;
	border: 1px solid;
	height: 180rpx;
}

.infos {
	p {
		text-align: center;
	}
	margin: 3% 0;
}
.jagged {
    height: 200upx;
    border: 2px solid #ccc;
    border-bottom: none;
    position: relative;
	width: 75%;
	margin: 2% auto;
	padding: 2%;
	line-height:40rpx;
	background: white;
	height: 180rpx;
	margin-bottom:8%;
}

.jagged:after {
    content: '';
    display: block;
    height: 10px;
    background-size: 20px 20px;
    background-repeat: repeat-x;
    background-image: linear-gradient(135deg, transparent 45%, #ccc 55%, transparent 60%), linear-gradient(45deg, transparent 45%, #ccc 55%, transparent 60%);
    position: absolute;
    bottom: -19upx;
    left: 0;
    right: 0;
}
.infos {
	margin-bottom:5%;
}
</style>

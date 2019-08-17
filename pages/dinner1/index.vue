<template>
	<view id="main">
		<view class="head">
			<image style="width: 100%;object-fit: cover;" src="../../static/poster.jpg"></image>
		</view>
		<view style="display: flex;flex-direction: row;justify-content: space-evenly;">
			<view class="content">
				<ul class="items" v-for="(item,index) in goodnameLists" :key="index" @click="check(index)" v-bind:class="{active:index==isActive}">
					<li class="goodSorts">
						<p>
							{{item.goodsnameSorts}}
						</p>
					</li>
				</ul>
			</view>
			
			<view class="tab-content">
        <view v-for="(item,index) in goodLists" :key="index" v-show="cur==index">
			<view class="gun" v-on="article">
				<view style="display: flex;flex-direction: inherit;justify-content: inherit;">
					<image style="width: 50%;height:50%;object-fit: cover;" :src="item.pics"></image>
					<ul class="item_details" style="font-size:12upx">
						<li style="font-size: 18upx;">{{item.food_name}}</li>
						<li style="font-size:12upx">{{item.food_details}}</li>
						<li style="display:flex;flex-direction: row; justify-content: flex-start; width: 90%;"><span style="margin-right:15upx;line-height: 57upx;color: red;">￥{{item.price}}</span><span @click="desc(num,index)" style="margin-top:12upx;border:1px solid;height:7vw;width: 7vw;line-height:50upx;position: relative;bottom: 12upx;">-</span><span><input v-model="item.nums" placeholder="0" style="width: 60upx;text-align:center;border: 1px solid;" /></span><span @click="add(num,index)" style="border:1px solid;height:7vw;width: 7vw;line-height:50upx;position: relative;bottom: 11.6upx;margin-top:11upx">+</span></li>
					</ul>
					<!-- <p style="font-size: 8upx;">鸡肉+鸡蛋+酸奶+番茄+米粉</p> -->
				</view>
				<view style="1upx solid black"></view>
						
			</view>
		</view>
    </view>
		</view>
	
			<view class="shopping_details">
				<view>
					<p>已选商品 {{num}} 件</p>
					<p>{{goods}}</p>
					<!-- <p>{{food_menu}} + {{details_num}}</p> -->
				</view>
			</view>
			<view class="shopping">
				<view class="car">
					<view class="car_num">
						<p>{{num}}</p>
					</view>
					<image style="width: 50upx;height:50upx;z-index: 9999;object-fit: cover;" src="../../static/shopping.png"></image>
				</view>
				<view class="infos">
					<p>共选购了{{num}}件商品 共 <span v-on="change(total)">{{total}}</span> 元</p>
					<p>另需配送费3元</p>
				</view>
				<view @click="goto()" v-bind:class="{chao:isChao}" class="addition">
					<p>{{buyText}}</p>
				</view>
				
			</view>
	</view>
	
</template>

<script>
	export default {
		data() {
			return {
				isChao:false,
				isActive:0,
				goods:'',
				num:'',
				buyText:'15元起送',
				// nums:0,
				total:0,
				goodnameLists:[
					{goodsnameSorts:'超值特价',pics:'../../static/dinner_food1.jpg',food_name:'牛扒'},
					{goodsnameSorts:'每日新品'},
					{goodsnameSorts:'经典爆款'},
					{goodsnameSorts:'单点系列'},
					{goodsnameSorts:'汉堡系列'},
					{goodsnameSorts:'肉卷系列'},
					{goodsnameSorts:'夏日新饮'},
					{goodsnameSorts:'清爽甜品'},
					{goodsnameSorts:'满分系列'},
					{goodsnameSorts:'夏日新饮'},
					{goodsnameSorts:'清爽甜品'},
					{goodsnameSorts:'满分系列'},
					{goodsnameSorts:'调料系列'}
				],
				tabMain: [{'title':'超值特价'},{'title':'每日新品'},{'title':'经典爆款'}],
                cur: 0 ,//默认选中第一个tab
				goodLists:[{
					pics:'../../static/dinner_food1.jpg',food_name:'超值简餐',price:'18',nums:0,food_details:'鸡肉+蛋+酸奶+番茄'
				},
				{
					pics:'../../static/dinner_food2.jpg',food_name:'盖饭',price:'20',nums:0,food_details:'鸡肉+火腿+米饭+饮料'
				},{
					pics:'../../static/dinner_food3.jpg',food_name:'牛扒',price:'18',nums:0,food_details:'牛肉+薯条+意大利面'
				},{
					pics:'../../static/dinner_food1.jpg',food_name:'营养中餐',price:'35',nums:0,food_details:'鸡肉+番茄+鸡蛋+生菜'
				},{
					pics:'../../static/dinner_food1.jpg',food_name:'牛扒',price:'55',nums:0
				},{
					pics:'../../static/dinner_food1.jpg',food_name:'牛扒',price:'15',nums:0
				},{
					pics:'../../static/dinner_food1.jpg',food_name:'牛扒',price:'75',nums:0
				}]
			}
		},
		computed: {
			article(){
				if(this.cur == 0) {
					// alert('hahah')
				}
			}
		},
		methods: {
			check(index){
				this.cur = index
				this.isActive = index
			},
			desc(num,index) {
				if(this.total>0){
					this.total = parseInt(this.total) - parseInt(this.goodLists[index].price) 
				}
				console.log(num)
				if(this.goodLists[index].nums > 0 && num > 0 ){
					this.num --
					this.goodLists[index].nums--
				}
			},
			change(total){
				if(total > 15) {
					this.isChao = true;
					this.buyText = '去结算'
				}else{
					this.isChao = false;
					this.buyText = '15元起送'
				}
				
				this.$store.state.count = total
				console.log(this.$store.state.count)
			},
			goto(){
				uni.navigateTo({
                    url: '../shopping/shopping',
                    success: res => {},
                    fail: () => {},
                    complete: () => {}
                });
			},
			add(num,index) {
				console.log(this.goodLists[index].nums)
				// this.goodLists[index].price
				this.total = parseInt(this.total) + parseInt(this.goodLists[index].price) 
				console.log(this.total)
				this.goodLists[index].nums++
				this.num++
			},
			title(index) {
				console.log(this)
			}
		}
		
	}
</script>

<style lang="scss" scoped>
	* {
		margin: 0;
		padding: 0;
	}
	ul,li {
		list-style: none;
	}
	.gun {
		height: 500upx;
		overflow-y:auto;
		view{
			height: 500upx;
			overflow-y:auto;
		}
	}
	.active {
		opacity: 1;
		color: orangered;
		width: 120upx;
			border-bottom:1px sandybrown solid;
	}
	.tab-content{
		// border: 1px solid red;
		width:70%;
	}
	.content {
		width: 15%;
		padding-right:3%;
		overflow:auto;
		height:400upx;
		border-right:lightgray 1px solid;
		// display: flex;
		// flex-direction: inherit;
		// border: 1px solid;
		.items {
			// border: 1px solid;
			width: 100%;
			
			p {
				text-align: center;
			}
		}
		
		margin-bottom: 15vw;
		
	}
	.shopping {
		padding: 5upx;
		// border: 1px solid;
		height:15vw;
		width: 100%;
		position: fixed;
		margin-top: 15%;
		bottom: 13.2vw;
		background: #100F14;
		display: flex;
		justify-content: inherit;
		flex-direction: row;
		.car_num {
			border-radius: 100%;
			position: absolute;
			top: 15%;
			width:3%;
			height: 20%;
			left: 6%;
			background: yellow;
			border: 1px solid yellow;
			p {
				font-size: 12upx;
				color: brown;
				text-align: center;
				position: relative;
				bottom:8upx;
				font-weight: bold;
			}
		}
		.infos {
			margin-top: 3%;
			margin-left: 2%;
			font-size: 10upx;
			// border: 1px solid white;
			color: white;
			}
			.addition {
				width: 26%;
				height:100%;
				position: absolute;
				bottom: 0;
				right: 0;
				border: 1px solid wdarkorange;
				background: darkorange;
				p {
					margin-top: 16%;
					
					text-align: center; 
					color: white;
				}
			}
			.chao {
				background: darkred;
			}
	}
.goodSorts {
	list-style: none;
	width: 120upx;
	line-height: 85upx;
	// border-right:1px sandybrown solid;
	text-align: center;
	letter-spacing: 3upx;
		p {
			
			font-size:12upx
		}
}
.item_details {
	margin-left: 5%;
	li {
		text-align: center;
		margin: 15% 0;
	}
}
.car {
	height: 60%;
	width: 10%;
	margin-left: 2%;
	margin-top: 2.5%;
	// border: 1px solid white;
	border-radius: 100%;
	image {
		margin-top: 10%;
		margin-left: 14%;
	}
}
.shopping_details {
	width:350upx;
	// height:160upx;
	border:1px solid;
	background: white;
	z-index: 99999;
	position: relative;
	// bottom: 85upx;
	p {
		font-size: 12upx;
	}
}
</style>

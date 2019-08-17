<template>
	<view class="content">
		<swipers></swipers>
		<view class="pic_box" >
			<view v-for="(item,index) in list" :key="index" class="pic_item">
				<view class=".pic_item"><image style="width: 30vw;height:30vw;object-fit: cover;" :src="item.pic"></image></view>
			</view>
		</view>
	</view>
</template>

<script>
	import swipers from '../../component/swipers.vue'
	export default {
		data() {
			 return {
            list:[{pic:'../../static/item1.png',num:'1'},
				  {pic:'../../static/item2.png',num:'1'},
				  {pic:'../../static/item3.png',num:'1'},
				  {pic:'../../static/item4.png',num:'1'},
				  {pic:'../../static/item5.png',num:'1'},
				  {pic:'../../static/item6.png',num:'1'},
				  {pic:'../../static/item7.png',num:'1'},
				  {pic:'../../static/item8.png',num:'1'},
				  {pic:'../../static/item3.png',num:'1'}]
        }
    },
	onLoad() {
		
	},
	components: {
		swipers
	},
    methods: {
       
		}
	}
</script>

<style>
	.content {
		text-align: center;
		height: 400upx;
	}
.pic_box {
	margin: 5upx auto;
	width:100vw;
	height:100vw;
	 display: flex;
    justify-content:space-evenly;
	align-content: space-around;
    /* justify-content:center; */
    flex-flow: row wrap;
	/* border: 1px solid; */
    flex-wrap: wrap;

       /* justify-content: space-between;
        /* justify-content:center; 
        flex-flow: row;
        flex-wrap: wrap; */
}
.pic_item {
	align-items:center;
	width: 30vw;
	height:30vw;
	font-size: 12upx;
}
</style>

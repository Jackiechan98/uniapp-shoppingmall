<template>
	<view class="content">
		
		<!--Search bar-->
		<view class="cu-bar search bg-white">
			<view class="search-form round">
				<text class="cuIcon-search"></text>
				<input v-model="search" placeholder=""/>
			</view>
		</view>
		
		<!--Tab-->
		<view>
			<scroll-view class="nav bg-white" scroll-x>
				<view class="flex text-center">
					<view :class="thistab==index?'text-blue cur':''" @click="Switch(index)" v-for="(item,index) in TabLists" :key="index" class="cu-item flex-sub">
						{{item}}
					</view>
				</view>
			</scroll-view>
		</view>
		
		<!---->
		<view style="margin-top:2upx;">
			<view style="padding:20upx 20upx 20upx 1upx;border-bottom: 1upx solid #e7e7e7;"class="flex justify-around bg-white" v-for="(p,i) in goodsLists" :key="i" >
				<view style="width: 300upx;">
					<image style="width: 180upx;height: 240upx;margin-left: 70upx;" :src="p.url"></image>
				</view>
				<view style="width: 440upx; margin-top: 35upx;borflex-direction: column; " >
					<view style=" font-size: 110%;">
						{{p.title}}
					</view>
					<view style="font-size: 130%;padding-top: 10upx;">
						<text style="color: #06618c;"><text style="font-size: 85%;">$</text>{{p.price}}</text>
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
				search:"",
				TabLists:["Hot","Fruit","Vegetable","Meat"],
				thistab:0,
				goodsList:[],
			}
		},
		onLoad() {
			this.getgoodsLists();
		},
		methods: {
			Switch(index){
				this.thistab=index
			},
			
			getgoodsLists(){
				var data=[];
				for(var i=0;i<10;i++){
					var p={
						id:1,
						title:'Apple iPhone 11 (128GB) - Purple (SIM-Free)',
						url:"../../static/icon/1.png",
						price:600,
						
					}
					data.push(p);
				}
				this.goodsLists=data;
			}
		}
	}
</script>

<style>
	/* .content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	} */
</style>

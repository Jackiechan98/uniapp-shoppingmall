<template>
	<view>
		<view class="cu-bar bg-white">
			<view @tap="backtogoods()" class="action">
				<text class="cuIcon-back text-gray"> Back</text>
			</view>
		</view>
		<!--zhanwei-->
		<!--Search bar-->
		<view>
			<!-- 			<swiper style="height:500upx;">
				<swiper-item v-for="(p, i) in  banners" :key="i">
					<image model="widthFix" class="bannerimg" :src="p.url"></image>
				</swiper-item>
			</swiper> -->

			<!-- 			<swiper style="height:500upx;">
				<swiper-item v-for="item in  swiperList" :key="item.id">
					<img class= "swiper-img" src="pagination"/>
				</swiper-item>
			</swiper> -->
		</view>
		<!--Basic information-->
		<!-- 		<view>
			<view>{{detail.price}}</view>
		</view>
		
		<view>
			<view>{{detail.name}}</view>
		</view> -->

		<div align="center">
			<image src="../../static/goods/gigabyte-3070.png"></image>
		</div>

		<view class="cu-bar bg-white">
			<div class="text-bold">
				<text style="font-size: 22px;color: #09a3ea;"> Price:$599.00</text>
			</div>

		</view>

		<view class="cu-bar bg-white">
			<div><text style="font-size: 18px;font-weight: bold;color: #000000;margin: 1px;">Gigabyte GeForce RTX 2070 Super Gaming OC White 8G Graphics Card, 3x WindForce Fans, 8GB 256-Bit GDDR6, GV-N207SGamingOC White-8GD Video Card</text></div>

		</view>

		<view class="cu-bar bg-white">
			<div><text style="font-size: 20px;font-weight: bold;color: #000000;">Product describtion:</text></div>
		</view>
		</Br>

		<view style="margin-left: 10px;margin-right: 10px;">
			About this item
			<li>Powered by GeForce RTX 2070 Super</li>
			<li>NVidia Turing architecture & real time ray tracing</li>
			<li>Wind force 3x cooling system with alternate spinning fans</li>
			<li>Intuitive controls with AORUS engine</li>
			<li>Core clock 1815 MHz</li>
			
			</br></br></br></br></br>

		</view>


		<view class="cu-bar barfixed bg-white tabbar border shop justify-between">
			<view class="action">
				<view class="cuIcon-cart">

				</view>

			</view>
			<view><button @tap="gotocart()" class=" bg-gradual-blue round submit" style="width: 400upx;"><text style="font-size: 20px;">Add to cart</text></button></view>
		</view>


	</view>
</template>

<script>
	export default {
		data() {
			return {
				// swiperOptions:{
				// 	pagination:".swiper-pagination",
				// 	loop:true
				// },
				// swiperList:[
				// 	{
				// 		id:'001',
				// 		imgUrl:require('')
				// 	}
				// ]
				goods_id: "",
				detail: {},
				banners: [],
			}
		},
		methods: {
			getdata() {
				uni.request({
					url: this.$url + "/goods/detail",
					data: {
						id: this.goods_id
					},
					method: "GET",
					success: (res) => {
						this.banners = res.data.banners;
						this.details = res.data.details;
						console.log(this.detail) //
					}
				})
			},
			backtogoods() {
				uni.switchTab({
					url: "../goods/goods"
				})
			},
			gotocart() {
				uni.switchTab({
					url: "../carts/carts"
				})
			}
		},
		onLoad(options) {
			this.goods_id = options.id;
			this.getdata();
		},

	}
</script>

<style>
	div {
		margin: 10px;
	}

	.barfixed {
		position: fixed;
		width: 750upx;
		bottom: 0upx;
		height: 10upx;
	}

	.zhanwei {
		width: 620upx;
		height: var(--status-bar-height);
	}

	.bannerimg {
		width: 620upx;
		height: 5px;

	}
</style>

<template>
	<view class="content">

		<!--Search bar-->
		<view class="nav" style="position: fixed;top: 0;width: 100%;z-index:9999">
			<view class="cu-bar search bg-white">
				<view class="search-form round">
					<text class="cuIcon-search"></text>
					<input v-model="search" placeholder="" />
				</view>
			</view>

			<!--Tab-->
			<view style="">
				<scroll-view class="nav bg-white" scroll-x>
					<view class="flex text-center">
						<view :class="thistab==index?'text-blue cur':''" :style="{color:thistab==index?'#06618c':''}" @click="Switch(index)"
						 v-for="(item,index) in TabLists" :key="index" class="cu-item flex-sub">
							{{item}}
						</view>
					</view>
				</scroll-view>
			</view>
		</view>

		<!---->
		<view style="margin-top:190upx;">
			<view style="padding:20upx 20upx 20upx 1upx;border-bottom: 1upx solid #e7e7e7;" class="flex justify-around bg-white"
			 v-for="(p,i) in goodsLists1" :key="i">
				<view style="width: 300upx;">
					<image style="width: 180upx;height: 240upx;margin-left: 70upx;" :src="p.url"></image>
				</view>
				<view style="width: 440upx; margin-top: 35upx;borflex-direction: column; ">
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
				search: "",
				TabLists: ["Hot", "Fruit", "Vegetable", "Meat"],
				thistab: 0,
				goodsList1: [],
			}
		},
		onLoad() {
			this.getgoodsLists1();
		},
		methods: {
			Switch(index) {
				this.thistab = index
			},

			getgoodsLists1() {
				var data = [{
					id: 1,
					url: "../../static/icon/1.png",
					title: "Apple iPhone 11 (128GB) - Purple (SIM-Free)",
					price: 600,
					num: 1,
				}, {
					id: 2,
					url: "../../static/icon/2.png",
					title: "Apple iPhone 8 Plus [64GB, Silver] + Carrier Subscription [Cricket Wireless]",
					price: 700,
					num: 2,
				}, {
					id: 3,
					url: "../../static/icon/3.png",
					title: "Apple iPhone XR, 256GB, Black - Fully Unlocked (Renewed)",
					price: 650,
					num: 1,
				}, {
					id: 4,
					url: "../../static/icon/1.png",
					title: "Apple iPhone 11 (128GB) - Purple (SIM-Free)",
					price: 600,
					num: 1,
				}, {
					id: 3,
					url: "../../static/icon/3.png",
					title: "Apple iPhone XR, 256GB, Black - Fully Unlocked (Renewed)",
					price: 650,
					num: 1,
				}];
				this.goodsLists1 = data;
			}
		}
	}
</script>

<style>
</style>

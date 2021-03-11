<template>
	<view>
		<!--Search bar-->
		<view class="cu-bar search bg-white">
			<view class="search-form round">
				<text class="cuIcon-search"></text>
				<input v-model="search" placeholder="" />
			</view>
		</view>

		<view class="flex">
			<scroll-view scroll-y style="height: calc(100vh - 194upx); width: 180upx;">

				<view @tap="select(i)" :style="{color:selected==i?'#06618c':'',fontSize:selected==i?'100%':'100%'}" :class="selected==i?'bg-white':''"
				 class="type-item" v-for="(p,i) in types" :key="i">
					{{p}}
				</view>
			</scroll-view>
			<scroll-view scroll-with-animation :scroll-into-view="'good-'+selected" class="bg-white" scroll-y style="height: calc(100vh - 194upx); width: 570upx;">
				<view :id="'good-'+i" style="border-bottom: 0.5upx #E7E7E7 solid;padding-bottom: 40upx;" v-for="(p,i) in goods" :key="i">
					<view class="g-title">{{types[i]}}</view>
					<view class="flex flex-wrap">
						<view class="flex justify-center align-center" style="width: 275upx;margin-top: 10upx;" v-for="(tp,ti) in p" :key="ti">
							<view>
							<image style="width: 170upx;height: 220upx;" :src="tp.url"></image>
							
							<view style="text-align: center;">{{tp.name}}</view>
							
							
							</view>
						</view>
					</view>
				</view>
			</scroll-view>
		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				search: "",
				types: [],
				goods: [],
				selected: 0
			}
		},
		methods: {
			gettypes() {
				var data = [];
				for (var i = 0; i < 5; i++) {
					data.push("type" + i)
				}
				this.types = data;
			},

			getgoods() {
				var data = [];
				for (var i = 0; i < 13; i++) {
					var p = [];
					p.push({
						url: "../../static/icon/1.png",
						name: this.types[i] + i,
						price: 1 * 2
					})
					p.push({
						url: "../../static/icon/2.png",
						name: this.types[i] + i,
						price: 1 * 2
					})
					p.push({
						url: "../../static/icon/3.png",
						name: this.types[i] + i,
						price: 1 * 2
					})
					data.push(p)
				}
				this.goods = data;
			},

			select(i) {
				this.selected = i
			}
		},

		onLoad() {
			this.gettypes()
			this.getgoods()
		}
	}
</script>

<style>
	.type-item {
		height: 100upx;
		text-align: center;
		line-height: 100upx;
	}
	
	.g-title{
		font-size: 120%;
		margin-top: 30upx;
		margin-bottom: 20upx;
		margin-left: 30upx;
	}
</style>

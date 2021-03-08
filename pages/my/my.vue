<template>
	<view>
		
		<!--top-->
		<view class="flex bg-white content1">
			<view class="flex justify-between">
				<view><image class="user-logo" src="../../static/client.jpg"></image></view>
				<view style="margin-left: 20upx;margin-top: 7upx;">
					<view class="user-name" >Ben</view>
					<view style="font-size: 130%;"> Id:10001</view>
				</view>
			</view>
		</view>
		<!--top end-->
		
		<!--order status-->
		<view class="flex justify-center">
			<view class="bg-white flex justify-around" style="width: 880upx;height: 150upx;border-top: 1upx solid #e7e7e7;padding-top: 25upx;">
				<view style="position: relative;" class="flex align-center flex-direction" v-for="(p,i) in orders" :key="i">
					<view :class="p.icon" style="font-size: 60upx;color: grey;">
						
					</view>
					<view v-if="p.num!=0" style="position: absolute;top:1px;right: 2px;" class="cu-tag bg-grey round sm">
						{{p.num}}
					</view>
					<view>
						{{p.text}}
					</view>
				</view>
			</view>
		</view>
		<!--end of order status-->
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				orders:[
					{
						text:"Pending",
						icon:"cuIcon-pay",
						num:1,
						id:1
					},
					{
						text:"Holding",
						icon:"cuIcon-pay",
						num:0,
						id:2
					},
					{
						text:"Shipped",
						icon:"cuIcon-deliver",
						num:0,
						id:3
					},
					{
						text:"Canceled",
						icon:"cuIcon-deliver",
						num:0,
						id:4
					},
					
				]
			}
		},
		methods: {
			
		}
	}
</script>

<style>
.user-logo{
	width: 130upx;
	height: 130upx;
}

.content1{
	padding: 30upx 30upx 30upx 30upx;
}
.user-name{
	font-size: 130%;
}
</style>

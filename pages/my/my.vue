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
		<view class="flex justify-center flex-direction bg-white" style="border-top: 1upx solid #e7e7e7;">
			<view class="flex justify-between " style="width: 93%;margin-top: 15upx;" >
				<text> </text>
				<text style="color:grey">All orders</text>
			</view>
			<view class="bg-white flex justify-around" style="width: 730upx;height: 140upx;padding-top: 16upx;">
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
		
		<view class="list-content total flex justify-between align-center">
			<view></view>
			<view @tap="gopage()" class="bg-white list-item" style="font-size: 110%;color:#747373;">Log out <text style="padding-left: 10upx; font-family: monospace; font-size: 130%;"> </text></view>
			
		</view>
		
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
			gopage(item){
				console.log(item);
				uni.reLaunch({
					url:"../login/login"
				})
			}
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

.total{
	position: fixed;
	bottom: 90upx;
	width: 750upx;
	height: 90upx;
	background-color: white;
	padding-left: 30upx;
	padding-right: 35upx;
}
</style>

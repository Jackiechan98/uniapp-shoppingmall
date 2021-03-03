<template>
	<view>
		<view class="header" style="padding-top: 20upx;padding-bottom: 20upx;">Shopping cart</view>
		<view class="operate">
			<view>
				<checkbox-group class="flex align-center" @change="changeAll">
				<checkbox :checked="checked" :class="checked==true?'checked':''" class=" blue round" style="zoom:70%"></checkbox>
				<text style="font-size: 110%; margin-left: 15upx; color:#747373">Select all</text>
				</checkbox-group>
			</view>
			<view>
				<view class="cu-btn sm round" style="color: #747373;">Delete</view>
			</view>
		</view>
		
		<view class="total flex justify-between align-center">
			<view style="font-size: 110%;color:#747373;">Subtotal <text style="padding-left: 10upx; font-family: monospace; font-size: 130%;"> $600</text></view>
			<view>
				<view class="cu-btn bg-gradual-blue round" >Checkout</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				checked:true
			}
		},
		methods: {
			changeAll(e){
				this.checked?this.checked=false:this.checked=true;
			}
		}
	}
</script>

<style>
	
.header{
	text-align: left;
	font-size: 170%;
	background-color: white;
	font-family: monospace;
	padding-left: 20upx;
	border-bottom: 1upx solid #e7e7e7
}
	
.operate{
	position: fixed;
	background-color: white;
	display: flex;
	justify-content: space-between;
	height: 80upx;
	align-items: center;
	width: 750upx;
	padding-left: 30upx;
	padding-right: 30upx;
}

.total{
	position: fixed;
	bottom: 100upx;
	width: 750upx;
	height: 100upx;
	background-color: white;
	padding-left: 30upx;
	padding-right: 20upx;
}
</style>

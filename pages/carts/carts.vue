<template>
	<view>
		<view class="header" style="padding-top: 20upx;padding-bottom: 20upx;">Shopping cart</view>
		
		<!--operate-->
		<view class="operate">
			<view>
				<checkbox-group class="flex align-center" @change="changeAll">
				<checkbox :checked="checked" :class="checked==true?'checked':''" class=" blue round" style="zoom:70%"></checkbox>
				<text style="font-size: 110%; margin-left: 15upx; color:#747373">Select all</text>
				</checkbox-group>
			</view>
			<view>
				<view @tap="deleteAll" class="cu-btn sm round" style="color: #747373;">Delete</view>
			</view>
		</view>
		
		<!--maincart-->
		<view class="cart-content">
			<view v-for="(p,i) in lists" :key="i" class="cart-item bg-white" >
				<view class="flex align-center" style="width: 280upx;">
					<checkbox-group>
					<checkbox @tap="changeChecked(i)" :checked="p.checked" :class="p.checked==true?'checked':''" class=" blue round" style="zoom:70%;"></checkbox>
					</checkbox-group>
					<image :src="p.img"></image>
				</view>
				<view style="width: 450upx;" class="cart-ycontent">
					<view class="cart-title">{{p.title}}</view>
					<view>
						<view class="flex justify-between">
							<view style="font-size: 120%;color:#747373;">${{p.price}}</view>
							<uni-number-box @change="noofchanges" v-model="p.num" style="margin-right: 24upx;" :min="0" :max="999"></uni-number-box>
						</view>
					</view>
				</view>
			</view>
		</view>
		
		<!--total-->
		<view class="total flex justify-between align-center">
			<view style="font-size: 110%;color:#747373;">Subtotal <text style="padding-left: 10upx; font-family: monospace; font-size: 130%;"> ${{sum}}</text></view>
			<view>
				<view class="cu-btn bg-gradual-blue round" >Checkout</view>
			</view>
		</view>
	</view>
</template>

<script>
	import uniNumberBox from "@/components/uni-number-box/uni-number-box.vue"
	export default {
		data() {
			return {
				checked:false,
				lists:[],
			}
		},
		components:{uniNumberBox},
		
		computed: {
			sum(){
				var s=0
				this.lists.forEach(p=>{
					if(p.checked==true){
						s+=p.num*p.price
					}
				})
				return s.toFixed(2);
			}
		},
		
		methods: {
			
			deleteAll(){
				this.lists=this.lists.filter(p=>{
					return !p.checked;
				})
			},
			
			changeChecked(index){
				this.lists[index].checked=this.lists[index].checked?false:true;
				var selected=this.lists.filter(p=>{return !p.checked});
				selected.length==0?this.checked=true:this.checked=false;
				// if(this.lists[index].checked==false){
				// 	this.checked=false
				// }
				
				// var x=0;
				// for(var n of this.lists){
				// 	if(n.checked==true){
				// 		x+=1
				// 		if(x==this.lists.length){
				// 			this.checked=true
				// 		}
				// 	}
				// }
				
				
				// for(this.lists[index] of this.lists){
				// 	if(this.lists[index].checked==true){
				// 		n++
				// 		// if(n==this.lists.length){
				// 		// 	this.checked=true
				// 		// }
				// 	}
				// }
				
				
			},
			
			changeAll(e){
				this.lists.forEach(p=>{
					p.checked=!this.checked;
				})
				
				this.checked?this.checked=false:this.checked=true;
			},
		
			noofchanges(val){
				val=parseInt(val)
				if(val==0){
					var thisdata=this.lists.find(p=>{
						return p.num==0;
					})
					var its=this;
					uni.showModal({
						confirmText:"Yes",
						confirmColor:"#636363",
						cancelColor:"#636363",
						content:"Are you absolutely sure to delete it",
						title:"Warning",
						cancelText:"Cancel",
						success(res){
							if(res.confirm){
								console.log(res)
								if(res.confirm){
									its.lists=its.lists.filter(p=>{
										return p.id!=thisdata.id;
									})
								}
							}
						}
					})
				}
			},
			
			
			onLoad(){
				this.getdata()
			},
			
			
			
			
			
			getdata(){
				var data=[{
					id:1,
					img:"../../static/icon/1.png",
					title:"Apple iPhone 11 (128GB) - Purple (SIM-Free)",
					price:600,
					num:1,
					checked:false
				},{
					id:2,
					img:"../../static/icon/2.png",
					title:"Apple iPhone 8 Plus [64GB, Silver] + Carrier Subscription [Cricket Wireless]",
					price:700,
					num:2,
					checked:false
				},{
					id:3,
					img:"../../static/icon/3.png",
					title:"Apple iPhone XR, 256GB, Black - Fully Unlocked (Renewed)",
					price:650,
					num:1,
					checked:false
				},{
					id:4,
					img:"../../static/icon/1.png",
					title:"Apple iPhone XR, 256GB, Black - Fully Unlocked (Renewed)",
					price:650,
					num:1,
					checked:false
				}];
				this.lists=data
			},
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
	border-bottom: 1upx solid #e7e7e7;
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
	border-bottom: 1upx solid #e7e7e7
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

.cart-content{
	margin-top: 80upx;
	margin-bottom: 200upx;
}

.cart-item{
	display: flex;
	justify-content: space-between;
	padding: 20upx 20upx 20upx 20upx;
	margin-top:1upx;
}

.cart-item image {
	width: 180upx;
	height: 240upx;
	padding-left: 8upx;
}

.cart-item checkbox{
	margin-left: 20upx;
}

.cart-title{
	font-size: 110%;
	padding-top: 30upx;
	overflow: hidden;
}

.cart-ycontent{
	display: flex;
	flex-direction: column;
	justify-content: space-between;
	padding-top: 8upx;
	
	padding-bottom: 8upx;
	margin-bottom: 20upx;
}

</style>

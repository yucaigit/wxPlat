<template>
	<view class="page1">
		<view class="box" v-for="(item,i) in messageList" :key="i">
			<view class="names">{{item.buyname}}</view>
			<image src="../../static/tab_icons/my_active.png" class="img"/>
			<view class="box2">
			<view class="neiron">
				<input :value="item.message"/>
			</view>
			</view>
		</view>
		
		
		<view class="myneiron">-------------</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:0,
				messageList:[],
				ms:'9ddddddddddd',
				msg:[]
			};
		},
		onLoad(options) {
			this.id=options.id
			this.getMymessage()
		},
		methods:{
			
			async getMymessage(){
				let result = await this.$request('/message/getMessage?id='+this.id)
				this.messageList = result
				console.log(result)
			},
			
		}
	}
</script>

<style lang="scss">
	.img{
		height: 100rpx;
		width: 100rpx;
		border-radius: 2px;
	}
	.names{
		font-size: 23rpx;
	}
	.box{
		display: flex;
		margin: 10rpx;
		width: auto;
	}
	.box2{
		width: auto;
		height: 100rpx;
		border-radius: 10rpx;
		background-color: #EAEAEA;
	}
</style>

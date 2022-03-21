<template>
	<view class='box-wrapper'>
		<view class="box-content">
			<view class='box-person'>
				<image class='box-content_profile' :src="profile.image"></image>
				<text class='box-content_name'>{{profile.name}}</text>
			</view>
			<view class='box-content_score'>{{profile.score}}</view>
			<view class='box-content_detail'>{{profile.content}}</view>
		</view>
		<result :dataVisual='dataVisual'></result>
	</view>
</template>

<script>
	import result from '../../component/common/result.vue'
	// const 
	export default{
		components:{
			result
		},
		data(){
			return{
				profile:{
					image:require('../../static/logo.png'),
					name:"李强",
					score:88,
					content:"周平均心情指数"
				},
				dataVisual:[
					{id:1,date:"六",score:86,},
					{id:2,date:"日",score:80,},
					{id:3,date:"一",score:"？",},
					{id:4,date:"二",score:90,},
					{id:5,date:"三",score:92,},
					{id:6,date:"四",score:97,},
					{id:7,date:"五",score:81,}
				],
				image:{
					green:require('../../static/green.svg'),
					gray:require('../../static/gray.svg'),
					orange:require('../../static/orange.svg')
				}
			}
		},
		mounted() {
			this.modifyEmoji()
			// console.log(this.dataVisual,'this.dataVisual')
		},
		methods:{
			modifyEmoji(){
				for(let i of this.dataVisual){
					// console.log(i.score,'score')
					if(80<=i.score&&i.score<90){
						console.log(i.score,'score1')
						this.$set(i,'img',this.image.green)
						this.$set(i,'color','#52C873')	
					}else if(i.score>=90){
						console.log(i.score,'score2')
						this.$set(i,'img',this.image.orange)
						this.$set(i,'color','#FF823C')	
					}else{
						console.log(i.score,'score3')
						this.$set(i,'img',this.image.gray)
						this.$set(i,'color','#CFCFCF')	
					}
				}
			}
		}
	}
</script>

<style lang="scss">
	.box-wrapper{
		
		position: absolute;
		box-sizing: border-box;
		width: 100%;
		height: 698rpx;
		padding:0rpx 24rpx ;
		top: 36rpx;	
		
		/* Function ff */
		
		background: #FFFFFF;
		box-shadow: 0rpx -12rpx 32rpx rgba(0, 0, 0, 0.15);
		border-radius: 48rpx;
	}
	.box-content{
		display: flex;
		flex-direction: column;
		align-items: center;
		animation: fade 1s linear;
	}
	@keyframes fade{
		0%{
			opacity: 0;
		}
		100%{
			opacity: 1;
		}
	}
	.box-content_profile{
		display: inline-block;
		width: 72rpx;
		height: 72rpx;
		border-radius: 50%;
	}
	.box-content_name{
		display: flex;
    /* justify-content: center; */
		align-items: center;
		margin-left: 24rpx;
		font-size: .4rem;
	}
	.box-person{
		margin-top: 92rpx;
		width: 176rpx;
		height: 72rpx;
		display: flex;
		flex-direction: row;
		justify-content: center;
	}
	.box-content_score{
		width: 176rpx;
		height: 200rpx;
		display: flex;
		justify-content: center;
		align-items: center;
		font-family: 'Nunito';
		font-style: normal;
		font-weight: 800;
		font-size:144rpx;
	}
	.box-content_detail{
		color: #929292;
		font-family: 'PingFang HK';
		font-style: normal;
		font-weight: 500;
		font-size: 36rpx;
	}
</style>

<template>
	<view class='result-wrapper'>
		<view class='result-box' v-for="(item,index) in dataVisual" :key="item.id">
			<view class='result-column' :style="{'--height':item.score==='？'?20:item.score,'--color':item.color,'--i':index+1}">
				<image class='result-img' :src='item.img'></image>
				<text class='result-text'>{{item.score==='？'?"":item.score}}</text>
			</view>
			<text class='result-date' :class='{"current-date":item.date===currentWeek}'>{{item.date}}</text>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			dataVisual:{
				type:Array,
				default:()=>{
					return []
				}
			}
		},
		data(){
			return {
				currentWeek:""
			}
		},
		created(){
			this.getWeekDate()
		},
		methods:{
			getWeekDate() {
				var now = new Date();
				var day = now.getDay();
				var weeks = new Array("日", "一", "二", "三", "四", "五", "六");
				var week = weeks[day];
				this.currentWeek=week
				console.log(this.currentWeek,'currentweek')
			 }
		}
	}
</script>

<style lang="scss">
.result-wrapper{
	display: flex;
	flex-direction: row;
	position: absolute;
	left: 0;
	// top: 500rpx;
	width: 100%;
	justify-content: space-evenly;
	height: 700rpx;
	
}
.result-box{
	display: flex;
	flex-direction: column;
	align-items: center;
		
	height: 700rpx;
	// text-align: center;
	justify-content: flex-end;
	
}
.result-column{
	position: relative;
	display: inline-block;
	// flex-direction: column;
	// align-items: center;
	// height: 600rpx;
	
	text-align: center;
	background-color: var(--color);
	border-radius:999px;
	width: 72rpx;
	animation: delay .5s linear forwards;
	animation-delay: calc(0.05s * var(--i));;
	// height: calc(var(--height) / 100 * 600rpx);
}
@keyframes delay{
	0%{
		height: 124rpx;
	}
	100%{
		height: calc(var(--height) / 100 * 600rpx);
	}
}
.result-img{
	width: 72rpx;
	height: 72rpx;
	position: absolute;
	bottom: 0;
	left: 0;
}
.result-text{
	color:#FFFFFF;
	position: absolute;
	left: 50%;
	transform: translateX(-50%);
	top: 10rpx;
}
.result-date{
	width: 36rpx;
	height: 50rpx;
	font-family: 'PingFang HK';
	font-style: normal;
	font-weight: 500;
	font-size: 36rpx;
	line-height: 50rpx;
	color: #2D2F33;
}
.current-date{
	width: 72rpx;
	height: 72rpx;
	line-height: 72rpx;
	text-align: center;
	background: #2D2F33;
	border-radius: 8px;
	color: white;
}
.result-box:active .result-date{
	width: 72rpx;
	height: 72rpx;
	text-align: center;
	/* Function ff */
	line-height: 72rpx;
	background: #FFFFFF;
	box-shadow: 0px 8rpx 20rpx rgba(0, 0, 0, 0.2);
	border-radius: 16rpx;
}
.result-box:active .result-column{
	// background: #FFFFFF;	
	box-shadow: 0px 8rpx 20rpx rgba(0, 0, 0, 0.2);
}
.result-box:active .current-date{
	color: #2D2F33;
}
</style>

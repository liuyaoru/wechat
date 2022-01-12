<template>
		<view class="home">
	  <swiper indicator-dots circular>
		  <swiper-item v-for="item in swipers" :key=item.id>
			  <image :src="item.img"></image>
		  </swiper-item>
	  </swiper>
	  <!--导航区域  -->
	  <view class="nav">
		  <view class="nav_item">
			  <view class="iconfont icon-ziyuan"></view>
			  <text>
				  超市购物
			  </text>
		  </view>
		  <view class="nav_item">
		  			  <view class=" iconfont icon-guanyuwomen"></view>
		  			  <text>
		  				  联系我们
		  			  </text>
		  </view>
		  <view class="nav_item">
		  			  <view class="iconfont icon-tupian"></view>
		  			  <text>
		  				  社区图示
		  			  </text>
		  </view>
		  <view class="nav_item">
		  			  <view class="iconfont icon-shipin"></view>
		  			  <text>
		  				  学习
		  			  </text>
		  </view>
		  </view>
		  
		  
		  
		<!--  推荐商品区域 -->
		  <view class="hot_goods">
			  <view class="hit">推荐商品 </view>
			  <view class="goods_list">
                 <view class="goods-item">
	              <image src="http://demo/dtcms.net/upload/201504/20/thumb_201504200046589514.jpg"></image>	
							  <view class="price">
								  <text>￥2199</text>
								  <text>￥2499</text>
								  </view>
								   <view class="name">
									   华为（HUAWEI）荣耀PLUS 16G双4版
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
				title: 'Hello',
				swipers:[]
			}
		},
		onLoad() {
			this.getSwipers()

		},
		methods: {
			//获取轮播图的数据
		       async	getSwipers()
		      	{
			 
		     	let res=await this.$myRuquest({
				
				url:'/api/getlunbo'
			})
				this.swipers=res.data.message
				console.log("获取轮播图的数据",res)
			/* 	uni.request({
					url:'http://localhost:8082/api/getlunbo',
					success:res=>{
						console.log(res)
						if(res.data.status!==0)
						{
							return uni.showToast({
								title:'获取数据失败'
							})
						}
						this.swipers=res.data.message
					}
				}) */
		
			}

		}
	}
</script>

<style lang="scss">
	.home{
		swiper{
			width: 750rpx;
			height: 380rpx;
			image:{
				height: 100%;
				width: 100%;
			}
			
		}
	}
	.nav{
		display: flex;
		.nav_item{
			width: 25%;
			text-align: center;
			view{
			  	width: 120rpx;
			     height:120rpx;
				 background:$shop-color;
				 border-radius: 60rpx;
				 margin: 10rpx auto;
				 line-height: 120rpx;
				 color: #fff;
				 font-size: 50rpx;
			}
			.icon-tupian{
				font-size:45rpx
			}
		    text {
				
				font: 30rpx;
			}
		}
	}
    .hot_goods{
		background: #eee;
		overflow: hidden;
		margin-top: 10rpx;
		.hit{
			height: 50px;
			line-height: 50px;
			color:$shop-color ;
			letter-spacing: 20px;
			text-align: center;
			margin: 7rpx 0;
			background: #fff;	
		}
		.goods_list{
			padding: 0 15rpx;
			.goods_item{
				
			}
		}
	}
</style>

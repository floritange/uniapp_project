<template>
	<view>
		<view>
			<swiper circular autoplay :interval="3000" :duration="500" indicator-dots style="height: 350rpx;"
				indicator-color="rgba(255, 255, 255, 0.6)" indicator-active-color="#ЗСВ371">
				<swiper-item v-for="item in imgs" :key="item">
					<image :src="item" alt="" mode="widthFix" style="width: 100%;" />
				</swiper-item>
			</swiper>
		</view>

		<view style="margin: 10px;">
			<view
				style="padding: 5px 10px; background-color: white; font-size: 12px; border-radius: 5px; display: flex; align-items: center;">
				<uni-icons type="sound" size="20"></uni-icons>
				<view>{{ notice }}</view>
			</view>
			<view style="background-color: white; margin: 5px 0; border-radius: 5px; padding: 10px 0;">
				<uni-row>
					<uni-col :span="6">
						<view class="grid-item-box" @click="clickItem('桃子')">
							<image mode="widthFix" style="width: 50%;"
								src="https://img14.360buyimg.com/n0/jfs/t1/246735/20/12062/340811/666fa4a4F7c4795f6/6b3a1eb7ba879a21.png">
							</image>
							<text style="font-size: 13px; margin-top: 5px;">桃子</text>
						</view>
					</uni-col>
					<uni-col :span="6">
						<view class="grid-item-box" @click="clickItem('苹果')">
							<image mode="widthFix" style="width: 50%;"
								src="https://img14.360buyimg.com//n0/jfs/t1/200524/15/42052/131614/6641af8eFcc1ac7ae/1cc7dbce9e1427b7.jpg">
							</image>
							<text style="font-size: 13px; margin-top: 5px;">苹果</text>
						</view>
					</uni-col>
					<uni-col :span="6">
						<view class="grid-item-box" @click="clickItem('柠檬')">
							<image mode="widthFix" style="width: 50%;"
								src="https://img14.360buyimg.com/n1/jfs/t1/214074/19/38586/137896/6603d28eFd3b3a673/fcc8433066923cd3.jpg">
							</image>
							<text style="font-size: 13px; margin-top: 5px;">柠檬</text>
						</view>
					</uni-col>
					<uni-col :span="6">
						<view class="grid-item-box" @click="clickItem('芒果')">
							<image mode="widthFix" style="width: 50%;"
								src="https://img14.360buyimg.com/n1/jfs/t1/167443/2/42383/98958/65d6a5ccFe677d1f8/6f2b0e24a15d2a07.png">
							</image>
							<text style="font-size: 13px; margin-top: 5px;">芒果</text>
						</view>
					</uni-col>
				</uni-row>
			</view>

			<view style="margin: 5px 0; font-size: 12px;">
				<uni-row :gutter="10">
					<uni-col :span="12" v-for="item in goodList" :key="item.name">
						<view style="margin-bottom: 5px; background-color: white; padding: 10px; border: radius 10px;">
							<image mode="widthFix" :src="item.img" style="width: 100%;"></image>
							<view class="lineEllipsis">{{ item.name }}</view>
							<view style="color: red; margin-top: 5px; font-weight: bold; font-size: 14px;">
								￥{{item.price}}</view>
							<view style="text-align: right;">
								<uni-icons type="plus" size="25" style="color: #666;"
									@click="addCart(item.name)"></uni-icons>
							</view>

						</view>
					</uni-col>
				</uni-row>
			</view>

		</view>



	</view>
</template>

<script>
	export default {
		data() {
			return {
				imgs: [
					"https://m.360buyimg.com/babel/jfs/t20260713/169353/21/38491/136346/64b0a7c7F115f8a08/c413a29fab739105.png",
					"https://m.360buyimg.com/babel/jfs/t20260720/149498/7/35786/89345/64ba2898Fbd1f6b1f/d147a7032b8f905d.jpg",
					"https://m.360buyimg.com/babel/jfs/t20260719/200274/27/38564/103066/64b8a92bF9ff64827/86b0873317ff1670.jpg",
				],
				notices: [{
						content: "今天好热"
					},
					{
						content: "明天好天气"
					},
					{
						content: "昨天很快乐"
					},
				],
				notice: '',
				goodList: [{
						name: "华硕（ASUS）Vivobook S 16 Flip 16 英寸折叠屏触摸笔记本电脑背光巧克力键盘 银色 Ryzen 7 7730U+16G+512G",
						img: "https://img12.360buyimg.com/n7/jfs/t1/227857/2/20968/41487/667a0a77F0aa1912e/8d3b48aa03e20eda.jpg",
						price: "9487.00",
					},
					{
						name: "华硕（ASUS）ROG Strix Scar 15游戏笔记本 i9 12900H 32G+1T 单键 RGB 键盘 Black/黑色 15.6英寸 RTX 3080 Ti",
						img: "https://img10.360buyimg.com/n7/jfs/t1/214226/12/31663/52353/6479b06bF6ca22b5a/97502e2a2f06e4c9.jpg",
						price: "34137.00",
					},
					{
						name: " Apple 【24期当天发货】苹果笔记本 macbook air m2 苹果电脑M2芯片 13.6英寸学生资源版 MacBookAir 13.6英寸 M2 深空灰色 【评价有礼】8GB+256GB 标",
						img: "https://img14.360buyimg.com/n7/jfs/t1/184198/22/47298/99925/669b84b7F9cecedef/6666e840798c9dc5.jpg",
						price: "6649.00",
					}
				]
			}
		},
		onLoad() {
			this.loadNotice()
		},
		methods: {
			loadNotice() {
				let i = 0
				this.notice = this.notices[i++].content
				setInterval(() => {
					this.notice = this.notices[i++].content
					if (i === this.notices.length) {
						i = 0
					}
				}, 3000)
			},
			clickItem(item) {
				console.log(item)
			},
			addCart(item) {
				console.log(item)
			},
		}
	}
</script>

<style>
	.grid-item-box {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.lineEllipsis {
		word-break: break-all;
		text-overflow: ellipsis;
		display: -webkit-box;
		-webkit-box-orient: vertical;
		-webkit-line-clamp: 2;
		/* 超出2行自动省略*/
		overflow: hidden;
	}
</style>
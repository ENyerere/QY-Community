<template>
	<view class="all">
		
		<!-- 抽屉 -->
		
		<view class="person-info-bottom" @click="showDrawer('infoDrawer')">
			<text class="person-info-text" @click="showDrawer('infoDrawer')">{{c ?'选择社区':'成蹊苑'}}</text>
		</view>
		<uni-drawer width="430" ref="infoDrawer" mode="right" :mask-click="false" @change="change($event,'infoDrawer')">
			<view class="person-info-scroll-view">
				<scroll-view class="person-info-scroll-view-box" scroll-y="true">
					<view class="close">
						<image class="返回" src="../../static/my/返回键.png" @click="closeDrawer('infoDrawer')"></image>
					</view>
		
					<view class="位置">
						<text class="auth-text">当前位置:浙江·杭州·下沙</text>
					</view>
		
					<view>
						<uni-card title="成蹊苑" sub-title="下沙区" :thumbnail="avatar">
							<text
								class="uni-body">成蹊苑是浙江经贸大学的生活园区之一，园内环境优美，设施齐全，每幢寝室楼内都配有自助洗衣房、学生活动室，每间寝室均有独立卫生间、阳台，并装配空调、热水器等基础设施，为学生提供一个舒适宜居的环境。园区周围还有各种休闲娱乐的场所，丰富学生的课余生活。</text>
						</uni-card>
						<view class="join1">
							<text @click="onClick">{{joined ? '加入':'已加入'}}</text>
						</view>
					</view>
				</scroll-view>
			</view>
		</uni-drawer>
		
		<!-- 动态 -->

		<view class="picker">
			<uni-data-picker placeholder="请选择所在楼" popup-title="请选择所在房号" :localdata="dataTree" v-model="classes"
				class="pick" @change="handlePickerChange(classes)">
			</uni-data-picker>
		</view>
		<uni-card>
			<view>
				<uni-segmented-control :current="current" :values="items" :style-type="styleType"
					:active-color="activeColor" @clickItem="onClickItem" class="sc" />
			</view>
			<view class="content">
				<view v-if="current === 0 && showContent" class="active-all">
					<uni-card title="基础卡片">
						<template v-slot:title>
							<uni-list>
								<uni-list-item title="法国真美啊!第一次来这边" />
							</uni-list>
						</template>
						<image style="width: 100%;" src="../../static/动态/动态1.jpg"></image>
						<text class="uni-body uni-mt-5"></text>
						<view slot="actions" class="card-actions">
							<view class="card-actions-item" @click="toggleFavorite1()">
								<image :src="favorite1 ? '../../static/动态/已收藏.png' : '../../static/动态/收藏.png'"
									class="a-img"></image>
								<text class="card-actions-item-text">{{ favorite1 ? '已收藏' : '收藏' }}</text>
							</view>
							<view class="card-actions-item" @click="toggleLike1()">
								<image :src="liked1 ? '../../static/动态/已点赞.png' : '../../static/动态/点赞.png'"
									class="a-img"></image>
								<text class="card-actions-item-text">{{ liked1 ? '已点赞' : '点赞' }}</text>
							</view>
							<view class="card-actions-item">
								<image src="../../static/动态/评论.png" class="a-img"></image>
								<text class="card-actions-item-text">评论</text>
							</view>
						</view>
					</uni-card>
					<uni-card title="基础卡片">
						<template v-slot:title>
							<uni-list>
								<uni-list-item title="祝大家圣诞快乐!Merry Christmas!" />
							</uni-list>
						</template>
						<image style="width: 100%;" src="../../static/动态/动态2.jpg"></image>
						<text class="uni-body uni-mt-5"></text>
						<view slot="actions" class="card-actions">
							<view class="card-actions-item" @click="toggleFavorite2()">
								<image :src="favorite2 ? '../../static/动态/已收藏.png' : '../../static/动态/收藏.png'"
									class="a-img"></image>
								<text class="card-actions-item-text">{{ favorite2 ? '已收藏' : '收藏' }}</text>
							</view>
							<view class="card-actions-item" @click="toggleLike2()">
								<image :src="liked2 ? '../../static/动态/已点赞.png' : '../../static/动态/点赞.png'"
									class="a-img"></image>
								<text class="card-actions-item-text">{{ liked2 ? '已点赞' : '点赞' }}</text>
							</view>
							<view class="card-actions-item">
								<image src="../../static/动态/评论.png" class="a-img"></image>
								<text class="card-actions-item-text">评论</text>
							</view>
						</view>
					</uni-card>
					<uni-card title="基础卡片">
						<template v-slot:title>
							<uni-list>
								<uni-list-item title="终于来到火影忍者的世界了!" />
							</uni-list>
						</template>
						<image style="width: 100%;" src="../../static/动态/动态3.jpg"></image>
						<text class="uni-body uni-mt-5"></text>
						<view slot="actions" class="card-actions">
							<view class="card-actions-item" @click="toggleFavorite3()">
								<image :src="favorite3 ? '../../static/动态/已收藏.png' : '../../static/动态/收藏.png'"
									class="a-img"></image>
								<text class="card-actions-item-text">{{ favorite3 ? '已收藏' : '收藏' }}</text>
							</view>
							<view class="card-actions-item" @click="toggleLike3()">
								<image :src="liked3 ? '../../static/动态/已点赞.png' : '../../static/动态/点赞.png'"
									class="a-img"></image>
								<text class="card-actions-item-text">{{ liked3 ? '已点赞' : '点赞' }}</text>
							</view>
							<view class="card-actions-item">
								<image src="../../static/动态/评论.png" class="a-img"></image>
								<text class="card-actions-item-text">评论</text>
							</view>
						</view>
					</uni-card>
				</view>
				<view v-if="current === 1 && showContent" class="image-all">
					<uni-list>
						<uni-list-item title="陈浩宇" note="业主" thumb="../../static/业主/yz1.jpg" thumb-size="lg" />
						<uni-list-item title="张周聪" note="业主" thumb="../../static/业主/yz2.jpg" thumb-size="lg" />
						<uni-list-item title="曾情" note="业主" thumb="../../static/业主/yz3.jpg" thumb-size="lg" />
						<uni-list-item title="姚沈峄" note="业主" thumb="../../static/业主/yz4.jpg" thumb-size="lg" />
						<uni-list-item title="邓裕轩" note="业主" thumb="../../static/业主/yz5.jpg" thumb-size="lg" />
						<uni-list-item title="朱志健" note="业主" thumb="../../static/业主/yz6.jpg" thumb-size="lg" />
					</uni-list>
				</view>
			</view>
			<view class="content">
				<view v-if="current === 0 && !showContent" class="active-all-none">
					<text>暂无内容</text>
				</view>
				<view v-if="current === 1 && !showContent" class="image-all-none">
					<text>暂无内容</text>
				</view>
			</view>
		</uni-card>

		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				avatar: '../../static/person/成蹊苑.jpg',
				infoDrawer: false,
				favorite1: false,
				favorite2: false,
				favorite3: false,
				liked1: false,
				liked2: false,
				liked3: false,
				joined:true,
				c:true,
				showContent: false,
				items: ['社区动态', '社区业主'],
				current: 0,
				activeColor: '#007aff',
				styleType: 'text',
				classes: '',
				dataTree: [{
						text: "38幢",
						value: "1-0",
						children: [{
								text: "514",
								value: "1-1"
							},
							{
								text: "515",
								value: "1-2"
							}
						]
					},
					{
						text: "39幢",
						value: "2-0",
						children: [{
								text: "515",
								value: "2-1"
							},
							{
								text: "514",
								value: "2-2"
							}
						]
					}
				]
			}
		},
		methods: {
			onClick(e) {
				console.log('加入成功', e);
				uni.showToast({
					title: '加入成功'
				});
				this.joined=false
			},
			onClickItem(e) {
				if (this.current !== e.currentIndex) {
					this.current = e.currentIndex
				}
			},
			handlePickerChange(value) {
				if (value === '1-2') {
					this.showContent = true;
				} else {
					this.showContent = false;
				};
			},
			toggleFavorite1() {
				this.favorite1 = !this.favorite1;
				uni.showToast({
					title: this.favorite1 ? '已收藏' : '取消收藏',
					icon: 'none'
				});
			},
			toggleFavorite2() {
				this.favorite2 = !this.favorite2;
				uni.showToast({
					title: this.favorite2 ? '已收藏' : '取消收藏',
					icon: 'none'
				});
			},
			toggleFavorite3() {
				this.favorite3 = !this.favorite3;
				uni.showToast({
					title: this.favorite3 ? '已收藏' : '取消收藏',
					icon: 'none'
				});
			},
			toggleLike1() {
				this.liked1 = !this.liked1;
				uni.showToast({
					title: this.liked1 ? '已点赞' : '取消点赞',
					icon: 'none'
				});
			},
			toggleLike2() {
				this.liked2 = !this.liked2;
				uni.showToast({
					title: this.liked2 ? '已点赞' : '取消点赞',
					icon: 'none'
				});
			},
			toggleLike3() {
				this.liked3 = !this.liked3;
				uni.showToast({
					title: this.liked3 ? '已点赞' : '取消点赞',
					icon: 'none'
				});
			},

			// 抽屉
			showDrawer(e) {
				this.$refs[e].open()
			},

			closeDrawer(e) {
				this.$refs[e].close(),
				this.c=false
			},
			change(e, type) {
				console.log((type === 'showLeft' ? '左窗口' : '右窗口') + (e ? '打开' : '关闭'));
				this[type] = e
			},

		},
		onBackPress() {
			if (this.showRight || this.showLeft || this.infoDrawer || this.erweiDrawer) {
				this.$refs.infoDrawer.close()
				return true
			}
		}
	}
</script>

<style>
	.person-info-text{
		font-size: 14px;
		color: #646464;
	}
	
	.person-info-bottom{
		height: 18px;
		width: 60px;
		display: flex;
		align-items: center;
		justify-content: center;
		background-color: #f0f0f0;
		border-radius: 5px;
		padding: 5px 10px;
		transform: translate(-110px, -5px);
	}
	
	.auth-text {
		font-size: 12px;
		color: #646464;
		white-space: nowrap;
	}
	
	.位置 {
		height: 10px;
		width: 130px;
		display: flex;
		align-items: center;
		justify-content: center;
		background-color: #f0f0f0;
		border-radius: 15px;
		padding: 5px 10px;
		transform: translate(265px, 5px);
	}
	
	.join1 {
		height: 40px;
		width: 60px;
		background-color: #007aff;
		color: white;
		font-weight: bold;
		border-radius: 6px;
		text-align: center;
		line-height: 240%;
		transform: translate(330px, -200px);
	}

	.close {
		height: 50px;
	}

	.返回 {
		height: 20px;
		width: 20px;
		left: 75%;
		transform: translate(-300px, 30px);
		position: relative;
	}

	.all {
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.picker {
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.card {
		width: 300px;
		height: auto;
	}

	.sc {
		border-bottom: 1px solid rgba(0, 0, 0, 0.1);
	}

	.pick {
		width: 300px;
	}

	.image-all {
		width: 300px;
	}

	.active-all {
		width: 400px;
		height: 1050px;
	}

	.active-all-none {
		width: 400px;
		height: 600px;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.image-all-none {
		width: 400px;
		height: 600px;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.card-actions {
		display: flex;
		flex-direction: row;
		justify-content: space-around;
	}

	.card-actions-items {
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.card-actions-item-text {
		font-size: 16px;
	}

	.a-img {
		height: 20px;
		width: 20px;
	}
</style>
<template>
	<view>
		<!-- 小程序 -->
		<swiper class="swiper" :display-multiple-items="3" previous-margin="50rpx" next-margin="50rpx">
			<swiper-item v-for="(item, index) in list" :key="index" class="swiper-item" v-show="index < 6">
				<view class="swiper-box">
					<image :src="item.src" class="yztx"></image>
					<text>{{ item.name }}</text>
				</view>
			</swiper-item>
		</swiper>
		<!-- 标签 -->
		<view class="menu">
			<view class="menu-item" v-for="(item, index) in menuItems" :key="index"
				:class="{'selected': index === selectedIndex}" @click="selectItem(index)">
				<text class="menu-text">{{ item }}</text>
			</view>
		</view>
		<!-- 商品 -->
		<scroll-view scroll-y="true" style="width: 315px; height: 700px;" :scroll-into-view="scrollIntoView" class="滚动">
			<view class="item" v-for="(drink, index) in drinks" :key="index" :id="'item-' + drink.id">
				<image class="image" :src="drink.image"></image>
				<view class="description">
					<text class="name">{{ drink.name }}</text>
					<text class="price">￥{{ drink.price }}</text>
				</view>
				<view class="tags">
					<text v-for="(tag, tagIndex) in drink.tags" :key="tagIndex" class="tag">{{ tag }}</text>
				</view>
			</view>
		</scroll-view>
	</view>
</template>


<script>
	export default {
		data() {
			return {
				menuItems: [
					'生鲜水果',
					'饮料酒水',
					'零食小吃',
					'生活用品',
					'',
					'',
					'',
					'',
					'',
					'',
					'',
					'',
					'',
					'',
					'',
					'',
					'',
					'',
					'',
					'',
					'',
				],
				selectedIndex: 0,
				list: [{
						src: "../../static/supermarket/小程序/associated-press-22547.svg",
						name: "AssoPress"
					},
					{
						src: "../../static/supermarket/小程序/anida-6813.svg",
						name: "anida 6813"
					},
					{
						src: "../../static/supermarket/小程序/猫眼.svg",
						name: "猫眼"
					},
					{
						src: "../../static/supermarket/小程序/espanola-restaurante.svg",
						name: "Restaurante"
					},
					{
						src: "../../static/supermarket/小程序/nike.svg",
						name: "Nike"
					}
				],
				scrollIntoView: '',
				drinks: [{
						id: '1',
						category: '生鲜水果',
						name: '草莓',
						price: 9.9,
						tags: ['水果'],
						image: '../../static/supermarket/商品展示图/果蔬/草莓.jpg'
					},
					{
						id: '2',
						category: '生鲜水果',
						name: '苹果',
						price: 9.9,
						tags: ['水果'],
						image: '../../static/supermarket/商品展示图/果蔬/苹果.jpg'
					},
					{
						id: '3',
						category: '生鲜水果',
						name: '蓝莓',
						price: 9.9,
						tags: ['水果'],
						image: '../../static/supermarket/商品展示图/果蔬/蓝莓.jpg'
					},
					{
						id: '4',
						category: '生鲜水果',
						name: '西红柿',
						price: 9.9,
						tags: ['水果'],
						image: '../../static/supermarket/商品展示图/果蔬/西红柿.jpg',
					},
					{
						id: '5',
						category: '生鲜水果',
						name: '豆角',
						price: 9.9,
						tags: ['蔬菜'],
						image: '../../static/supermarket/商品展示图/果蔬/豆角.jpg',
					},
					{
						id: '6',
						category: '生鲜水果',
						name: '胡萝卜',
						price: 9.9,
						tags: ['蔬菜'],
						image: '../../static/supermarket/商品展示图/果蔬/胡萝卜.jpg',
					},
					{
						id: '7',
						category: '生鲜水果',
						name: '浆果',
						price: 9.9,
						tags: ['水果'],
						image: '../../static/supermarket/商品展示图/果蔬/浆果.jpg',
					},
					{
						id: '8',
						category: '生鲜水果',
						name: '蘑菇',
						price: 9.9,
						tags: ['蔬菜'],
						image: '../../static/supermarket/商品展示图/果蔬/蘑菇.jpg',
					},
					{
						id: '9',
						category: '生鲜水果',
						name: '芒果',
						price: 9.9,
						tags: ['水果'],
						image: '../../static/supermarket/商品展示图/果蔬/芒果.jpg',
					},
					{
						id: '10',
						category: '生鲜水果',
						name: '美洲大树莓',
						price: 9.9,
						tags: ['水果'],
						image: '../../static/supermarket/商品展示图/果蔬/美洲大树莓.jpg',
					},
					{
						id: '11',
						category: '饮料酒水',
						name: '果汁',
						price: 9.9,
						tags: ['饮料'],
						image: '../../static/supermarket/商品展示图/饮料酒水/果汁.jpg',
					},
					{
						id: '12',
						category: '饮料酒水',
						name: '可乐',
						price: 9.9,
						tags: ['饮料'],
						image: '../../static/supermarket/商品展示图/饮料酒水/可乐.jpg',
					},
					{
						id: '13',
						category: '饮料酒水',
						name: '咖啡',
						price: 9.9,
						tags: ['饮料'],
						image: '../../static/supermarket/商品展示图/饮料酒水/咖啡.jpg',
					},
					{
						id: '14',
						category: '饮料酒水',
						name: '鸡尾酒',
						price: 9.9,
						tags: ['酒水'],
						image: '../../static/supermarket/商品展示图/饮料酒水/鸡尾.jpg',
					},
					{
						id: '15',
						category: '饮料酒水',
						name: '啤酒',
						price: 9.9,
						tags: ['酒水'],
						image: '../../static/supermarket/商品展示图/饮料酒水/啤酒.jpg',
					},
					{
						id: '16',
						category: '饮料酒水',
						name: '香槟',
						price: 9.9,
						tags: ['酒水'],
						image: '../../static/supermarket/商品展示图/饮料酒水/香槟.jpg',
					},
					{
						id: '17',
						category: '零食小吃',
						name: '三只松鼠',
						price: 9.9,
						tags: ['零食'],
						image: '../../static/supermarket/商品展示图/零食小吃/坚果.jpg',
					},
					{
						id: '18',
						category: '零食小吃',
						name: '牛角包',
						price: 9.9,
						tags: ['零食'],
						image: '../../static/supermarket/商品展示图/零食小吃/牛角包.jpg',
					},
					{
						id: '19',
						category: '零食小吃',
						name: '披萨',
						price: 9.9,
						tags: ['小吃'],
						image: '../../static/supermarket/商品展示图/零食小吃/披萨.jpg',
					},
					{
						id: '20',
						category: '零食小吃',
						name: '薯条',
						price: 9.9,
						tags: ['小吃'],
						image: '../../static/supermarket/商品展示图/零食小吃/薯条.jpg',
					},
					{
						id: '21',
						category: '生活用品',
						name: '橄榄油',
						price: 9.9,
						tags: ['食用油'],
						image: '../../static/supermarket/商品展示图/粮油/橄榄油.jpg',
					},
					{
						id: '22',
						category: '生活用品',
						name: '炒米',
						price: 9.9,
						tags: ['米'],
						image: '../../static/supermarket/商品展示图/粮油/炒米.jpg',
					},
					{
						id: '23',
						category: '生活用品',
						name: '黑米',
						price: 9.9,
						tags: ['米'],
						image: '../../static/supermarket/商品展示图/粮油/黑米.jpg',
					},
					{
						id: '24',
						category: '生活用品',
						name: '东北米',
						price: 9.9,
						tags: ['米'],
						image: '../../static/supermarket/商品展示图/粮油/东北米.jpg',
					},
				],
			};
		},
		mounted() {
			this.$nextTick(() => {
				this.scrollToCategory(this.menuItems[this.selectedIndex]);
			});
		},
		methods: {
			selectItem(index) {
				this.selectedIndex = index;
				const category = this.menuItems[index];
				const firstItem = this.drinks.find(drink => drink.category === category);
				if (firstItem) {
					this.scrollIntoView = 'item-' + firstItem.id;
				} else {
					console.error('No items found in category:', category);
				}
			},
			scrollToCategory(category) {
				const firstItem = this.drinks.find(drink => drink.category === category);
				if (firstItem) {
					this.scrollIntoView = 'item-' + firstItem.id;
				} else {
					console.error('No items found in category:', category);
				}
			},
		},
		selectItem(index) {
			this.selectedIndex = index;
			this.scrollToCategory(this.menuItems[index]);
		},
	}
</script>

<style scoped>
	.swiper {
		width: 100%;
		height: 120px;
	}

	.swiper-box {
		width: 80px;
		display: flex;
		flex-direction: column;
		align-items: center;
		text-align: center;
	}

	.yztx {
		height: 60px;
		width: 60px;
		border-radius: 50%;
		margin-bottom: 5px;
	}

	.menu {
		width: 20%;
		background-color: #f8f8f8;
		border-radius: 10px;
		overflow: hidden;

	}

	.menu-item {
		background-color: #f8f8f8;
		padding: 15px;
		cursor: pointer;
		position: relative;

	}

	.menu-item::before,
	.menu-item::after {
		content: '';
		position: absolute;
		top: 0;
		width: 20px;
		height: 100%;
		background-color: #f8f8f8;
	}

	.menu-item::before {
		left: -10px;
		border-radius: 10px 0 0 10px;

	}

	.menu-item::after {
		right: -10px;
		border-radius: 0 10px 10px 0;

	}

	.menu-item.selected::before,
	.menu-item.selected::after {
		background-color: #ffffff;

	}

	.menu-item.selected {
		background-color: #ffffff;
		color: #000000;
	}

	.menu-text {
		font-size: 14px;
		color: #5a5a5a;
	}

	.menu-item.selected .menu-text {
		color: inherit;
		font-weight: bold;
	}

	/* 商店 */

	.container {
		display: flex;
		flex-direction: column;
	}

	.item {
		display: flex;
		margin-bottom: 10px;
	}

	.image {
		width: 100px;
		/* 根据需要调整 */
		height: 100px;
		/* 根据需要调整 */
		margin-right: 10px;
		border-radius: 10px;
	}

	.description {
		display: flex;
		flex-direction: column;
	}

	.name {
		font-size: 16px;
		font-weight: bold;
	}

	.price {
		color: red;
		transform: translate(0px, 50px);
	}

	.tags {
		display: flex;
		flex-wrap: wrap;
		height: 20px;
		transform: translate(-40px, 30px);
	}

	.tag {
		background-color: #f0f0f0;
		border-radius: 5px;
		padding: 2px 5px;
		margin-right: 5px;
		margin-top: 5px;
		font-size: 12px;
	}

	.滚动 {
		transform: translate(100px, -712px);
	}
</style>
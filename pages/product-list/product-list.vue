<template>
	<view class="page">
		<page-head :title="title"></page-head>
		<view class="uni-product-list">
			<view class="uni-product" v-for="(product,index) in productList" :key="index">
				<view class="image-view">
					<image v-if="renderImage" class="uni-product-image" :src="product.image"></image>
				</view>
				<view class="uni-product-title">{{product.title}}</view>
				<view class="uni-product-qwe">
					<image class="uni-product-qweimage" :src="qweImage"></image>
				</view>
				<view class="uni-product-price">
					<text class="uni-product-price-favour">￥{{product.originalPrice}}</text>
					<text class="uni-product-tip">{{product.tip}}</text>
					<text class="uni-product-price-original">￥{{product.favourPrice}}</text>
				</view>
				<view class="uni-product-asd">加入购物车›</view>
			</view>
		</view>
	</view>
</template>

<script>
export default {
    data() {
        return {
            title: 'product-list',
			productList: [],
			qweImage:'https://img.alicdn.com/tfs/TB1KgWMiX67gK0jSZPfXXahhFXa-147-36.png',
            renderImage: false
        };
    },
    methods: {
        loadData(action = 'add') {
            const data = [
                {
                    image: 'https://img.alicdn.com/bao/uploaded/i3/196993935/O1CN01lTq6UE1ewH5SGRHFZ_!!0-item_pic.jpg_240x240Q90.jpg',
                    title: '【设计师合作款】女装 羊毛混纺圆领针织衫(长袖) 420988',
                    originalPrice: 299,
                    favourPrice: 199,
					
                    tip: '秒杀'
                },
                {
                    image: 'https://img.alicdn.com/bao/uploaded/i4/196993935/O1CN01JqAKIu1ewH5WfDTDA_!!0-item_pic.jpg_240x240Q90.jpg',
                    title: '【设计师合作款】女装 羊毛混纺圆领针织衫(长袖) 420988',
                    originalPrice: 199,
                    favourPrice: 99,
                    tip: '优惠'
                },
                {
                    image: 'https:////img.alicdn.com/bao/uploaded/i4/196993935/O1CN01StQAws1ewH5UOjdPQ_!!0-item_pic.jpg_240x240Q90.jpg',
                    title: '【设计师合作款】女装 羊毛混纺圆领针织衫(长袖) 420988',
                    originalPrice: 159,
                    favourPrice: 59,
                    tip: '秒杀'
                },
                {
                    image: 'https://img.alicdn.com/bao/uploaded/i1/196993935/O1CN01G9vdcR1ewH5VwC5Kf_!!0-item_pic.jpg_240x240Q90.jpg',
                    title: '【设计师合作款】女装 羊毛混纺圆领针织衫(长袖) 420988',
                    originalPrice: 159,
                    favourPrice: 59,
                    tip: '秒杀'
                },
                {
                    image: 'https://img.alicdn.com/bao/uploaded/i1/196993935/O1CN01IJ5Sku1ewH5R0qQ9R_!!0-item_pic.jpg_240x240Q90.jpg',
                    title: '【设计师合作款】女装 羊毛混纺圆领针织衫(长袖) 420988',
                    originalPrice: 199,
                    favourPrice: 99,
                    tip: '优惠'
                },
                {
                    image: 'https://img.alicdn.com/bao/uploaded/i3/196993935/O1CN013fwB9K1ewH5VkRCcf_!!0-item_pic.jpg_240x240Q90.jpg',
                    title: '【设计师合作款】女装 羊毛混纺圆领针织衫(长袖) 420988',
                    originalPrice: 399,
                    favourPrice: 299,
                    tip: '秒杀'
                }
            ];

            if (action === 'refresh') {
                this.productList = [];
            }

            data.forEach(item => {
                this.productList.push(item);
            });
        }
    },
    onLoad() {
        this.loadData();
        setTimeout(()=> {
            this.renderImage = true;
        }, 300);
    },
    onPullDownRefresh() {
        this.loadData('refresh');
        // 实际开发中通常是网络请求，加载完数据后就停止。这里仅做演示，加延迟为了体现出效果。
        setTimeout(() => {
            uni.stopPullDownRefresh();
        }, 2000);
    },
    onReachBottom() {
        this.loadData();
    }
};
</script>

<style>
	
</style>

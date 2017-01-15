<template>
  	<div class="goods">
	  	<div class="menu-wrapper" ref="menuwrapper">
	  		<ul>
	  			<li v-for="(item,index) in goods" class="menu-item">
  					<span class="text"> <span v-show="item.type > 0" class="icon" :class="classMap[item.type]"></span>{{item.name}} </span>
	  			</li>
	  		</ul>
	    </div>
     	<div class="goods-wrapper" ref="goodswrapper">
		  	<ul>
		  		<li v-for="(item,index) in goods" class="food-list">
		  			<h2 class="title"> {{item.name}} </h2>
		  			<ul>
		  				<li v-for="food in item.foods" class="food-item">
		  					<div class="food-icon">
		  						<img :src="food.icon">
		  					</div>
		  					<div class="content">
		  						<h3 class="name"> {{food.name}} </h3>
		  						<p class="dec"> {{food.description}} </p>
		  						<div class="extra">
		  							<span>月售 {{food.sellCount}}</span>
		  							<span>好评率 {{food.rating}}%</span>
		  						</div>
		  						<div class="price">
		  							<span class="new-price"><span>￥</span>{{food.price}}</span>
		  							<span class="old-price" v-show="food.oldPrice"><span>￥</span>{{food.oldPrice}}</span>
		  						</div>
		  					</div>
		  				</li>
		  			</ul>
		  		</li>
		  	</ul>
		</div>
    </div>
</template>

<script>
	//引入滚动插件
	import BScroll from 'better-scroll';

	export default {
		proops:{
			seller:{

			}
		},
		data(){
			return {
				goods:[]
			}
		},
		 created(){
		  	this.$http.get("/api/goods").then(function(response){
		  		if(response.body.errno == 0) { 
		  			this.goods = response.body.data;
		  			//当dom更新后再执行初始化
		  			this.$nextTick(function(){
		  				this._initScroll();
		  			})
		  		}
		  	}),
		  	this.classMap = ['decrease','discount','special','invoice','guarantee']
	    },
	    methods:{
    		_initScroll(){
				this.menuScroll = new BScroll(this.$refs.menuwrapper,{})

				this.foodScroll = new BScroll(this.$refs.goodswrapper,{});
    		}
	    }
	}
</script>

<style>
/*---------------------上下固定高度，中间自适应的布局---------------*/
.goods {
	position: absolute;
	top: 175px;
	bottom: 46px;
	width: 100%;
	overflow: hidden;
	display: flex;
}
.goods .menu-wrapper {
	flex: 0 0 80px;
	width: 80px;
	background: #f3f5f7;
}
.goods .goods-wrapper {
	flex: 1;
	background: #fff;
}
/*--------------左侧-------------*/

.menu-wrapper .menu-item {
	width: 56px;
	height: 54px;
	padding: 0 12px;
	display: table;
}
.menu-wrapper .text {
	font-size: 12px;
	color: #666;
	line-height: 14px;
	border-bottom: 1px solid rgba(7,17,27,.1);
	display: table-cell;
	vertical-align: middle;
}
.goods .icon {
	display: inline-block;
	width: 12px;
	height: 12px;
	margin-right: 2px;
	vertical-align: middle;
}
.goods .decrease {  
	background: url(./decrease_1@3x.png) no-repeat; /*满减*/
	background-size: 100% 100%;
}
.goods .discount {
	background: url(./discount_1@3x.png) no-repeat;/*打折*/
	background-size: 100% 100%;
}
.goods .special {
	background: url(./special_1@3x.png) no-repeat;/*套餐*/
	background-size: 100% 100%;
}
.goods .invoice {
	background: url(./invoice_1@3x.png) no-repeat;/*发票*/
	background-size: 100% 100%;
}
.goods .guarantee {
	background: url(./guarantee_1@3x.png) no-repeat;/*保障*/
	background-size: 100% 100%;
}


/*--------------右侧-------------*/

.food-list .title {
	width: 100%;
	height:26px;
	line-height: 26px;
	font-size: 12px;
	padding-left: 14px;
	color: rgb(147,153,159);
	background: #f3f5f7;
	border-left: 2px solid #d9dde1;
}

.food-item {
	display: flex;
	margin: 18px;
	padding-bottom: 18px;
	border-bottom: 1px solid rgba(7,17,27,.1);
}
.food-item:last-child {
	border-bottom: 0;
}
.food-item .food-icon {
	width: 57px;
	font-size: 0;
	margin-right: 10px;
}
.food-item .food-icon img {
	width: 57px;
	height: 57px;
}
.food-item .content {
	flex: 1;
	padding-top: 2px;
}
.food-item .content .name {
	font-size: 14px;
	color: rgb(7,17,27);
	line-height: 14px;
}
.food-item .content .extra {
	font-size: 0;
}
.food-item .content .dec,
.food-item .content .extra span {
	font-size: 10px;
	color: rgb(147,153,159);
	line-height: 10px;
	vertical-align: top;
}
.food-item .content .extra span:nth-of-type(1){
	margin-right: 12px;
}
.food-item .content .dec {
	margin: 8px 0;
}
.price {
	font-size: 0
}
.price span {
	vertical-align: top;
}
.new-price {
	font-size: 14px;
	font-weight: 700;
	color: rgb(240,20,20);
	line-height: 24px;
	margin-right: 8px;
}
.new-price span {
	font-size: 10px;
	font-weight: normal;
}
.old-price {
	font-size: 10px;
	color: rgb(147,153,159);
	font-weight: 700;
	line-height: 24px;
}
.old-price span {
	font-size: 10px;
	font-weight: normal;
}






</style>

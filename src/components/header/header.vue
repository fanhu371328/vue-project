<template>
  <div class="header">
  	<!--内容区-->
  	<div class="content-wrapper">
  		<div class="avatar">
  			<img width="64" height="64" :src="seller.avatar"/>
  		</div>
  		<div class="content">
  			<div class="title">
  				<span class="brand"></span><span class="name"> {{seller.name}} </span>
  			</div>
  			<div class="description">
  				{{seller.description}}/{{seller.deliveryTime}}分钟送达
  			</div>
  			<div class="support" v-if="seller.supports">
  				<span class="icon" :class="classMap[seller.supports[0].type]"></span>
  				<span class="text"> {{seller.supports[0].description}}</span>
  			</div>
  		</div>
  		<div class="support-count" v-if="seller.supports" @click="showDetail">
  			<span class="count">{{seller.supports.length}}个</span>
  			<img src="./next@3x.png"/>
  		</div>
  	</div>
  	<!--公告区-->
  	<div class="bulletin-wrapper" @click="showDetail">
  		<span class="bulletin-title"></span><span class="bulletin-text">{{seller.bulletin}}</span>
  		<img src="./next@3x.png"/>
  	</div>
  	<div class="bag">
  		<img :src="seller.avatar"/>
  	</div>
  	<!--浮层区-->
  	<transition name="fade">
	  	<div class="detail" v-show = "detailShow">
	  		<!--当内容区高于屏幕的时候底部关闭按钮会随着滚动，当小于屏幕高度的时候回固定在屏幕底部-->
	  		<div class="detail-wrapper clearfix">
	  			<div class="detail-main">
	  				<h1 class="name">{{seller.name}}</h1>
	  				<div class="star-wrapper">
	  					<star :size="48" :score="seller.score"></star>
	  				</div>
	  				<div class="special-offers">
	  					<span></span><h3>优惠信息</h3><span></span>
	  				</div>
	  				<div class="supports" v-if="seller.supports">
	  					<li class="support-item" v-for="(item, index) in seller.supports">
	  						<span class="icon" :class="classMap[seller.supports[index].type]"></span><span class="text"> {{item.description}} </span>
	  					</li>
	  				</div>
	  				<div class="notice">
	  					<span></span><h3>商家公告</h3><span></span>
	  				</div>
	  				<div class="notice-content">
	  					{{seller.bulletin}}
	  				</div>
	  			</div>
	  		</div>
	  		<div class="detail-close" @click="closeDetail">
	  			<img src="./guanbi@3x.png"/>
	  		</div>
	  	</div>
  	</transition>
  </div>
</template>

<script>

	import star from '../star/star';

	export default {
	  name: 'header', 
	  props: {
	  	seller: {
	  	}
	  },
	  data() {
	    return {
	    		detailShow:false,
	    }
	  },
	  methods: {
	  	showDetail() {
	  		this.detailShow = true;
	  	},
	  	closeDetail() {
	  		this.detailShow = false;
	  	}
	  },
	  created() {
	  	this.classMap = ['decrease','discount','special','invoice','guarantee'];
	  },
	  components:{
	  	star
	  }
	}
</script>

<style>

.header {
	position: relative;
	color: #fff;
	background: rgba(7,17,27,.5);
	overflow: hidden;
}
/*-------------内容区---------*/	
.content-wrapper{
	display: flex;
	padding: 24px 12px 18px 24px;
	font-size: 0;
	position: relative;
}
.content-wrapper .avatar {display: inline-block;}
.content-wrapper .avatar img {
	border-radius: 2px;
}
.content-wrapper .content {
	display: inline-block;
	margin-left: 16px;
	padding-top: 2px;
	font-size: 14px;	
}
.content-wrapper .support-count {
	position: absolute;
	bottom: 10px;
	right: 12px;
	background: rgba(0,0,0,.2);
	padding: 7px 15px;
	border-radius: 20px;
}
.content-wrapper .support-count span {
	line-height: 24px;
	font-size: 10px;
}
.content-wrapper .support-count img {
	width: 6px;
	height: 10px;
	margin-left: 10px;
}

.content-wrapper .content .title .brand {
	display: inline-block;
	vertical-align: top;
	width: 30px;
	height: 18px;
	background: url(./brand@3x.png) no-repeat;
	background-size: 100% 100%;
}
.content-wrapper .content .title .name {
	font-size: 16px;
	line-height: 18px;
	font-weight: bold;
}
/*-------------描述----------*/
.description {
	margin: 8px 0 10px;
	font-size: 12px;
	line-height: 12px;
}
/*------------支持-------------*/
.support {
	font-size:0;
}
.support .icon {
	display: inline-block;
	vertical-align: top;
	width: 12px;
	height: 12px;
	margin-right: 2px;
}
.support .text {font-size: 10px;line-height: 12px;}
.support .decrease {  
	background: url(./decrease_1@3x.png) no-repeat; /*满减*/
	background-size: 100% 100%;
}
.support .discount {
	background: url(./discount_1@3x.png) no-repeat;/*打折*/
	background-size: 100% 100%;
}
.support .special {
	background: url(./special_1@3x.png) no-repeat;/*套餐*/
	background-size: 100% 100%;
}
.support .invoice {
	background: url(./invoice_1@3x.png) no-repeat;/*发票*/
	background-size: 100% 100%;
}
.support .guarantee {
	background: url(./guarantee_1@3x.png) no-repeat;/*保障*/
	background-size: 100% 100%;
}
/*----------------公告区---------------*/
.bulletin-wrapper {
	height: 28px;
	padding: 0 22px 0 12px;
	white-space: nowrap;
	overflow: hidden;
	text-overflow: ellipsis;
	background: rgba(7,17,27,.2);
	position: relative;
}
.bulletin-wrapper .bulletin-title {
	display: inline-block;
	width: 22px;
	height: 12px;
	background: url(bulletin@3x.png) no-repeat;
	background-size: 100% 100%;
	margin-right: 4px;
	vertical-align: middle;
	line-height: 28px;
}
.bulletin-wrapper .bulletin-text {
	font-size: 10px;
	vertical-align: middle;
	line-height: 28px;
}
.bulletin-wrapper img {
	width: 6px;
	height: 10px;
	position: absolute;
	right: 12px;
	top:8px;
}
/*------------背景图----------*/
.bag {
	position: absolute;
	width: 100%;
	height: 100%;
	top: 0;
	left: 0;
	z-index: -1;
	filter: blur(10px);
}
.bag img {
	margin: 0 auto;
	margin-left: 18%;
	margin-top: 8%;
}
/*------------浮层--------------*/
.detail {
	position: fixed;
	top: 0;
	left: 0;
	z-index: 99;
	width: 100%;
	height: 100%;
	overflow: auto;  
	background: rgba(7,17,27,.8);
	/*filter: blur(10px);*/
}
/*过渡效果*/
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s
}
.fade-enter, .fade-leave-active {
  opacity: 0
}


.detail-wrapper {
	min-height: 100%;
}
.detail-main {
	padding-top: 64px;
	padding-bottom: 64px;
}
.detail-main .name {
	font-size: 16px;
	text-align: center;
	line-height: 16px;
	font-weight: 700;
}
.detail-close {
	position: relative;
	width:32px;
	height: 32px;
	margin: -64px auto 0 auto;
	/*clear: both;*/
	font-size: 32px;
}
.detail-close img {
	width: 32px;
	height: 32px;
}

.star-wrapper {
	margin-top: 16px;
	padding:2px 0;
	text-align: center;
}
/*-----------------------优惠信息-----------------*/
.special-offers {
	padding: 0 36px;
	margin:28px 0 24px;
	display: flex;
	align-items: center;
}
.special-offers span {
	flex: 1;
	border: 1px solid rgba(255,255,255,.2);
}
.special-offers h3 {
	padding: 0 12px;
	font-weight: 700;
}
.supports {
	font-size:0;
	padding: 0 47px;
}
.support-item .icon {
	display: inline-block;
	vertical-align: middle;
	width: 16px;
	height: 16px;
	margin-right: 6px;
}
.supports .text {
	font-size: 12px;
	line-height: 24px;
	color: #fff;
	vertical-align: middle;
}

.supports .decrease {  
	background: url(./decrease_1@3x.png) no-repeat; /*满减*/
	background-size: 100% 100%;
}
.supports .discount {
	background: url(./discount_1@3x.png) no-repeat;/*打折*/
	background-size: 100% 100%;
}
.supports .special {
	background: url(./special_1@3x.png) no-repeat;/*套餐*/
	background-size: 100% 100%;
}
.supports .invoice {
	background: url(./invoice_1@3x.png) no-repeat;/*发票*/
	background-size: 100% 100%;
}
.supports .guarantee {
	background: url(./guarantee_1@3x.png) no-repeat;/*保障*/
	background-size: 100% 100%;
}
/*-----------------商家公告--------------*/


.notice {
	padding: 0 36px;
	margin:28px 0 24px;
	display: flex;
	align-items: center;
}
.notice span {
	flex: 1;
	border: 1px solid rgba(255,255,255,.2);
}
.notice h3 {
	padding: 0 12px;
	font-weight: 700;
}
.notice-content {
	padding: 0 47px;
	font-size: 12px;
	line-height: 24px;
}


</style>

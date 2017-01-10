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
  		<div class="support-count" v-if="seller.supports">
  			<span class="count">{{seller.supports.length}}个个个个</span>
  			<i class="icon-keyboard_arrow_right"></i>
  		</div>
  	</div>
  	<!--公告区-->
  	<div class="bulletin-wrapper">
  		<span class="bulletin-title"></span><span class="bulletin-text">{{seller.bulletin}}</span>
  		<i class="icon-keyboard_arrow_right"></i>
  	</div>
  	<div class="bag">
  		<img :src="seller.avatar"/>
  	</div>
  </div>
</template>

<script type="text/ecmascript-6">
	
export default {
  name: 'header', 
  components: {
    
  },
  props:{
  	seller:{
  		
  	}
  },
  created() {
  	this.classMap = ['decrease','discount','special','invoice','guarantee']
  }
}
</script>

<style lang="stylus" rel="stylesheet/stylus">

/*@font-face {
	font-family:icon;
	src:  url('../../common/fonts/icon.eot?8tqr70')
  	src:  url('../../common/fonts/icon.eot?8tqr70#iefix') format('embedded-opentype'),
    url('../../common/fonts/icon.ttf?8tqr70') format('truetype'),
    url('../../common/fonts/icon.woff?8tqr70') format('woff'),
    url('../../common/fonts/icon.svg?8tqr70#icon') format('svg')
  	font-weight: normal
  	font-style: normal
}*/

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
	font-size: 14px;	
}
.content-wrapper .support-count {
	position: absolute;
	bottom: 10px;
	right: 12px;
	background: rgba(0,0,0,.2);
	padding: 7px 8px;
	border-radius: 20px;
}
.content-wrapper .support-count span {
	line-height: 24px;
	font-size: 10px;
}
.content-wrapper .support-count i {
	font-family: icon;
	font-size: 10px;
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

</style>

<template>
	<div class="shopcar">
		<div class="content">
			<div class="content-left">
				<div class="logo-wrapper">
					
				</div>
				<div class="price">
					<p>
						￥ <span class="price-num">0</span>
					</p>
				</div>
				<div class="desc">
					另需配送费5元
				</div>
			</div>
			<div class="content-right">
			<span>￥<span class="start-price">20</span></span>起送
			</div>
		</div>
	</div>


</template>

<script type="text/javascript">
	
	export default{

	}

</script>

<style type="text/css">
	
	.shopcar {
		width:100%;
		position: fixed;
		bottom: 0;
		z-index: 1000;
	}
	.shopcar .price {
		font-size: 16px;
		color:rgba(255,255,255,.4);
	}
	.shopcar .content{
		display: flex;
	}
	.shopcar .content-left {
		flex: 1;
		height: 46px;
		background:#141d27;
		font-size: 0;
		display: flex;
	}
	.shopcar .content-left .logo-wrapper {
		
		width: 44px;
		height: 44px;
		background: #2b343c url('./yuyin@3x.png') no-repeat;
		background-size: 105% 105%;
		background-position: center;
		border-radius: 50%;
		margin:0 18px;
		border: 6px solid #141d27;
		position: relative;
		top:-10px;
	}
	.shopcar .content-left .price {
		font-size: 16px;
		color: rgba(255,255,255,.4);
		background:#141d27;
	}
	.shopcar .content-left .price p {
		margin-top: 12px;
		height: 25px;
		line-height: 25px;
		padding-right: 12px;
		border-right: 1px solid rgba(255,255,255,.4);
		font-weight: 700;
		font-size: 16px;
	}
	.shopcar .content-left .desc {
		padding-left: 12px;
		flex: 1;
		font-size: 12px;
		color: rgba(255,255,255,.4);
		line-height: 46px;
		background:#141d27;
	}
	.shopcar .content-right {
		flex: 0 0 105px;
		height: 46px;
		line-height: 46px;
		text-align: center;
		background: rgba(7,17,27,.7);
		color: rgba(255,255,255,.4);
		font-size: 16px;
		font-weight: 700;
	}
	.shopcar .content-right span {
		font-size: 14px;
		font-weight: 700;
	}











</style>
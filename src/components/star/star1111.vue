<template>
  <div class="star" :class="starType">
  	<span v-for="itemClass in itemClasses" :class="itemClass"></span>
  	
  </div>
</template>

<script>
	//通过传递过来的尺寸和分数显示不同样式
	//computed 是vue的计算属性
	
	var LENGTH = 5;
	var CLS_ON = 'on';
	var CLS_HALF = 'half';
	var CLS_OFF = 'off';
	
	
	
	export default {
		props:{
			size:{
				type:Number
			},
			score:{
				type:Number
			}
		},
	    computed:{
	    		starType(){
	    			return "star-"+this.size
	    		},
	    		itemClasses(){
	    			var result = [];
	    			//先乘以2向下取整后再除以二，效果是不足1.5的取1，大于1.5不足2的取1.5///向下取0.5的整
	    			var score = Math.floor(this.score*2) / 2;
	    			var hasDecimal = score % 1 !== 0;  //是否有小数，有就显示半星
	    			var integer = Math.floor(score);  //整星
	    			for (i=0 ; i<integer ; i++){
	    				result.push(CLS_ON)
	    			}
	    			
	    			if(hasDecimal){
	    				result.push(CLS_HALF)
	    			}
	    			
	    			while (result.length < LENGTH){
	    				result.push(CLS_OFF)
	    			}
	    			
	    			return result;
	    		}
	    }
	  
	  
	}
</script>

<style>
	/*展示星星的有三个地方每个尺寸不一样，分别定义*/
	.star  {
		font-size: 0;
	}
	
	.star-item {
		display: inline-block;
		background-repeat: no-repeat;
	}
	
    .star-48 .star-item {
		width: 20px;
		height: 20px;
		margin-right: 22px;
		background-size: 20px 20px;
	}
	.star-48 .star-item:last-child {
		margin-right: 0;
	}
	.star-48 .star-item .on {
		background: url(star48_on@3x.png);
	}
	.star-48 .star-item .half {
		background: url(star48_half@3x.png);
	}
	.star-48 .star-item .off {
		background: url(star48_off@3x.png);
	}
    .star-36 .star-item {
		width: 15px;
		height: 15px;
		margin-right: 6px;
		background-size: 15px 15px;
	}
	.star-36 .star-item:last-child {
		margin-right: 0;
	}
	.star-36 .star-item .on {
		background: url(star36_on@3x.png);
	}
	.star-36 .star-item .half {
		background: url(star36_half@3x.png);
	}
	.star-36 .star-item .off {
		background: url(star36_off@3x.png);
	}
    .star-24 .star-item {
		width: 10px;
		height: 10px;
		margin-right: 3px;
		background-size: 10px 10px;
	}
	.star-24 .star-item:last-child {
		margin-right: 0;
	}
	.star-24 .star-item .on {
		background: url(star24_on@3x.png);
	}
	.star-24 .star-item .half {
		background: url(star24_half@3x.png);
	}
	.star-24 .star-item .off {
		background: url(star24_off@3x.png);
	}


</style>

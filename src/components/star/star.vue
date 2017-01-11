<template>
  <div class="star" :class="starType">
  	<span v-for="item in items" :class="item" class="star-item"></span>
  </div>
</template>

<script>
	var LENGTH = 5;
	var CLS_ON = 'on';
	var CLS_HALF = 'half';
	var CLS_OFF = 'off';
	
	
	
	export default {
		props: {
			size: {
			},
			score: {
			}
		},
	    computed: {
    		starType() {
    			return "star-"+this.size
    		},
    		items() {

    			var result = [];

    			var score = Math.floor(this.score*2) / 2;
    			var hasDecimal = score % 1 !== 0;  
    			var integer = Math.floor(score);  

    			for (var i=0 ; i<integer ; i++){
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
	}
	
    .star-48 .star-item {
		width: 20px;
		height: 20px;
		margin-right: 22px;
	}
	.star-48 .star-item:last-child {
		margin-right: 0;
	}
	.star-48 .on {
		background: url(star48_on@3x.png);
		background-size: 100% 100%;
	} 
	.star-48 .half {
		background: url(star48_half@3x.png);
		background-size: 100% 100%;
	}
	.star-48 .off {
		background: url(star48_off@3x.png);
		background-size: 100% 100%;
	}
    .star-36 .star-item {
		width: 15px;
		height: 15px;
		margin-right: 6px;
	}
	.star-36 .star-item:last-child {
		margin-right: 0;
	}
	.star-36 .on {
		background: url(star36_on@3x.png);
		background-size: 15px 15px;
	}
	.star-36 .half {
		background: url(star36_half@3x.png);
		background-size: 15px 15px;
	}
	.star-36 .off {
		background: url(star36_off@3x.png);
		background-size: 15px 15px;
	}
    .star-24 .star-item {
		width: 10px;
		height: 10px;
		margin-right: 3px;
	}
	.star-24 .star-item:last-child {
		margin-right: 0;
	}
	.star-24 .on {
		background: url(star24_on@3x.png);
		background-size: 10px 10px;
	}
	.star-24 .half {
		background: url(star24_half@3x.png);
		background-size: 10px 10px;
	}
	.star-24 .off {
		background: url(star24_off@3x.png);
		background-size: 10px 10px;
	}


</style>

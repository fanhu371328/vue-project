<template>
  <div id="app">
  	
  	<myheader :seller="seller"></myheader>
  	
  	<div class="tab">
	  	<div class="tab-item">
	  		<router-link to="/goods">商品</router-link>
	  	</div>
	  	<div class="tab-item">
	  		<router-link to="/ratings">评论</router-link>
	  	</div>
	  	<div class="tab-item">
	  		<router-link to="/seller">商家</router-link>
	  	</div>
	  	
    </div>
  	<router-view></router-view>
    
  </div>
</template>

<script>
	import myheader from './components/header/header.vue';

	export default {
	  name: 'app',
	  data(){
	  	return {
	  		seller:{
	  		}
	  	}
	  },
	  created(){
	  	this.$http.get("/api/seller").then(function(response){

	  		if(response.body.errno == 0) { 
	  			this.seller = response.body.data;
	  			console.log(this.seller)
	  		}
	  	})
	  },
	  components: {
	  	myheader
	  }
	}
</script>

<style lang="stylus">
	#app .tab {
		display: flex;
		width: 100%;
		line-height: 40px;
		border-bottom: 1px solid rgba(7,17,27,.1);
	}
	#app .tab .tab-item {
		flex: 1;
		text-align: center;
	}
	.tab a {
		display: block;
		font-size: 14px;
		color: rgb(77,85,93);
	}
	.tab .active {
		color:rgb(240,20,20);
	}
	
</style>

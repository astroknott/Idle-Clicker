<template></template>

<script>
 export default {
     name: 'AutoBuyer',
		 props: {
				 initialSpeed: Number,
		 },
     data: function () {
				 return {
						 speed: this.initialSpeed
				 }
     },
		 mounted: function () {
				 this.initialize();
		 },
		 methods: {
				 initialize: function () {
						 setInterval( this.buyClicker, this.speed);
				 },
				 
				 buyClicker: function () {
						 this.$emit('buy-clicker', 1);
				 }
		 }
 }
</script>

<style scoped>
</style>

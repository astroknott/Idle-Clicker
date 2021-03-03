<template></template>

<script>
 export default {
     name: 'Clicker',
     data: function () {
				 return {
						 speed: 100
				 }
     },
		 mounted: function () {
				 this.initialize();
		 },
		 methods: {
				 initialize: function () {
						 setInterval( this.increment, this.speed);
				 },
				 
				 increment: function () {
						 this.$emit('update-money', .01);
				 }
		 }
 }
</script>

<style scoped>
</style>

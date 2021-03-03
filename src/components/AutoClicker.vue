<template>
  <button @click="$emit('update-counter', 1)">Click</button>
</template>

<script>
 export default {
     name: 'Clicker',
     props: {
				 msg: String,
     },
     data: function () {
				 return {
				 }
     },
		 methods: {
		 }
 }
</script>

<style scoped>
</style>

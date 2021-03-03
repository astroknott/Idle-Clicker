<template>
  <div id="app">
		<h1>${{ display(money) }}</h1>
    <p>Clicker Count: {{ clickers.length }}</p>
		<Clicker
			  v-for="clicker in clickers"
				:key="clicker.id"
				v-on:update-money="updateMoney"
		/>

		<AutoBuyer
				v-for="buyer in buyers"
				v-on:buy-clicker="buyClicker"
				v-bind:initialSpeed="10000"
		/>
		
		<button type="button" class="btn btn-primary me-2" @click="updateMoney(clickStrength)">Increment</button>
		<button type="button" class="btn btn-secondary me-2" v-bind:disabled="money < clickerCost" @click="buyClicker()">
			Add Clicker: ${{ display(clickerCost) }}
		</button>

		<button type="button" class="btn btn-secondary" v-bind:disabled="money < buyerCost" @click="buyBuyer()">
			Add AutoBuyer: ${{ display(buyerCost) }}
		</button>
  </div>
</template>

<script>
 import Clicker from './components/Clicker.vue';
 import AutoBuyer from './components/AutoBuyer.vue';
 
 export default {
		 name: 'App',
		 components: {
				 Clicker,
				 AutoBuyer,
		 },
		 computed: {
		 },
     data: function () {
				 return {
						 money: 0,
						 clickStrength: 10,
						 clickers: [],
						 buyers: [],
						 buyerCost: 20,
						 clickerCost: 5,
						 costMod: 1.02,
				 }
     },
		 methods: {
				 display: function (val) {
						 return val.toFixed(2);
				 },
				 updateMoney: function (amt) {
						 this.money += amt;
				 },

				 buyClicker: function () {
						 if (this.money >= this.clickerCost) {
								 // pay for clicker
								 this.money -= this.clickerCost;
								 // add clicker
								 this.clickers.push({id: this.clickers.length + 1});
								 // increase cost of next clicker
								 this.clickerCost = this.clickerCost * this.costMod;
						 }
				 },

				 buyBuyer: function () {
						 if (this.money >= this.buyerCost) {
								 // pay for buyer
								 this.money -= this.buyerCost;
								 // add buyer
								 this.buyers.push({id: this.buyers.length + 1});
								 // increase cost of next buyer
								 this.buyerCost = this.buyerCost * this.costMod;
						 }
						 
				 }
		 }
 }
</script>

<style>
 #app {
		 font-family: Avenir, Helvetica, Arial, sans-serif;
		 -webkit-font-smoothing: antialiased;
		 -moz-osx-font-smoothing: grayscale;
		 text-align: center;
		 color: #2c3e50;
		 margin-top: 60px;
 }
</style>

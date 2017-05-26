<template lang="html">
  <div class="">
  	<img src="static/CostaRica.jpg">
    <button class="button-forward" @click="forward"><b>	&#62;</b></button>
    <div class="main-title">
      <h1>{{ msg }}</h1>
    </div>
    <div class="textstuff">
      <button class="main-butt" v-for="provincia in provincias" @click="select(provincia)"><b>{{ provincia }}</b></button>
    </div>
  </div>
</template>

<script>
export default {
	data() {
		return {
			msg: 'Parques Nacionales de Costa Rica',
			provincias: [],
		}
	},
	methods: {
		select: function ( provincia ) {
			console.log( provincia );
			this.$emit( 'changeScreen', 'Parques', provincia );
		},
		forward() {
			this.$emit( 'forward' );
		}
	},
	beforeMount() {
		var provinciasDB = require( '../assets/db/provincias.json' );
		console.log( "provincias: " + provinciasDB );
		console.log( "length: " + provinciasDB.length );
		for ( var i = 0; i < provinciasDB.length; i++ ) {
			this.provincias[ i ] = provinciasDB[ i ].Nombre;
		}
		document.body.scrollTop = document.documentElement.scrollTop = 0;
	}
}
</script>

<style lang="css">
</style>

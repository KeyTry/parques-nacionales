<template lang="html">
  <div class="">
    <img :src="this.img" alt="">
    <br>
    <button class="button-back" @click="back"><b>&#60;</b></button>
    <button class="button-forward" @click="forward"><b>&#62;</b></button>
    <div class="main-title">
      <h1>{{ msg }} {{Lugar}}</h1>
    </div>
    <div class="textstuff">
      <button class="main-butt" v-for="parque in parques" @click="select(parque)"><b>{{ parque }}</b></button>
    </div>
  </div>
</template>

<script>
export default {
	data() {
		return {
			msg: "Parques Nacionales en",
			parques: [],
			img: '',
		}
	},
	props: [ 'Lugar' ],
	methods: {
		back() {
			this.$emit( 'back', 'Provincias' );
		},
		select: function ( parque ) {
			console.log( parque );
			this.$emit( 'changeScreen', 'Parque', parque );
		},
		forward() {
			this.$emit( 'forward' );
		}
	},
	beforeMount() {
		console.log( "Lugar (desde Parques): " + this.Lugar );
		var parquesDB = require( '../assets/db/parques.json' );
		var provinciasDB = require( '../assets/db/provincias.json' );
		var j = 0;
		for ( var i = 0; i < provinciasDB.length; i++ ) {
			if ( provinciasDB[ i ].Nombre == this.Lugar ) {
				this.img = provinciasDB[ i ].img;
			}
		}
		for ( var i = 0; i < parquesDB.length; i++ ) {
			if ( parquesDB[ i ].Provincia == this.Lugar ) {
				this.parques[ j ] = parquesDB[ i ].Nombre;
				console.log( "parque " + j + ": " + this.parques[ j ] );
				j++;
			}
		}
		document.body.scrollTop = document.documentElement.scrollTop = 0;
	}
}
</script>

<style lang="css">
</style>

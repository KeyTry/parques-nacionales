<template lang="html">
  <div class="">
      <img :src="this.img" alt="">
      <button class="button-back" @click="back"><b>&#60;</b></button>
      <button class="button-forward" @click="forward"><b>&#62;</b></button>
      <div class="main-title">
          <h1>{{ nombre }}</h1>
      </div>
      <div class="textstuff">
        <h2>Provincia: </h2><h3>{{ provincia }}</h3>
        <h2>Área de Conservación: </h2><h3>{{ area }}</h3>
        <h2>Superficie: </h2><h3>{{ superficie }}</h3>
        <h2>Descripción</h2>
        <p>{{ descripcion }}</p>
      </div>
  </div>
</template>

<script>
export default {
	data() {
		return {
			msg: "Hola Parque!",
			nombre: '',
			provincia: '',
			superficie: '',
			img: '',
			descripcion: '',
			area: '',
		}
	},
	props: [ 'Lugar' ],
	methods: {
		back() {
			this.$emit( 'changeScreen', 'Parques', this.provincia );
		},
		forward() {
			this.$emit( 'forward' );
		}
	},
	beforeMount() {
		console.log( "Lugar (desde Parque): " + this.Lugar );
		var parquesDB = require( '../assets/db/parques.json' );
		var j = 0;
		var tempImg
		for ( var i = 0; i < parquesDB.length; i++ ) {
			if ( parquesDB[ i ].Nombre == this.Lugar ) {
				console.log( "parque encontrado" );
				this.nombre = "Parque Nacional " + parquesDB[ i ].Nombre;
				this.provincia = parquesDB[ i ].Provincia;
				this.superficie = parquesDB[ i ].Superficie + " Hectáreas";
				this.img = "static/" + parquesDB[ i ].img;
				this.descripcion = parquesDB[ i ].Descripcion;
				this.area = parquesDB[ i ].Area;
			}
		}
		document.body.scrollTop = document.documentElement.scrollTop = 0;
	}
}
</script>

<style lang="css" scoped>
h2{
  font-size: 2em;
}
h3{
  font-size: 1.4em;
}
</style>

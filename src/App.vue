<template>
<div id="app">
	<component v-bind:is="currentView" @changeScreen="changeScreen" @forward="forward" @back="back" :Lugar="Lugar">
	</component>
	<h5>Daniel Somarribas<br>2017</h5>
</div>
</template>

<script>
import Hello from './components/Hello'
import Provincias from './components/Provincias'
import Parques from './components/Parques'
import Parque from './components/Parque'

export default {
	name: 'app',
	data() {
		return {
			currentView: 'Provincias',
			Lugar: '',
			otherLugar: '',
			previousPosition: 'Provincias',
			previousLugar: ''
		}
	},
	components: {
		Hello,
		Provincias,
		Parques,
		Parque
	},
	methods: {
		changeScreen( position, lugar ) {
			console.log( "Recibido: Position: " + position + ", lugar: " + lugar );
			this.previousPosition = this.currentView;
			this.previousLugar = this.otherLugar;
			console.log( "Previous Position: " + this.previousPosition + ", Previous Lugar: " + this.previousLugar );
			this.currentView = position;
			this.Lugar = lugar;
			this.otherLugar = lugar;
			console.log( "enviando: " + lugar );
		},
		back( position ) {
			this.currentView = position;
		},
		forward() {
			this.changeScreen( this.previousPosition, this.previousLugar );
		}
	}
}
</script>

<style>
body {
	background-color: #7DB800;
}

#app {
	font-family: 'Avenir', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #1A1A1A;
	margin-top: 60px;
	max-width: 50%;
	min-width: 512px;
	margin: auto;
	background-color: #ECECEC;
	border-radius: 4px;
	margin-top: 12px;
	margin-bottom: 24px;
	padding-bottom: 24px;
}

.textstuff {
	padding: 36px 64px 12px 64px;
}

img {
	max-width: 100%;
	border-radius: 4px 4px 0 0;
	display: inline-block;
	position: relative;
}

.main-title {
	font-size: 1.5em;
	background-color: #005E5A;
	color: #ECECEC;
	padding: 12px 24px;
}

.main-butt,
.button-back,
.button-forward {
	border: 0px 2px 2px 0px solid;
	background: #FD0006;
	border-color: #FC999B;
	color: #ECECEC;
	cursor: pointer;
	margin-top: 0;
}

.main-butt {
	display: block;
	margin: auto;
	margin-bottom: 36px;
	padding: 24px;
	width: 352px;
	max-width: 90%;
	border-radius: 6px;
	font-size: 1.6em;
	-webkit-transition-duration: 0.3s;
	transition-duration: 0.3s;
}

.button-back:hover,
.main-butt:hover,
.button-forward:focus {
	background-color: #FD393E;
	color: #1A1A1A;
}

.button-back:focus,
.main-butt:focus,
.button-forward:focus {
	outline: 0;
}

.button-back,
.button-forward {
	position: fixed;
	font-size: 3em;
	width: 72px;
	height: 72px;
	border-radius: 100%;
	-webkit-transition-duration: 0.3s;
	transition-duration: 0.3s;
}

.button-back {
	left: 12vw;
	top: 12vh;
}

.button-forward {
	right: 12vw;
	bottom: 12vh;
}

p {
	margin: auto;
	text-align: left;
	font-size: 1.15em;
	line-height: 1.5em;
}
</style>
style>
le>

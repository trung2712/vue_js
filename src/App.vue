<template>
  <div id="app">
    <label>Nhap C</label>
    <input type="number" name="C" v-model="c"/>
    <comp-header :nhap-c=" Number (c)" />
    <img src="./assets/logo.png">
    <h1>{{ msg }}</h1>
		<comp-footer />
	</div>
</template>

<script>
import CompHeader from './components/CompHeader.vue';
import CompFooter from './components/CompFooter.vue';
export default {
	name: 'app',
	data () {
		return {
			msg:  "",
      c : 3
		}
	},
	components: {
		CompHeader,
		CompFooter
	}
}
</script>

<style>
	#app {
		font-family: 'Avenir', Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
		margin-top: 60px;
	}

	h1, h2 {
		font-weight: normal;
	}

	ul {
		list-style-type: none;
		padding: 0;
	}

	li {
		display: inline-block;
		margin: 0 10px;
	}

	a {
		color: #42b983;
	}
</style>

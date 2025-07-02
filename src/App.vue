<template>
	<div id="splash">
		<img alt="Vue logo" src="./assets/logo.png" style="margin-left: auto; margin-right: auto; display: block" />
		<h1>Vite Single File Plugin Example</h1>
		<p>
			This is a test app for
			<a href="https://github.com/richardtallent/vite-plugin-singlefile"> Vite Plugin SingleFile </a>. It uses a <code>file:</code> package reference for the
			plugin to allow local testing of changes to the plugin, so to build this, you need the plugin cloned to a sister folder in order to build this app.
		</p>
		<p>This app is compiled into a single <code>index.html</code> file, which means it can be:</p>
		<ul>
			<li>Directly opened in a browser using double-click</li>
			<li>Served with a single HTTP request</li>
			<li>Embedded in a CMS, LMS, or other system that doesn't allow external scripts</li>
			<li>Attached and sent as an email</li>
		</ul>
		<h2>Feature tests</h2>
		<ul>
			<li>LocalStorage: {{ testLocalStorage }}</li>
			<li>Secure Context: {{ testSecureContext }}</li>
			<li>
				WebXR: <button v-if="!testXR" @click.prevent="doTestXR()">Test Me</button> <span v-else>{{ testXR }}</span>
			</li>
			<li>
				Immersive WebXR: <button v-if="!testImmersiveXR" @click.prevent="doTestImmersiveXR()">Test Me</button> <span v-else>{{ testImmersiveXR }}</span>
			</li>
		</ul>
		<canvas ref="canvas" />
	</div>
</template>
<script setup lang="ts">
import { onBeforeMount, ref, Ref } from "vue"

const testLocalStorage = ref("")
const testSecureContext = ref("")
const testXR = ref("")
const testImmersiveXR = ref("")
const canvas: Ref = ref(null)

const doTestXR = () => {
	const gl = canvas.value?.getContext("webgl", { xrCompatible: true })
	testXR.value = gl ? "Yes" : "NO"
}

const doTestImmersiveXR = () => {
	if ("xr" in navigator)
		(navigator as any).xr
			.requestSession("immersive-vr")
			.then(() => {
				testImmersiveXR.value = "Yes"
			})
			.catch(() => (testImmersiveXR.value = "NO"))
	else {
		testImmersiveXR.value = "n/a"
	}
}

onBeforeMount(() => {
	window.localStorage.setItem("test", "Yes")
	testLocalStorage.value = window.localStorage.getItem("test") ?? "NO"
	testSecureContext.value = window.isSecureContext ? "Yes" : "NO"
})
</script>
<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	color: #2c3e50;
	margin-top: 60px;
	display: flex;
}
#splash {
	margin-left: auto;
	margin-right: auto;
	background-color: white;
	padding: 1rem;
}
code {
	font-weight: bold;
}
</style>

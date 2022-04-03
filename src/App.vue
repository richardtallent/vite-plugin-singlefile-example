<template>
	<div id="splash">
		<img
			alt="Vue logo"
			src="./assets/logo.png"
			style="margin-left: auto; margin-right: auto; display: block"
		/>
		<h1>Vite Single File Plugin Example</h1>
		<p>
			This is a test app for
			<a href="https://github.com/richardtallent/vite-plugin-singlefile">
				Vite Plugin SingleFile </a
			>. It uses a <code>file:</code> package reference for the plugin to allow
			local testing of changes to the plugin, so to build this, you need the
			plugin cloned to a sister folder in order to build this app.
		</p>
		<p>
			This app is compiled into a single <code>index.html</code> file, which
			means it can be:
		</p>
		<ul>
			<li>Directly opened in a browser using double-click</li>
			<li>Served with a single HTTP request</li>
			<li>
				Embedded in a CMS, LMS, or other system that doesn't allow external
				scripts
			</li>
			<li>Attached and sent as an email</li>
		</ul>
	</div>
</template>

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
}
code {
	font-weight: bold;
}
</style>

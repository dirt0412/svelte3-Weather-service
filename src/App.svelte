<script>
	import Main from "./pages/Main.svelte";
	import { Router, Route, Link } from "svelte-routing";
	import Berlin from "./pages/Berlin.svelte";
	import Warszawa from "./pages/Warszawa.svelte";
	import Tokyo from "./pages/Tokyo.svelte";
	import NewYork from "./pages/NewYork.svelte";
	export let url = ""; //This property is necessary declare to avoid ignore the Router
</script>

<Router {url}>
	<nav>
		<Link to="/" class="hover:text-gray-700 hover:no-underline">Main</Link>
		<Link to="berlin" class="link"
			>Berlin</Link
		>
		<Link to="warszawa" class="link"
			>Warszawa</Link
		>
		<Link to="tokyo" class="link"
			>Tokyo</Link
		>
		<Link to="newYork"  class="link"
			>New York</Link
		>
	</nav>
	<div class="container">
		<Route path="/"><Main /></Route>
		<Route path="berlin" component={Berlin} />
		<Route path="warszawa" component={Warszawa} />
		<Route path="tokyo" component={Tokyo} />
		<Route path="newYork" component={NewYork} />
	</div>
</Router>

<style>
	:global(body) {
		padding-left: 20%;
		padding-right: 20%;
	}
	.container {
		background-color: #eee;
		padding: 5px;
	}
	:global(h1) {
		color: #777;
		font-weight: 600;
		font-size: 18px;
	}
	:global(a) {
		color: #888;
		text-decoration: none;
		font-size: 20px;
		padding-left: 20px;
	}

	:global(a:hover) {
		text-decoration: none;
		color: #111;
	}

	:global(a:visited) {
		color: #888;
	}
	:global(.link){
		color: #888;
	}

</style>

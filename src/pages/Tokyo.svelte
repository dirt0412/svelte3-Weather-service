<script>
	import City from './City.svelte';
	import { onMount, onDestroy, beforeUpdate, afterUpdate } from "svelte";

	let nameCity = 'Tokyo';

	onMount(async () => {

	});
	beforeUpdate(() => {
		//autoscroll = div && (div.offsetHeight + div.scrollTop) > (div.scrollHeight - 20);
	});

	afterUpdate(() => {
		//if (autoscroll) div.scrollTo(0, div.scrollHeight);
	});
	onDestroy(() => {
		//clearInterval(interval);
	});
</script>

<City {nameCity} ></City>

<script lang="ts">
	import RiveComponent from './RiveComponent.svelte';

	let riveInstance;
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<section on:click={() => {
	const smInputs = riveInstance.stateMachineInputs("State Machine 1");
	const toggleInput = smInputs[0];
	toggleInput.value = !toggleInput.value;
}}>
	<RiveComponent
		src="/grimley.riv"
		autoplay={true}
		artboard="Dwarf Panel"
		stateMachines="State Machine 1"
		bind:riveInstance={riveInstance} />
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}
</style>

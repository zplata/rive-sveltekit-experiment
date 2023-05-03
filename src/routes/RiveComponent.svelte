<script lang="ts">
  import {Rive, Layout, Fit, Alignment} from '@rive-app/canvas';
	import {onMount} from 'svelte';

  export let src;
  export let autoplay;
  export let artboard;
  export let stateMachines;
  export let riveInstance;

	onMount(() => {
		const canvasEl = document.getElementById('rive-canvas');
		riveInstance = new Rive({
			src,
			autoplay,
			artboard,
			layout: new Layout({
				fit: Fit.Contain,
				alignment: Alignment.Center,
			}),
			stateMachines,
			canvas: canvasEl,
			onLoad: () => {
				riveInstance.resizeDrawingSurfaceToCanvas();
			},
		});
	});
</script>

<div class="rive-canvas-container">
  <canvas id="rive-canvas"></canvas>
</div>

<style>
  .rive-canvas-container {
		width: 100%;
		height: 100%;
	}

	#rive-canvas {
		width: 100%;
		height: 100%;
		min-width: 100vw;
		min-height: 100vh;
	}
</style>
<script lang="ts">
	// Utils
	import { inView } from "motion";
	import { onMount } from "svelte";

	// Props
	let {
		text = "",
		oncomplete = () => {},
		show = $bindable(true)
	}: { text: string; show?: boolean; oncomplete?: () => void } = $props();

	// State
	let words = $derived(text.split(" "));
	let element: HTMLElement | null = null;

	function handleWordIntroEnd(index: number) {
		if (index + 1 === words.length) {
			setTimeout(() => {
				oncomplete();
			}, 500);
		}
	}

	// onMount(() => {
	// 	if (element) {
	// 		inView(element, (element, entry) => {
	// 			if (entry.isIntersecting) {
	// 				show = true;
	// 			}
	// 		});
	// 	}
	// });
</script>

<span class:show bind:this={element}>
	{#each (text || "").split(" ") as word, i}
		<span
			class="animated-word inline-block origin-left"
			style:--delay="{i * 100}ms"
			onanimationstart={() => handleWordIntroEnd(i)}
		>
			{word}
		</span>{" "}
	{/each}
</span>

<style lang="postcss">
	.animated-word {
		/* No initial opacity set */
	}

	.show .animated-word {
		animation: appearAnimation 1000ms cubic-bezier(0.22, 0.61, 0.36, 1) both;
		animation-delay: var(--delay);
		transform: translateY(12px) scale(1);
		filter: blur(4px);
	}

	@keyframes appearAnimation {
		from {
			transform: translateY(12px) scale(1);
			filter: blur(4px);
		}
		to {
			transform: translateY(0) scale(1);
			filter: blur(0);
		}
	}

	@media (prefers-reduced-motion: reduce) {
		.show .animated-word {
			animation: none;
		}
	}
</style>

<script lang="ts">
	import { onMount } from "svelte";

	// Props
	type Props = {
		delay?: number;
		duration?: number;
		children?: any;
	};
	let { delay = 0, duration = 800, children }: Props = $props();

	// State
	let element: HTMLElement | null = null;
	let isVisible = $state(false);

	onMount(() => {
		if (!element) return;

		// Respect user's motion preferences
		const prefersReducedMotion = window.matchMedia("(prefers-reduced-motion: reduce)").matches;
		if (prefersReducedMotion) {
			isVisible = true;
			return;
		}

		const observer = new IntersectionObserver(
			(entries) => {
				entries.forEach((entry) => {
					if (entry.isIntersecting) {
						isVisible = true;
						observer.unobserve(entry.target);
					}
				});
			},
			{
				threshold: 0.1,
				rootMargin: "0px 0px -50px 0px"
			}
		);

		observer.observe(element);

		return () => {
			observer.disconnect();
		};
	});
</script>

<div
	bind:this={element}
	class={["animate-wrapper", isVisible ? "is-visible" : ""]}
	style:--delay="{delay}ms"
	style:--duration="{duration}ms"
>
	{@render children?.()}
</div>

<style lang="postcss">
	.animate-wrapper {
		animation: slideBlurIn var(--duration) cubic-bezier(0.22, 0.61, 0.36, 1) both;
		animation-delay: var(--delay);
	}

	.animate-wrapper:not(.is-visible) {
		animation-play-state: paused;
	}

	@keyframes slideBlurIn {
		from {
			transform: translateY(24px);
			filter: blur(8px);
		}
		to {
			transform: translateY(0);
			filter: blur(0);
		}
	}

	@media (prefers-reduced-motion: reduce) {
		.animate-wrapper {
			animation: none;
		}
	}
</style>

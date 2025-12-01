<script lang="ts">
	// Components
	import Marquee from "./sub/Marquee.svelte";

	// Props
	const {
		paused,
		label = "Scaling companies like yours",
		layout = "vertical",
		mode = "light",
		logoUrls = [
			"https://cdn.brandfetch.io/facebook.com/w/400/h/400/logo?c=1id_elLz2Bd5Ej-dWo7",
			"https://cdn.brandfetch.io/amazon.com/w/400/h/400/logo?c=1id_elLz2Bd5Ej-dWo7",
			"https://cdn.brandfetch.io/google.com/w/400/h/400/logo?c=1id_elLz2Bd5Ej-dWo7",
			"https://cdn.brandfetch.io/apple.com/w/400/h/400/logo?c=1id_elLz2Bd5Ej-dWo7"
		],
		...rest
	}: {
		paused?: boolean;
		label?: string;
		layout?: "horizontal" | "vertical";
		mode?: "light" | "dark";
		logoUrls?: string[];
		[key: string]: any;
	} = $props();
</script>

<div
	data-scroller
	class="grid place-items-center gap-6 self-end py-6 {label ? 'sm:py-16' : 'sm:py-12'}"
	class:!flex={layout === "horizontal"}
	{...rest}
	class:dark={mode === "dark"}
	{...rest}
>
	{#if label}
		<p
			class="text-callout text-emphasis-low whitespace-nowrap font-medium"
			class:mr-3={layout === "horizontal"}
			class:sm:mr-6={layout === "horizontal"}
		>
			{label}
		</p>
	{/if}
	<div class="m-auto w-full max-w-prose overflow-hidden">
		<Marquee
			class="mask-image text-muted-foreground h-full items-center [--gap:theme(spacing.8)] sm:[--gap:theme(spacing.16)]"
			speed={paused ? 0 : 0.1}
		>
			{#each logoUrls as logo, i}
				<img src={logo} alt="" class="mx-10 h-6 w-fit object-contain opacity-60 saturate-0 transition-opacity duration-300 hover:opacity-80" />
			{/each}
		</Marquee>
	</div>
</div>

<style lang="postcss">
	:global(.mask-image) {
		mask-image: linear-gradient(to right, transparent, black 15%, black 85%, transparent);
	}
</style>

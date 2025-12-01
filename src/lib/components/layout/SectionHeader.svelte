<script lang="ts">
	// Components
	import AnimateText from "$lib/components/animation/AnimateText.svelte";

	// Props
	let {
		title = "",
		subtitle = "",
		oncomplete = () => {},
		size = "sm"
	}: {
		title: string;
		subtitle: string;
		oncomplete?: () => void;
		size?: "sm" | "lg";
	} = $props();
</script>

<div
	class={[
		"section-pb-sm container-sm grid gap-4 text-balance",
		size === "lg" ? "text-display" : "text-title2"
	]}
>
	<h2 class="leading-tight">
		<AnimateText text={title} {oncomplete} />
	</h2>
	<p class="text-emphasis-dim text-title3">
		<AnimateText text={subtitle} />
	</p>
</div>

<script lang="ts">
	import type { Component } from "svelte";

	interface Props {
		title?: string;
		description?: string;
		icon?: Component;
		iconClass?: string;
		imageSrc?: string;
		imageAspect?: "16/9" | "9/16";
		class?: string;
	}

	let {
		title = "",
		description = "",
		icon,
		iconClass = "size-5 text-primary",
		imageSrc,
		imageAspect = "16/9",
		class: customClass = ""
	}: Props = $props();
</script>

<article
	class="bg-card text-card-foreground hover:bg-card-hover border-border group flex flex-col rounded-lg border p-6 px-7 text-pretty transition-all duration-300 ease-out lg:p-7 lg:px-8 {customClass}"
>
	{#if icon || imageSrc}
		<div class="mb-10">
			{#if icon && imageSrc}
				{@const Icon = icon}
				<div class="relative overflow-hidden rounded-lg">
					<img
						src={imageSrc}
						alt={title}
						class="w-full object-cover transition-transform duration-500 ease-out group-hover:scale-105 {imageAspect === '9/16'
							? 'aspect-[9/16]'
							: 'aspect-[16/9]'}"
					/>
					<div
						class="bg-background/95 border-border absolute top-4 left-4 rounded-md border p-2 backdrop-blur-sm"
					>
						<Icon
							class="size-5 {iconClass.includes('text-')
								? iconClass.split(' ').find((c) => c.startsWith('text-'))
								: 'text-primary'}"
						/>
					</div>
				</div>
			{:else if icon}
				{@const Icon = icon}
				<div class="inline-flex rounded-lg bg-primary/10 p-3">
					<Icon class={iconClass} />
				</div>
			{:else if imageSrc}
				<div class="overflow-hidden rounded-lg">
					<img
						src={imageSrc}
						alt={title}
						class="w-full object-cover transition-transform duration-500 ease-out group-hover:scale-105 {imageAspect === '9/16'
							? 'aspect-[9/16]'
							: 'aspect-[16/9]'}"
					/>
				</div>
			{/if}
		</div>
	{/if}

	<div class:mt-auto={icon || imageSrc}>
		<h3 class="text-title3 text-card-foreground mb-3 transition-colors duration-300 group-hover:text-primary">
			{title}
		</h3>
		<p class="text-callout text-muted-foreground max-w-prose leading-relaxed">{description}</p>
	</div>
</article>

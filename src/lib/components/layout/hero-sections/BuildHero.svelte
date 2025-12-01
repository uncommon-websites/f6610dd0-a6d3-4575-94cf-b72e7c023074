<!--
    @component
    Build.inc-inspired hero with massive typography and minimal design.
    Features large, bold text with generous whitespace and subtle animations.

    Usage:
    ```html
    <BuildHero
      title="Commercial insurance that actually makes sense"
      subtitle="AI-powered matching finds your optimal coverage in minutes, not weeks."
      callsToAction={[
        { href: "/contact", label: "Get a quote" },
        { href: "/about", label: "How it works" }
      ]}
    />
    ```

    Props:
    - `title`: Main headline (string) - Keep it bold and impactful
    - `subtitle`: Supporting text (string) - Brief value proposition
    - `callsToAction`: CTA buttons array (max two: primary, secondary)
-->

<script lang="ts">
	// Components
	import Button from "$lib/components/ui/Button.svelte";

	// Constants
	import { cta } from "$lib/navigation";

	// Types
	type Props = {
		title: string;
		subtitle: string;
		imageSrc?: string;
		callsToAction?: Array<{
			href: string;
			label: string;
		}>;
		[key: string]: any;
	};

	let {
		title,
		subtitle,
		imageSrc,
		callsToAction = [cta],
		...rest
	}: Props = $props();

	// Animation state
	let mounted = $state(false);

	// Mount animation
	$effect(() => {
		const timer = setTimeout(() => {
			mounted = true;
		}, 100);

		return () => clearTimeout(timer);
	});
</script>

<div class="relative min-h-screen bg-background" {...rest}>
	{#if imageSrc}
		<!-- Full Page Background Image -->
		<div class="absolute inset-0">
			<img
				src={imageSrc}
				alt="Hero visual"
				class={[
					"h-full w-full object-cover transition-all duration-1000 ease-out",
					mounted ? "scale-100 opacity-100" : "scale-105 opacity-0"
				]}
			/>
			<!-- Gradient Overlay for Text Readability -->
			<div class="absolute inset-0 bg-gradient-to-b from-black/60 via-black/40 to-black/70"></div>
		</div>
	{/if}

	<header
		class="section-px container relative z-10 mx-auto grid min-h-screen place-items-center text-center"
	>
		<!-- Main Title - Massive Typography -->
		<div class="mx-auto max-w-6xl">
			<h1
				class={[
					"font-[450] transition-all duration-1000 ease-out",
					"text-[2.5rem] leading-[1.05] tracking-[-0.02em]",
					"sm:text-[3.5rem]",
					"md:text-[4.5rem]",
					"lg:text-[5.5rem]",
					"xl:text-[6.5rem]",
					imageSrc ? "text-white" : "",
					mounted ? "translate-y-0 opacity-100" : "translate-y-8 opacity-0"
				]}
			>
				{title}
			</h1>

			<!-- Subtitle - Clean and Spacious -->
			<p
				class={[
					"mx-auto mt-8 max-w-2xl transition-all duration-1000 ease-out",
					"text-headline md:text-title3",
					imageSrc ? "text-white/90" : "text-muted-foreground",
					mounted ? "translate-y-0 opacity-100 delay-200" : "translate-y-8 opacity-0"
				]}
			>
				{subtitle}
			</p>

			<!-- CTAs - Minimal and Confident -->
			{#if callsToAction.length > 0}
				<div
					class={[
						"mt-12 flex flex-wrap items-center justify-center gap-4 transition-all duration-1000 ease-out",
						mounted ? "translate-y-0 opacity-100 delay-300" : "translate-y-8 opacity-0"
					]}
				>
					{#each callsToAction as cta, index}
						<Button
							href={cta.href}
							size="lg"
							variant={index % 2 === 0 ? "primary" : "secondary"}
							class="min-w-[160px]"
						>
							{cta.label}
						</Button>
					{/each}
				</div>
			{/if}
		</div>

		<!-- Subtle scroll indicator -->
		<div
			class={[
				"absolute bottom-12 left-1/2 -translate-x-1/2 transition-all duration-1000 ease-out",
				mounted ? "translate-y-0 opacity-30 delay-500" : "translate-y-8 opacity-0"
			]}
		>
			<div class={[
				"mx-auto h-12 w-6 rounded-full border-2 p-1",
				imageSrc ? "border-white/30" : "border-muted-foreground/20"
			]}>
				<div
					class={[
						"h-2 w-2 rounded-full",
						imageSrc ? "bg-white/60" : "bg-muted-foreground/40"
					]}
					style="animation: bounce 2s infinite;"
				></div>
			</div>
		</div>
	</header>
</div>

<style>
	@keyframes bounce {
		0%,
		100% {
			transform: translateY(0);
			opacity: 0.4;
		}
		50% {
			transform: translateY(12px);
			opacity: 0.8;
		}
	}
</style>

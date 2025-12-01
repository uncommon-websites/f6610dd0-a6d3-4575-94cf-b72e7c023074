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
	import Logo from "$lib/components/Logo.svelte";

	// Constants
	import { cta } from "$lib/navigation";
	import { CONFIG } from "$lib/content";

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
			<!-- Modern gradient overlay with better depth -->
			<div class="absolute inset-0 bg-gradient-to-b from-black/70 via-black/50 to-black/80"></div>
		</div>
	{/if}

	<!-- Company Logo and Name - Top Left Navigation -->
	<div
		class={[
			"section-px container absolute top-0 left-0 right-0 z-20 mx-auto flex items-center justify-start py-6 transition-all duration-1000 ease-out",
			mounted ? "translate-y-0 opacity-100" : "-translate-y-4 opacity-0"
		]}
	>
		<div class="flex items-center gap-3">
			<Logo class={[
				"size-8 sm:size-10",
				imageSrc ? "text-white" : ""
			]} />
			<span class={[
				"text-body1 sm:text-title3 font-medium",
				imageSrc ? "text-white" : ""
			]}>
				{CONFIG.companyName}
			</span>
		</div>
	</div>

	<header
		class="section-px container relative z-10 mx-auto grid min-h-screen place-items-center text-center"
		style="text-shadow: 0 2px 20px rgba(0, 0, 0, 0.3), 0 8px 40px rgba(0, 0, 0, 0.2);"
	>
		<!-- Main Title - Massive Typography with improved hierarchy -->
		<div class="mx-auto max-w-7xl">

			<h1
				class={[
					"font-[450] transition-all duration-1000 ease-out",
					"text-[2.75rem] leading-[1.05] tracking-[-0.025em]",
					"sm:text-[4rem]",
					"md:text-[5rem]",
					"lg:text-[6rem]",
					"xl:text-[7rem]",
					imageSrc ? "text-white" : "",
					mounted ? "translate-y-0 opacity-100 delay-100" : "translate-y-8 opacity-0"
				]}
			>
				{title}
			</h1>

			<!-- Subtitle - Enhanced readability and spacing -->
			<p
				class={[
					"mx-auto mt-10 max-w-3xl transition-all duration-1000 ease-out",
					"text-title3 md:text-title2",
					imageSrc ? "text-white/95" : "text-muted-foreground",
					mounted ? "translate-y-0 opacity-100 delay-300" : "translate-y-8 opacity-0"
				]}
			>
				{subtitle}
			</p>

			<!-- CTAs - Modern button treatment with better spacing -->
			{#if callsToAction.length > 0}
				<div
					class={[
						"mt-16 flex flex-wrap items-center justify-center gap-4 transition-all duration-1000 ease-out",
						mounted ? "translate-y-0 opacity-100 delay-[400ms]" : "translate-y-8 opacity-0"
					]}
				>
					{#each callsToAction as cta, index}
						<Button
							href={cta.href}
							size="lg"
							variant={index % 2 === 0 ? "primary" : "secondary"}
							class="min-w-[180px]"
						>
							{cta.label}
						</Button>
					{/each}
				</div>
			{/if}
		</div>

		<!-- Refined scroll indicator -->
		<div
			class={[
				"absolute bottom-12 left-1/2 -translate-x-1/2 transition-all duration-1000 ease-out",
				mounted ? "translate-y-0 opacity-40 delay-500" : "translate-y-8 opacity-0"
			]}
		>
			<div class={[
				"mx-auto h-12 w-6 rounded-full border-2 p-1",
				imageSrc ? "border-white/40" : "border-muted-foreground/30"
			]}>
				<div
					class={[
						"h-2 w-2 rounded-full",
						imageSrc ? "bg-white/70" : "bg-muted-foreground/50"
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

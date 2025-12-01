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

<div class="bg-background" {...rest}>
	<header
		class="section-px container mx-auto grid place-items-center text-center"
		style="padding-top: clamp(6rem, 12vw, 10rem); padding-bottom: clamp(6rem, 12vw, 10rem);"
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
					mounted ? "translate-y-0 opacity-100" : "translate-y-8 opacity-0"
				]}
			>
				{title}
			</h1>

			<!-- Subtitle - Clean and Spacious -->
			<p
				class={[
					"text-muted-foreground mx-auto mt-8 max-w-2xl transition-all duration-1000 ease-out",
					"text-headline md:text-title3",
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

			<!-- Optional Hero Image -->
			{#if imageSrc}
				<div
					class={[
						"mt-16 transition-all duration-1000 ease-out",
						mounted ? "translate-y-0 opacity-100 delay-400" : "translate-y-8 opacity-0"
					]}
				>
					<img
						src={imageSrc}
						alt="Hero visual"
						class="mx-auto w-full max-w-5xl rounded-lg border border-border"
					/>
				</div>
			{/if}
		</div>

		<!-- Subtle scroll indicator -->
		<div
			class={[
				"mt-24 transition-all duration-1000 ease-out",
				mounted ? "translate-y-0 opacity-30 delay-500" : "translate-y-8 opacity-0"
			]}
		>
			<div class="mx-auto h-12 w-6 rounded-full border-2 border-muted-foreground/20 p-1">
				<div
					class="animate-bounce-slow h-2 w-2 rounded-full bg-muted-foreground/40"
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

<!--
@component AboutTeaser
An engaging founder story teaser that builds personal connection and company credibility.
-->
<script lang="ts">
	// Types
	type TeamMember = {
		name: string;
		role: string;
		image: string;
	};

	// Components
	import Button from "../ui/Button.svelte";
	import ScrollText from "./sub/ScrollText.svelte";

	// State
	let sectionRef: HTMLElement;

	let props = $props();

	// Data
	const teamMember: TeamMember = {
		name: "Alex Morgan",
		role: "Founder & CEO",
		image: "/generated/image-a-confident-small-business-founder-in-th.webp"
	};

	const founderQuote = `"I watched my father's restaurant nearly fold because his broker sold him a policy that didn't cover water damage. When the pipe burst, he learned the hard way that 'comprehensive' didn't mean what he thought. That moment taught me something: small business owners shouldn't need to become insurance experts just to protect what they've built. There had to be a better way."`;
</script>

<section bind:this={sectionRef} {...props}>
	<div class="section-px section-py container mx-auto">
		<div class="relative mx-auto grid max-w-3xl place-items-center gap-12">
			<!-- Founder Quote -->
			<ScrollText
				class="text-title2 text-center leading-relaxed"
				text={founderQuote}
			/>

			<!-- Founder Profile & CTA -->
			<div class="flex flex-col items-center gap-6 sm:flex-row sm:items-center">
				<img
					src={teamMember.image}
					alt={teamMember.name}
					class="size-16 rounded-full object-cover ring-2 ring-primary/10"
				/>
				<div class="text-center sm:text-left">
					<div class="text-callout font-medium">{teamMember.name}</div>
					<div class="text-caption text-emphasis-medium">{teamMember.role}</div>
				</div>
				<Button href="/about" variant="secondary" size="sm" class="sm:ml-4">
					Read our story
				</Button>
			</div>
		</div>
	</div>
</section>

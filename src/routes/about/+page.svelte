<script lang="ts">
	// Components
	import CallToAction from "$lib/components/layout/CallToAction.svelte";

	// Icons
	import StakeholderGrid from "$lib/components/layout/StakeholderGrid.svelte";
	import Story from "./Story.svelte";
	import SecondaryHero from "$lib/components/layout/hero-sections/SecondaryHero.svelte";
	import Culture from "$lib/components/layout/Culture.svelte";

	// Constants
	const values = [
		{
			title: "Transparency first",
			description: "No hidden fees, no confusing jargon, no surprises. We believe small business owners deserve to understand exactly what they're buying and why."
		},
		{
			title: "Speed without compromise",
			description: "AI helps us move fast, but we never sacrifice accuracy or coverage quality. You get quotes in minutes with the confidence of thorough risk analysis."
		},
		{
			title: "Human when it matters",
			description: "Technology handles the repetitive work so our licensed experts can focus on the complex decisions that truly need human judgment and empathy."
		}
	];
</script>

<SecondaryHero
	title="Making insurance work for small businesses"
	subtitle="We're building the future of commercial insurance—transparent, fast, and designed for entrepreneurs who deserve better."
	imageSrc="/generated/image-modern-insurance-tech-startup-team-colla.webp"
/>

<!-- Story Section -->
<Story
	paragraphs={[
		"We started this company after watching too many small business owners get burned by confusing insurance policies and predatory pricing. One of our founders spent three months trying to get proper coverage for her first retail store—only to discover critical gaps after a minor incident. That's when we knew something had to change.",
		"The commercial insurance industry hasn't evolved in decades. Brokers still operate on opaque commission structures, policies are written in impenetrable legal language, and small businesses pay inflated premiums because they lack negotiating power. We saw an opportunity to use machine learning to level the playing field.",
		"Our AI analyzes thousands of data points to match businesses with optimal coverage in minutes, not weeks. We've eliminated the traditional broker markup by automating the heavy lifting, passing those savings directly to our customers. But we didn't stop there—we also built a hybrid model where licensed insurance experts are available whenever you need human guidance.",
		"Today, we're proud to serve thousands of small businesses across the country, saving them an average of 30% on premiums while providing better coverage. Every policy we write, every claim we help process, and every business we protect reinforces why we do this work. Small business owners deserve insurance that actually works for them."
	]}
/>

<!-- Our Culture Section -->
<Culture {values} />

<!-- StakeholderGrid Section -->
<StakeholderGrid
	stakeholderType="team"
	title="Our team"
	subtitle="Insurance experts and technologists working together"
	stakeholders={[
		{
			name: "Sarah Mitchell",
			position: "Founder & CEO",
			bio: "Former retail business owner who experienced insurance frustrations firsthand. Built this company to give small businesses the clarity and protection they deserve.",
			image: "/generated/image-professional-woman-ceo-in-modern-office-.webp"
		},
		{
			name: "Marcus Chen",
			position: "Chief Technology Officer",
			bio: "Machine learning engineer with 12 years building AI systems at scale. Passionate about using technology to solve real-world problems for everyday businesses.",
			image: "/generated/image-professional-man-cto-in-tech-startup-env.webp"
		},
		{
			name: "Jennifer Rodriguez",
			position: "Chief Operating Officer",
			bio: "Licensed insurance broker with 15 years of industry experience. Leads our hybrid human-AI approach to ensure customers get expert guidance when they need it.",
			image: "/generated/image-professional-woman-coo-in-business-setti.webp"
		}
	]}
/>

<StakeholderGrid
	stakeholderType="investor"
	title="Backed by the best"
	subtitle="Leading investors who believe in our mission"
	stakeholders={[
		{
			name: "Point Nine Capital",
			image: "https://cdn.brandfetch.io/pointnine.com/w/400/h/400/logo?c=1id_elLz2Bd5Ej-dWo7"
		},
		{
			name: "TSIC Ventures",
			image: "https://cdn.brandfetch.io/tiny.vc/w/400/h/400/logo?c=1a2b3c4d5e"
		},
		{
			name: "Sequoia Capital",
			image: "https://cdn.brandfetch.io/sequoiacap.com/w/400/h/400/logo"
		}
	]}
/>

<!-- CTA Section -->
<CallToAction
	title="Ready to experience better insurance?"
	subtitle="Get your custom quote in minutes"
	description="Join thousands of small business owners who've discovered the clarity and savings of AI-powered insurance matching. No confusing jargon, no hidden fees, no waiting—just the right coverage for your business."
	imageSrc="/generated/image-welcoming-insurance-team-ready-to-help-c.webp"
	callsToAction={[
		{ href: "/contact", label: "Get your free quote", variant: "primary" },
		{ href: "/", label: "Learn more", variant: "secondary" }
	]}
/>

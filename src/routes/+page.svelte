<script lang="ts">
	// Components
	import Summary from "$lib/components/layout/Summary.svelte";
	import Features from "$lib/components/layout/Features.svelte";
	import Testimonials from "$lib/components/layout/Testimonials.svelte";
	import CallToAction from "$lib/components/layout/CallToAction.svelte";
	import AboutTeaser from "$lib/components/layout/AboutTeaser.svelte";
	import LogoScroller from "$lib/components/layout/LogoScroller.svelte";
	import BuildHero from "$lib/components/layout/hero-sections/BuildHero.svelte";
	import AnimateIn from "$lib/components/animation/AnimateIn.svelte";

	// Icons
	import IconZap from "~icons/lucide/zap";
	import IconDollarSign from "~icons/lucide/dollar-sign";
	import IconFileText from "~icons/lucide/file-text";
	import IconShield from "~icons/lucide/shield";
	import IconArrowLeftRight from "~icons/lucide/arrow-left-right";
	import IconHeadphones from "~icons/lucide/headphones";
	import IconUsers from "~icons/lucide/users";
	import IconBriefcase from "~icons/lucide/briefcase";
	import IconHome from "~icons/lucide/home";
	import IconHardHat from "~icons/lucide/hard-hat";
	import IconLock from "~icons/lucide/lock";
	import IconTruck from "~icons/lucide/truck";
</script>

<AnimateIn delay={0}>
	<BuildHero
		title="Commercial insurance that actually makes sense"
		subtitle="AI-powered matching finds your optimal coverage in minutes, not weeks. No confusing jargon, no excessive fees—just the right protection for your business."
		imageSrc="/generated/image-a-modern-city-skyline-at-golden-hour-foc.webp"
		callsToAction={[
			{ href: "/contact", label: "Get a quote" },
			{ href: "/about", label: "How it works" }
		]}
	/>
</AnimateIn>

<AnimateIn delay={200}>
	<LogoScroller
		label="Trusted by growing businesses"
		logoUrls={[
			'https://cdn.brandfetch.io/shopify.com/w/400/h/400/logo',
			'https://cdn.brandfetch.io/squarespace.com/w/400/h/400/logo',
			'https://cdn.brandfetch.io/mailchimp.com/w/400/h/400/logo',
			'https://cdn.brandfetch.io/stripe.com/w/400/h/400/logo'
		]}
	/>
</AnimateIn>

<AnimateIn delay={300}>
	<Summary
		title="Why we exist"
		text="Small business owners shouldn't need an insurance degree to protect what they've built. We analyze your unique risk profile using machine learning and match you with optimal coverage in minutes—eliminating confusing policies, excessive broker fees, and weeks of back-and-forth. It's the clarity and speed you deserve, powered by AI that actually understands your business."
	/>
</AnimateIn>

<AnimateIn delay={400}>
	<Features
		title="Coverage types for your business"
		subtitle="Comprehensive protection tailored to small business needs"
		features={[
			{
				title: "General liability",
				description:
					"Protects against customer injuries, property damage claims, and advertising injury lawsuits that could threaten your business.",
				icon: IconUsers
			},
			{
				title: "Professional liability",
				description:
					"Covers errors, omissions, and negligence claims from clients who say your services caused them financial harm.",
				icon: IconBriefcase
			},
			{
				title: "Property insurance",
				description:
					"Safeguards your physical assets—buildings, equipment, inventory—from fire, theft, vandalism, and natural disasters.",
				icon: IconHome
			},
			{
				title: "Workers' compensation",
				description:
					"Required in most states, covers medical costs and lost wages when employees get injured or sick on the job.",
				icon: IconHardHat
			},
			{
				title: "Cyber liability",
				description:
					"Protects against data breaches, ransomware attacks, and customer notification costs in our digital-first world.",
				icon: IconLock
			},
			{
				title: "Commercial auto",
				description:
					"Covers vehicles used for business purposes, including liability and physical damage for cars, trucks, and vans.",
				icon: IconTruck
			}
		]}
	/>
</AnimateIn>

<AnimateIn delay={500}>
	<Testimonials
		testimonials={[
			{
				name: "Maria Rodriguez",
				position: "Owner",
				company: "Verde Kitchen Supply",
				quote:
					"We got our liability and property coverage quote in 20 minutes instead of waiting weeks for broker callbacks. Saved $4,200 annually compared to our old policy, and the AI actually explained what we were buying in plain English.",
				image: "/generated/image-2-editorial-lifestyle-image-of-a-hispani.webp"
			},
			{
				name: "James Chen",
				position: "Founder",
				company: "Precision Auto Body",
				quote:
					"After a customer injury scare, I realized our coverage had serious gaps. Their risk analysis caught three exposures my previous broker missed. Now I sleep better knowing we're actually protected, not just paying premiums.",
				image: "/generated/image-3-editorial-documentary-style-photo-of-a.webp"
			},
			{
				name: "David Thompson",
				position: "Managing Partner",
				company: "Thompson & Associates Consulting",
				quote:
					"Shopping for professional liability used to mean deciphering dozens of confusing proposals. Their platform compared eight carriers in minutes and highlighted exactly where coverage differed. Closed our policy the same day.",
				image: "/generated/image-4-editorial-lifestyle-shot-of-a-professi.webp"
			}
		]}
	/>
</AnimateIn>

<AnimateIn delay={600}>
	<Features
		title="Coverage made simple"
		subtitle="Get the protection your business needs without the headaches that usually come with it"
		features={[
			{
				title: "Instant AI matching",
				description:
					"Our machine learning analyzes your business profile and matches you with optimal coverage in minutes. No more waiting weeks for broker callbacks or wading through irrelevant policies.",
				icon: IconZap
			},
			{
				title: "Transparent pricing",
				description:
					"See exactly what you're paying for with clear breakdowns and no hidden fees. We save small businesses an average of 30% compared to traditional brokers.",
				icon: IconDollarSign
			},
			{
				title: "Plain English policies",
				description:
					"Insurance shouldn't require a law degree to understand. We translate complex insurance jargon into clear language so you know exactly what's covered.",
				icon: IconFileText
			},
			{
				title: "Smart risk analysis",
				description:
					"Our AI evaluates your specific business risks and recommends coverage tailored to your industry. Get protection that actually fits your needs, not a one-size-fits-all package.",
				icon: IconShield
			},
			{
				title: "One-click comparisons",
				description:
					"Compare multiple insurance options side-by-side with clear pros and cons. Make informed decisions without spreadsheets or confusion.",
				icon: IconArrowLeftRight
			},
			{
				title: "Human support when needed",
				description:
					"AI handles the heavy lifting, but licensed insurance experts are available whenever you need guidance. Get the best of automation and human expertise.",
				icon: IconHeadphones
			}
		]}
	/>
</AnimateIn>

<AnimateIn delay={700}>
	<AboutTeaser />
</AnimateIn>

<AnimateIn delay={800}>
	<CallToAction 
		title="Ready to protect your business?"
		subtitle="Get your custom quote in minutes"
		description="Join thousands of small business owners who've discovered smarter, faster insurance. Our AI analyzes your unique needs and delivers personalized coverage options—no confusing jargon, no hidden fees, no waiting. Start your quote now and see why businesses are making the switch."
		imageSrc="/generated/image-5-editorial-photo-of-a-business-owner-re.webp"
		callsToAction={[
			{ href: "/contact", label: "Get your free quote", variant: "primary" },
			{ href: "/about", label: "See how it works", variant: "secondary" }
		]}
	/>
</AnimateIn>

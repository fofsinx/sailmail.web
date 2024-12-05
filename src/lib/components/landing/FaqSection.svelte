<script lang="ts">
	import { ChevronDown } from 'lucide-svelte';
	import { cn } from '$lib/utils';
	import { slide } from 'svelte/transition';
	import { inview } from 'svelte-inview';

	const faqs = [
		{
			question: 'Is Sailmail really free?',
			answer:
				"Yes! The Community Edition is free forever. We're building a sustainable open-source project that benefits everyone."
		},
		{
			question: 'Can I self-host Sailmail?',
			answer:
				'Absolutely! Sailmail is designed to be self-hosted. Check out our deployment guides to get started with Docker or Kubernetes.'
		},
		{
			question: 'How does Sailmail compare to commercial services?',
			answer:
				'Sailmail offers similar features to commercial services but with complete control over your data and infrastructure, plus the flexibility to modify the code for your needs.'
		},
		{
			question: 'What about support?',
			answer:
				'Community support is available through GitHub discussions and our Discord community. Enterprise customers receive dedicated support with SLAs.'
		},
		{
			question: 'Is Sailmail production-ready?',
			answer:
				'Yes! Many companies are already using Sailmail in production. Our enterprise customers process millions of emails monthly.'
		},
		{
			question: 'Can I contribute to Sailmail?',
			answer:
				'Absolutely! We welcome contributions from the community. Check out our contribution guidelines on GitHub to get started.'
		}
	];

	let openIndex: number | null = null;

	function toggleFaq(index: number) {
		openIndex = openIndex === index ? null : index;
	}
</script>

<section
	class="relative mx-auto max-w-7xl px-6 py-24 sm:py-32 lg:px-8 lg:py-40"
	use:inview={{ unobserveOnEnter: true, rootMargin: '-50px' }}
>
	<div class="mx-auto max-w-4xl divide-y divide-gray-900/10 dark:divide-gray-100/10">
		<h2 class="mb-12 text-center text-2xl font-bold leading-10 tracking-tight">
			Frequently asked questions
		</h2>
		<dl class="mt-10 space-y-6 divide-y divide-gray-900/10 dark:divide-gray-100/10">
			{#each faqs as faq, index}
				<div class={cn('pt-6', index === 0 ? 'pt-6' : '')}>
					<dt>
						<button
							on:click={() => toggleFaq(index)}
							class={cn(
								'flex w-full items-start justify-between text-left',
								'group transition-colors duration-200',
								'hover:text-gray-900 dark:hover:text-gray-100'
							)}
						>
							<span class="text-base font-semibold leading-7">{faq.question}</span>
							<span class="ml-6 flex h-7 items-center">
								<ChevronDown
									class={cn(
										'size-6 transition-transform duration-200',
										openIndex === index ? 'rotate-180 transform' : ''
									)}
									aria-hidden="true"
								/>
							</span>
						</button>
					</dt>
					{#if openIndex === index}
						<dd
							class="mt-2 pr-12"
							transition:slide={{
								duration: 400,
								easing: (t) => {
									return 1 - Math.pow(1 - t, 4); // Ease out quart for extra smoothness
								}
							}}
						>
							<p class="text-base leading-7 text-gray-600 dark:text-gray-400">
								{faq.answer}
							</p>
						</dd>
					{/if}
				</div>
			{/each}
		</dl>
	</div>

	<!-- Background Effects -->
	<div class="absolute inset-0 -z-10 overflow-hidden">
		<div
			class="absolute left-[50%] top-0 h-[40rem] w-[80rem] -translate-x-[50%] opacity-30 [mask-image:radial-gradient(farthest-side,white,transparent)]"
		>
			<div
				class="absolute inset-0 bg-gradient-to-r from-[var(--color-one)] via-[var(--color-two)] to-[var(--color-three)] [mask-image:radial-gradient(circle_at_center,white,transparent_70%)]"
			/>
		</div>
	</div>
</section>

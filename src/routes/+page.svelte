<script lang="ts">
	import { _ } from '$lib/i18n';
	import type { PageData } from './$types';
	import { onMount } from 'svelte';

	import Card from '$lib/ui/Card.svelte';
	import Logo from '$lib/ui/Logo.svelte';
	import SmallProductCard from '$lib/ui/SmallProductCard.svelte';

	interface Props {
		data: PageData;
	}

	let { data }: Props = $props();

	onMount(() => {
		function sendHeight() {
			// Use scrollHeight to get the full height of the content
			const height = document.body.scrollHeight;
			// Send the height to the parent window. '*' is a wildcard for the target origin.
			// For better security, replace it with the actual domain of the parent page if known.
			parent.postMessage({ frameHeight: height }, '*');
		}

		// Send the height on initial load
		sendHeight();
		// Send the height whenever the window is resized
		window.addEventListener('resize', sendHeight);
	});
</script>

<svelte:head>
	<!-- Preconnect to static assets -->
	<link rel="preconnect" href="https://images.openfoodfacts.org" crossorigin="anonymous" />

	<title>Open Food Facts Explorer</title>
</svelte:head>

<div class="mx-auto my-4 flex flex-col items-center md:container xl:max-w-6xl">
	<Card>
		<div class="card-body items-center px-0 text-center">
			<h3 class="card-title mb-4 block text-2xl md:flex">
				{$_('home.welcome')}
				<div class="block xl:inline-block">
					<Logo />
				</div>
				Explorer!
			</h3>
			<!-- eslint-disable-next-line svelte/no-at-html-tags -->
			<p>{@html $_('home.intro_1')}</p>
			<p>{$_('home.intro_2')}</p>
		</div>
	</Card>

	<div class="mt-8 flex w-full">
		<div
			class="grid w-full grid-cols-1 gap-4 sm:grid-cols-2 lg:grid-cols-3 lg:gap-2 xl:grid-cols-3"
		>
			{#await data.streamed.products}
				{#each [...Array(4).keys()] as i (i)}
					<div class="skeleton dark:bg-base-300 h-28 bg-white p-4 shadow-md"></div>
				{/each}
			{:then products}
				{#each products as state (state.product.code)}
					<SmallProductCard product={state.product} />
				{/each}
			{/await}
		</div>
	</div>
	<div class="xl:max-w-8xl container mx-auto mt-16 px-4">
		<donation-banner></donation-banner>
	</div>
</div>
<script>
	import '$lib/prism-theme.postcss';

	export let title;
	export let intro;
	export let date;
	export let thumbnail;
	export let client;

	let dateDisplay = new Date(Date.parse(date)).toLocaleDateString('en-UK', {
		year: 'numeric'
	});
</script>

<svelte:head>
	<title>{title} - Justin Venbrux</title>
</svelte:head>

<div class="prose prose-sm sm:prose page max-w-none sm:max-w-none">
	<div class="py-8 sm:py-10">
		<div class="no-underline hidden sm:block mb-16 text-sm text-bold not-prose"><a href="/" class="text-teal-500 hover:text-black">← Back to home</a></div>
		<div class="leading-relaxed text-4xl mt-0 sm:text-6xl font-Outfit font-medium">{title}</div>
		<div class="mt-2 sm:mt-8">{intro}</div>
		<div class="text-xs text-gray-500 my-4 ">{dateDisplay} {#if client}- {client}{/if}</div>
	</div>
	{#if thumbnail}
		<img src={`/${thumbnail}`} class="fancy" alt="Banner {title}" />
	{/if}

	<slot />
</div>


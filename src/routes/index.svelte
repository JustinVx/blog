<script context="module">
	export const prerender = true;
	export async function load({ session }) {
		const posts = session.posts;
		return { props: { posts } };
	}
</script>

<script>
	import Grouper from '../components/Grouper.svelte';
	export let posts;

	const formatDate = (value) => {
		const date = new Date(value);
		return new Intl.DateTimeFormat('nl-NL', {
			year: undefined,
			month: 'long',
			day: 'numeric'
		}).format(date);
	};

	const getYearFromPost = (post) => {
		return post.parsedDate.getFullYear();
	};
</script>

<svelte:head>
	<title>Justin Venbrux</title>
</svelte:head>

<div class="max-w-none page mx-auto py-4 sm:py-4">
	<div
		class="flex flex-col sm:flex-row justify-between items-center mb-10 md:my-12 lg:my-16 lg:mb-24"
	>
		<div class="order-1 sm:order-0 text-sm sm:text-base">
			<div>
				<div class="text-xs text-gray-500 my-4 uppercase">About me</div>
				<p class="mb-2">
					I create cools things that help people. Currently I'm working as a User Experience Designer at <a class="font-bold underline" href="https://www.sodastudio.nl">Soda Studio</a>. I have an academic background at the <a class="font-bold underline" href="https://www.tudelft.nl/en/">Delft University of Technology</a> and about 5 years worth of experience in digital product design.
				</p>
				<p>
					I love to learn. My interests range from technology, healthcare, culture, systems, psychology and sociology to finding out what this whole web3 thing is about or trying a new recipe for kumpir. I also dabble in SwiftUI, Python and Svelte sometimes.
				</p>
			</div>
		</div>
	</div>

	<div>
		<div class="hidden sm:grid sm:grid-cols-5 gap-x-20 lg:gap-x-16 gap-y-4 mb-12 lg:mb-24">
			<div><img src="/svg/1Minuut.svg" /></div>
			<div><img src="/svg/KLM.svg" /></div>
			<div><img src="/svg/DHH.svg" /></div>
			<div><img src="/svg/Recharge.svg" /></div>
			<div><img src="/svg/Renault.svg" /></div>
			<div><img src="/svg/Soda.svg" /></div>
			<div><img src="/svg/Twill.svg" /></div>
			<div><img src="/svg/Secrid.svg" /></div>
			<div><img src="/svg/Veringmeier.svg" /></div>
			<div><img src="/svg/TU.svg" /></div>
		</div>
	</div>

	<div>
		<div class="text-xs text-gray-500 my-4 uppercase">Work</div>
		<div class="grid sm:grid-cols-2 gap-6 my-8">
			<Grouper items={posts} groupForItem={getYearFromPost} let:group let:item>
				<div class="p-4 border-2 border-gray-200 hover:-translate-y-1 bg-white rounded-2xl" slot="item">
					<a href={`./${item.slug}`}>
						<img class="mb-4 rounded-xl" src={item.thumbnail} alt={item.title} />
						<div class="title font-medium text-xl font-Outfit mb-1">{item.title}</div>
						<div class="date text-gray-600 font-light text-sm">{item.description}</div>
						<div class="no-underline block sm:hidden mt-4 mb-2 text-sm text-bold"><a href={`./${item.slug}`} class="text-teal-500 hover:text-black">Learn more →</a></div>
					</a>
				</div>
			</Grouper>
		</div>
	</div>
</div>


<script>
	import '../app.postcss';
</script>

<div class="font-inter h-screen flex flex-col">
	<header class="mt-4 sm:mt-16">
		<div class="grid hoofd items-center">
			<div class="flex justify-end py-4 text-xs">
				<img alt="Profile pic" src="/small.jpg" class="rounded-full w-12 h-12 bg-white border-2 border-gray-200" />
			</div>
			<h1 class="text-xs uppercase font-bold p-4">
				<a class="tracking-widest hover:text-teal-500" href="/">Justin Venbrux</a>
			</h1>
		</div>
	</header>
	<div class="flex-grow">
		<slot />
	</div>
	<footer class="text-xs text-center p-4 sm:p-8 mt-16">
		<div>© 2021 Justin Venbrux, All Rights Reserved.</div>
	</footer>
</div>

<style>
.hoofd {
	grid-template-columns:
		1fr
		min(72ch, 100%)
		1fr;
}
</style>

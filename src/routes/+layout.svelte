<script>
	import { page } from '$app/stores';
	import '../app.css';

	const links = [
		{ name: 'Inicio', href: '/' },
		// { name: 'Audiovisuales', href: '/audiovisuales' },
		// { name: 'Composición', href: '/composicion' },
		// { name: 'Producción', href: '/produccion' },
		{ name: 'Portfolio', href: '/portfolio' },
		{ name: 'Nosotros', href: '/nosotros' },
		{ name: 'Contacto', href: '/contacto' }
	];
</script>

<main class="">
	<slot />
</main>

<nav
	class="fixed bottom-0 z-50 flex h-[25vh] w-full items-center bg-gray-200/10 px-8 text-white backdrop-blur-sm md:h-[15vh] md:justify-between"
>
	<ul
		class="grid w-fit max-w-[600px] grid-cols-2 justify-between px-8 uppercase md:flex md:w-full md:justify-between md:gap-0 md:px-0"
	>
		{#each links as { name, href }}
			<li class="px-6 py-2 font-victor md:px-0 md:py-0">
				<a
					{href}
					class="opacity-50 transition hover:opacity-80"
					aria-current={$page.url.pathname === href}>{name}</a
				>
			</li>
		{/each}
	</ul>
	<div class="">sound</div>
</nav>

<style>
	a[aria-current='true'] {
		opacity: 100;
		filter: drop-shadow(0 0 0.6rem rgba(255, 255, 255, 0.4));
	}
</style>

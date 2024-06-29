<script>
	import { page } from '$app/stores';
	import { Shuffle, Volume, Volume1, VolumeX } from 'lucide-svelte';
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

<main class="h-full w-full">
	<slot />
</main>

<nav
	class="font-jetbrains fixed bottom-0 z-50 flex h-[25vh] w-full items-center px-8 font-thin text-white md:h-[15vh] md:justify-between lg:text-[1.7rem]"
>
	<ul
		class="grid max-w-[60vw] grid-cols-2 justify-between px-8 lowercase md:flex md:w-full md:justify-evenly md:gap-0 md:px-0"
	>
		{#each links as { name, href }}
			<li class="">
				<a
					{href}
					class="bg-black/70 px-4 py-2 opacity-50 transition hover:opacity-80"
					aria-current={$page.url.pathname === href}><span>{name}</span></a
				>
			</li>
		{/each}
	</ul>

	<!-- controles playback -->
	<div>
		<button class="bg-black p-4 text-white/70"><Shuffle strokeWidth="1.5" size="32" /></button>
		<button class="bg-black p-4 text-white/70"><VolumeX strokeWidth="1.5" size="32" /></button>
	</div>
</nav>

<style>
	a[aria-current='true'] {
		@apply bg-white/70 text-black opacity-100 shadow-inner transition duration-300 ease-in-out;
	}

	a[aria-current='true'] span {
		filter: drop-shadow(0 0.1rem 0.1rem rgba(0, 0, 0, 0.4));
	}
</style>

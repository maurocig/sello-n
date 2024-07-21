<script>
	import BannerHome from './BannerHome.svelte';
	import Description from './Description.svelte';
</script>

<section class="relative flex h-[100vh] shrink-0 items-start justify-center">
	<!-- Título -->
	<h1
		class="z-30 pt-[15vh] font-jetbrains text-6xl font-thin tracking-tighter text-white/80 drop-shadow-[0_0_0.8rem_black]"
	>
		estrugamou
	</h1>
</section>

<Description />

<style>
	.video-gradient {
		background: radial-gradient(ellipse at center, rgba(228, 56, 22, 0.12) 5%, rgb(19, 7, 18) 100%);
	}
</style>

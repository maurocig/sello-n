<script>
	import BannerHome from './BannerHome.svelte';
	import Description from './Description.svelte';
</script>

<section class="relative flex h-[100vh] shrink-0 items-start justify-center">
	<video
		muted
		autoplay
		loop
		playsinline
		disablepictureinpicture
		class="absolute -z-10 h-full w-full object-cover"
	>
		<source src="/stills-2-15clip-webpages.m4v" type="video/mp4" />
	</video>
	<div class="to-emerald-930 video-gradient absolute h-full w-full"></div>
	<div
		class="absolute h-full w-full bg-gradient-to-b from-rose-300/40 via-transparent to-black/60"
	></div>
	<!-- Título -->
	<h1
		class="font-jetbrains z-30 pt-[15vh] text-6xl font-thin tracking-tighter text-white/80 drop-shadow-[0_0_0.8rem_black]"
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

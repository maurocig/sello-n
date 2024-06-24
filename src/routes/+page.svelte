<script>
	import BannerHome from './BannerHome.svelte';
	import Description from './Description.svelte';
</script>

<section class="relative flex h-[80vh] shrink-0 items-center justify-center">
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
	<div
		class="absolute h-full w-full bg-gradient-to-b from-slate-900 via-transparent to-slate-900"
	></div>
	<h1 class="z-30 text-6xl text-white/80 drop-shadow-[0_0_0.8rem_black]">estrugamou</h1>
</section>

<Description />

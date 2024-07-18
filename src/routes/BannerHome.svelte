<script>
	import { ArrowBigDown, ChevronDownCircle } from 'lucide-svelte';
</script>

<div class="flex h-[100vh] w-full flex-col items-center justify-center bg-black text-slate-200">
	<slot />
	<button
		class="absolute bottom-[20vh] bg-transparent text-white/30 transition hover:text-white/60"
	>
		<ChevronDownCircle size={50} strokeWidth={0.8} class="" />
	</button>
</div>

<style>
</style>

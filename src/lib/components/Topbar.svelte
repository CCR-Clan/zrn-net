<script lang="ts">
	import { Button, buttonVariants } from '$lib/components/ui/button/index.js';
	import * as DropdownMenu from '$lib/components/ui/dropdown-menu/index.js';
</script>

<div
	class="sticky top-0 z-50 w-full border-b bg-background/95 backdrop-blur supports-[backdrop-filter]:bg-background/60"
>
	<div class="container flex h-16 items-center">
		<div class="mr-4 flex">
			<a href="/" class="mr-6 flex items-center space-x-2">
				<span class="oswald-font-topbar text-xl font-bold">Zerion</span>
			</a>
			<nav class="flex items-center space-x-6 text-sm font-medium">
				<a href="/players" class={buttonVariants({ variant: 'ghost' })}>Players</a>
				<a href="/about" class={buttonVariants({ variant: 'ghost' })}>About</a>
				<a href="https://discord.gg/mJGeqBs6Q5" class={buttonVariants({ variant: 'ghost' })}>Join</a>
			</nav>
		</div>
	</div>
</div>

<style>
	.oswald-font-topbar {
		font-family: 'Oswald', sans-serif;
		font-optical-sizing: auto;
		font-weight: 700;
		font-style: bold;
	}
	.oswald-font-drop {
		font-family: 'Oswald', sans-serif;
		font-optical-sizing: auto;
		font-weight: 500;
		font-style: normal;
	}
</style>

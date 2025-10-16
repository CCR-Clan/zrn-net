<script lang="ts">
	import type { PageData } from './$types';
	import Button from '$lib/components/ui/button/button.svelte';
	import * as Table from '$lib/components/ui/table/index.js';

	interface Rank {
		game: string;
		rank: string;
		peak: string;
		clanRank?: string;
		'Clan Rank'?: string;
		clankRank?: string;
	}

	let {
		data
	}: {
		data: {
			player: {
				socials: any;
				description: any;
				id: any;
				role: any;
				profileImage: string | null | undefined;
				name: any;
				ranks: Rank[];
			};
		};
	} = $props();
</script>

{#if data.player}
	<div class="mx-auto mt-10 flex w-full max-w-7xl px-4 sm:px-6">
		<div class="mx-auto w-full max-w-3xl rounded-2xl border border-white/10 bg-white/5 p-6 shadow-xl backdrop-blur-sm sm:p-8">
			<div class="flex w-full flex-col items-center gap-6 sm:flex-row sm:items-start">
				<img
					class="h-24 w-24 rounded-full border-2 border-orange-400 ring-2 ring-orange-400/30 shadow-lg sm:h-32 sm:w-32"
					alt="{data.player.name} Avatar"
					src={data.player.profileImage}
				/>
				<div class="flex flex-col items-center text-center sm:items-start sm:text-left">
					<h1 class="oswald-font-players bg-gradient-to-r from-orange-300 via-amber-200 to-rose-300 bg-clip-text text-2xl font-extrabold tracking-tight text-transparent sm:text-4xl">
						{data.player.name} · {data.player.role}
					</h1>
					<p class="mt-3 text-base leading-7 text-gray-300 sm:text-lg">{data.player.description}</p>
					<div class="mt-4 flex flex-wrap justify-center gap-2 sm:justify-start">
						{#if data.player.socials}
							{#each data.player.socials as social, i}
								<div class="oswald-font-players">
									<Button href={social.link} variant="link" class="p-0 text-sm hover:text-orange-200 sm:text-base">{social.name}</Button>
									{#if i < data.player.socials.length - 1}
										<span class="mx-2 text-orange-300/70">·</span>
									{/if}
								</div>
							{/each}
						{/if}
					</div>
				</div>
 		</div>
		</div>
	</div>
{:else}
	<div class="mx-auto mt-16 flex w-full max-w-7xl items-center justify-center px-4 sm:px-6">
		<h1 class="rounded-xl border border-white/10 bg-white/5 px-4 py-3 text-xl font-bold text-rose-300 shadow sm:text-2xl">Player Not Found!</h1>
	</div>
{/if}

<style>
	.oswald-font-players {
		font-family: 'Oswald', sans-serif;
		font-optical-sizing: auto;
		font-weight: 700;
		font-style: normal;
	}
</style>

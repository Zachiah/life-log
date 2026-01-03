<script lang="ts">
	const rawData: { date: string; events: (string | [title: string, url: string])[] }[] = [
		{
			date: 'January 1 2026',
			events: [
				'Did my morning routine for 2026 for the first time',
				[
					'Implemented velocity for MIDI input on the music theory app',
					'https://github.com/Zachiah/music-theory/commit/1d8dd3eafe468c8e957f8004689afaf193376767'
				],
				'Practiced improving my left hand piano technique for maybe 30 minutes',
				['Setup this site', 'https://life-log.zachiah.com/']
			]
		},
		{
			date: 'January 2 2026',
			events: [
				'Started building a parser based calculator from scratch in rust',
				'Practiced improving my left hand piano technique for maybe 30 minutes'
			]
		}
	];

	const data: { date: string; events: { title: string; url?: string }[] }[] = rawData.map(
		(day) => ({
			date: day.date,
			events: day.events.map((event) =>
				typeof event === 'string' ? { title: event } : { title: event[0], url: event[1] }
			)
		})
	);
</script>

<div class="flex flex-col gap-4 p-4">
	<div class="flex flex-col gap-2">
		<h1 class="text-4xl">Zachiah's Life Log</h1>
		<p class="text-lg">Most notable accomplishments each day starting 2026</p>
	</div>

	<div class="flex">
		{#each data as day (day.date)}
			<div>
				<h2 class="text-2xl">{day.date}</h2>
				<ul class="list-inside list-disc">
					{#each day.events as event (event.title)}
						<li>
							{#if event.url}
								<!-- eslint-disable-next-line svelte/no-navigation-without-resolve -->
								<a class="text-blue-400" href={event.url}>{event.title}</a>
							{:else}
								{event.title}
							{/if}
						</li>
					{/each}
				</ul>
			</div>
		{/each}
	</div>
</div>

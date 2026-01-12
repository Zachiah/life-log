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
		},
		{
			date: 'January 3 2026',
			events: [
				'Continued working on the parser I started yesterday',
				'Practiced improving my left hand piano technique for maybe 45 minutes'
			]
		},
		{
			date: 'January 4 2026',
			events: [
				'Continued working on the parser',
				'Practiced improving my left hand piano technique for maybe 30 minutes',
				'Went to Bible study',
				'Did a ton of piano improvisation'
			]
		},
		{
			date: 'January 5 2026',
			events: [
				'Triaged/reproed a bunch of issues on zed',
				'Continued working on parser. It can evaluate expressions of the form `a op b` now! Just need to make it recursive',
				'Practice improving my left hand piano technique for maybe 20 minutes'
			]
		},
		{
			date: 'January 6 2026',
			events: [
				'Triaged/reproed issues on zed',
				[
					'Made a PR fixing multibyte multicolumn selections in zed',
					'https://github.com/zed-industries/zed/pull/46214'
				]
			]
		},
		{
			date: 'January 7 2026',
			events: [
				'Triaged/reproed issues on zed',
				[
					'Made a PR fixing multiline search in zed',
					'https://github.com/zed-industries/zed/pull/46298'
				]
			]
		},
		{
			date: 'January 8 2026',
			events: [
				'Triaged/reproed issues on zed',
				[
					'Made a tiny PR making apostrophes not be considered brackets in markdown in zed',
					'https://github.com/zed-industries/zed/issues/45912'
				]
			]
		},
		{
			date: 'January 9 2026',
			events: [
				'Triaged/reproed issues on zed',
				'Had a meeting talking about potentially working at Zed with Conrad',
				'Added tests to 2 of my zed PRs',
				'Convert a project into a monorepo using PNPM',
				'Practiced guitar/piano a bit'
			]
		},
		{
			date: 'January 10 2026',
			events: ['Worked on the monorepo PR from yesterday a bit', 'Did pull-ups']
		},
		{
			date: 'January 11 2026',
			events: ['Triaged a ton of zed issues in the morning and a bit more in the evening']
		},
		{
			date: 'January 12 2026',
			events: ['Triaged/reproed zed issues']
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
		<p class="text-lg">Most notable things I did each day starting 2026</p>
	</div>

	<div class="flex flex-col gap-2">
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

<script lang="ts">
	const bMap = {
		'0': ['', '', '', ''],
		'1': ['active', '', '', ''],
		'2': ['', 'active', '', ''],
		'3': ['active', 'active', '', ''],
		'4': ['', '', 'active', ''],
		'5': ['active', '', 'active', ''],
		'6': ['', 'active', 'active', ''],
		'7': ['active', 'active', 'active', ''],
		'8': ['', '', '', 'active'],
		'9': ['active', '', '', 'active']
	}

	let time = $state<string>('00:00:00 AM')
	let hours = $state<string[]>(['0', '0'])
	let minutes = $state<string[]>(['0', '0'])
	let seconds = $state<string[]>(['0', '0'])

	let bHours = $state<string[]>([])
	let bHours1 = $state<string[]>([])
	let bHours2 = $state<string[]>([])

	let bMinutes = $state<string[]>([])
	let bMinutes1 = $state<string[]>([])
	let bMinutes2 = $state<string[]>([])

	let bSeconds = $state<string[]>([])
	let bSeconds1 = $state<string[]>([])
	let bSeconds2 = $state<string[]>([])

	function toBinary(digit: string): string[] {
		return bMap[digit]
	}

	const interval = setInterval(() => {
		const d = new Date()
		const t = d.toLocaleTimeString()
		time = t
		// break time into hours, minutes, seconds
		const [h, m, s] = t.split(':')

		hours = h.split('')
		if (hours.length === 1) {
			hours.unshift('0')
		}

		minutes = m.split('')
		const [s1, s2] = s.split(' ')
		seconds = s1.split('')

		console.log(hours)

		bHours = toBinary(hours)
		bHours1 = toBinary(hours[0])
		bHours2 = toBinary(hours[1])

		bMinutes = toBinary(minutes)
		bMinutes1 = toBinary(minutes[0])
		bMinutes2 = toBinary(minutes[1])

		bSeconds = toBinary(seconds)
		bSeconds1 = toBinary(seconds[0])
		bSeconds2 = toBinary(seconds[1])
	}, 1000)
</script>

<header>
	<h1>Svelte 5 Binary Clock</h1>
</header>

<section>
	<div class="flex">
		<div class="stack">
			<div class="digit">1</div>
			<div class="digit">2</div>
			<div class="digit">4</div>
			<div class="digit">8</div>
		</div>
		<div class="stack">
			{#each bHours1 as dotStatus}
				<div class="dot {dotStatus}" />
			{/each}
		</div>
		<div class="stack">
			{#each bHours1 as dotStatus}
				<div class="dot {dotStatus}" />
			{/each}
		</div>
		<div class="stack">
			{#each bMinutes1 as dotStatus}
				<div class="dot {dotStatus}" />
			{/each}
		</div>
		<div class="stack">
			{#each bMinutes2 as dotStatus}
				<div class="dot {dotStatus}" />
			{/each}
		</div>
		<div class="stack">
			{#each bSeconds1 as dotStatus}
				<div class="dot {dotStatus}" />
			{/each}
		</div>
		<div class="stack">
			{#each bSeconds2 as dotStatus}
				<div class="dot {dotStatus}" />
			{/each}
		</div>
	</div>
	<div class="flex">
		<div class="digit" />
		<div class="digit">{hours[0]}</div>
		<div class="digit">{hours[1]}&nbsp;</div>
		<div class="digit">{minutes[0]}</div>
		<div class="digit">{minutes[1]}&nbsp;</div>
		<div class="digit">{seconds[0]}</div>
		<div class="digit">{seconds[1]}</div>
	</div>
</section>
<p>(Just refresh me. I am still buggy. 😉)</p>

<style>
	:root {
		--size: 5rem;
	}
	header,
	p {
		text-align: center;
	}
	p {
		font-size: 2rem;
	}
	.flex {
		display: flex;
		justify-content: center;
		align-items: center;
		gap: 1rem;
	}
	.stack {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		gap: 1rem;
	}
	.digit,
	.dot {
		display: grid;
		place-items: center;
		width: var(--size);
		height: var(--size);
	}
	.digit {
		font-size: 4rem;
	}
	.dot {
		border-radius: 50%;
		background-color: rgba(255, 255, 255, 0.1);
	}
	.active {
		background-color: rgba(255, 255, 255, 0.8);
	}
</style>

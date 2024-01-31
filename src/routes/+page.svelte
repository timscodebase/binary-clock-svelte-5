<script lang="ts">
	const Bmap = new Map([
		[0, '0000'],
		[1, '1000'],
		[2, '0100'],
		[3, '1100'],
		[4, '0010'],
		[5, '1010'],
		[6, '0110'],
		[7, '1110'],
		[8, '0001'],
		[9, '1001'],
		[10, '0101']
	])

	let time = $state<string[]>('00:00:00')
	let hours = $state<string[]>([])
	let minutes = $state<string[]>([])
	let seconds = $state<string[]>([])

	function toBinary(arr: number[]): string[] {
		const results: string[] = []
		for (let i = 0; i < arr.length; i++) {
			console.log(`${i}: `, Bmap.get(parseInt(arr[i])), Bmap.get(parseInt(arr[i])))
			results.push(Bmap.get(parseInt(arr[i])))
		}
		return results
	}

	const interval = setInterval(() => {
		const d = new Date()
		const t = d.toLocaleTimeString()
		time = t
		// break time into hours, minutes, seconds
		const [h, m, s] = t.split(':')

		hours = h.split('')
		minutes = m.split('')
		const [s1, s2] = s.split(' ')
		seconds = s1.split('')
		console.log(toBinary(seconds))
	}, 1000)
</script>

<section>
	<div class="flex">
		<p>{hours[0]}</p>
		<p>{hours[1]}</p>
		:
		<p>{minutes[0]}</p>
		<p>{minutes[1]}</p>
		:
		<p>{seconds[0]}</p>
		<p>{seconds[1]}</p>
	</div>
</section>

{#each Bmap as [key, value]}
	<div>
		<p>{key}:</p>
		<p>{value}</p>
	</div>
{/each}

<style>
	div {
		display: grid;
		grid-template-columns: 3ch 1fr;
	}

	.flex {
		display: flex;
		justify-content: center;
		align-items: center;
	}
</style>

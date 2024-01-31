<script lang="ts">
	import '$lib/css/styles.css'
	import { description, title } from '$lib/config.ts'
</script>

<svelte:head>
	<meta property="og:locale" content="en_US" />
	<meta property="og:title" content={title} />
	<meta property="og:description" content={description} />
</svelte:head>

<slot />

<style>
</style>

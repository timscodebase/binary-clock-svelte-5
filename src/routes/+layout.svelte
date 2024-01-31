<script lang="ts">
	import '$lib/css/styles.css'
	import { description, title } from '$lib/config.ts'
	import { t } from 'vitest/dist/index-5aad25c1'
</script>

<svelte:head>
	<meta property="og:locale" content="en_US" />
	<meta property="og:title" content={t} />
	<meta property="og:description" content={description} />
</svelte:head>

<slot />

<style>
</style>

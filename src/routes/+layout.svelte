<script lang="ts">
  import "$lib/scss/global.scss"

	import favicon from '$lib/assets/favicon.svg'
  import Header from "./+layout/Header.svelte"
  import Footer from "./+layout/Footer.svelte"

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<Header />
{@render children()}
<Footer />
<script>
	import '../app.css';
	import Header from '../components/Header/header.svelte';
</script>

<Header />
<div class="p-4 flex justify-center">
	<slot />
</div>

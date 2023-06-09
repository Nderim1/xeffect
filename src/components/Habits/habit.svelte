<script>
	import Calendar from './calendar.svelte';
</script>

<div class="m-4 border p-4 border-secondary w-96 w-max-96 rounded-md">
	<button class="w-full flex p-2 border-l-4 border-l-orange-700 justify-between">
		<div class="text-left">
			<p>Workout 💪🏽</p>
			<small>Every day</small>
		</div>
		<div class="flex place-self-center">
			<svg
				xmlns="http://www.w3.org/2000/svg"
				fill="none"
				viewBox="0 0 24 24"
				stroke-width="1.5"
				stroke="currentColor"
				class="w-6 h-6"
			>
				<path stroke-linecap="round" stroke-linejoin="round" d="M8.25 4.5l7.5 7.5-7.5 7.5" />
			</svg>
		</div>
	</button>
	<Calendar />
</div>

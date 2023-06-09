<script>
	import { Tooltip } from '@svelte-plugins/tooltips';

	// Get the current date
	const currentDate = new Date();

	const currentDay = currentDate.getDate();

	// Get the current month
	const currentMonth = currentDate.getMonth();
	const monthName = currentDate.toLocaleString('default', { month: 'long' });

	// Get the current year
	const currentYear = currentDate.getFullYear();

	// Get the number of days in the current month
	const numberOfDays = new Date(currentYear, currentMonth + 1, 0).getDate();

	let days = Array.from({ length: numberOfDays }, (_, i) => i + 1);
	const weekdays = ['M', 'T', 'W', 'T', 'F', 'S', 'S'];

	// get the first day of the month and calculate by how much the calendar needs to shift
	const firstWeekday = currentDate.getDay() - 1;
	const empty = Array.from({ length: firstWeekday }, () => '');
</script>

<div class="w-auto max-w-sm w-max-96 h-96 grid gap-0 grid-cols-7">
	<!-- <span>{monthName}</span> -->
	<!-- <div class=""> -->
	{#each weekdays as weekDay}
		<div class="flex justify-center items-center font-semibold">{weekDay}</div>
	{/each}
	{#each empty as emptyDay}
		<div class="">{emptyDay}</div>
	{/each}
	{#each days as day}
		<Tooltip
			content={day > currentDay
				? `<span class='whitespace-nowrap'>Complete day ${day}!</span>`
				: "<span class='whitespace-nowrap'>No action!</span>"}
			animation={day > currentDay ? 'bounce' : 'fade'}
		>
			<button
				class="w-full h-full border border-dotted p-1 cursor-pointer
      {currentDay !== day && 'opacity-50'}
      {day < currentDay ? 'previousDays' : 'day'}"
			>
				{day}
			</button>
		</Tooltip>
	{/each}
	<!-- </div> -->
</div>

<style>
	.previousDays {
		background-image: none;
		cursor: auto;
	}
	.day {
		background-image: url("data:image/svg+xml;charset=utf-8,%3Csvg%20width='8'%20height='8'%20viewBox='0%200%206%206'%20xmlns='http://www.w3.org/2000/svg'%3E%3Cpath%20d='M5%200h1L0%206V5zm1%205v1H5z'%20fill='%239C92AC'%20fill-opacity='0.4'%20fill-rule='evenodd'/%3E%3C/svg%3E");
	}

	.day:hover {
		scale: 1.2;
		opacity: 1;
		transition: 400ms;
	}
</style>

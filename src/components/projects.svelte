<script>
	import { onMount } from 'svelte';

	let myProjectsData;

	let fetchData = async () => {
		try {
			const response = await fetch('/data/my-work-details.json');

			if (response.ok) {
				const data = await response.json();
				myProjectsData = data;
			} else {
				console.error('Failed to fetch projects:', response.status);
			}
		} catch (error) {
			console.error('Error fetching projects:', error);
		}
	};

	fetchData();
</script>

<section>
	<h2>My Work</h2>

	<section>
		<!-- For each -->
		{#if myProjectsData}
			{#each myProjectsData as project}
				{project.project_name}
			{/each}
		{:else}
			<p>Sorry, er ging iets mis met het fetchen van mijn projecten. Laat het mij weten!</p>
		{/if}
	</section>
</section>

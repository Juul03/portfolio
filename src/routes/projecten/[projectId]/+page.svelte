<script>
	import { onMount } from 'svelte';

	let lastSegment;
	let activeProject;
	let error = null;

	let getProjectData = async (project) => {
		try {
			const response = await fetch(`/data/${project}.json`);
			if (!response.ok) {
				throw new Error(`Failed to fetch data for ${project}.`);
			}
			const data = await response.json();
			console.log('dataaaa of the project', data);
			activeProject = data[0];
		} catch (err) {
			// Handle fetch errors
			error = `Error: ${err.message}`;
		}
	};

	onMount(() => {
		// Get the current URL path
		const urlPath = window.location.pathname;
		// Split the URL path by slashes ('/') to get an array of segments
		const urlSegments = urlPath.split('/');
		// Get the last segment of the URL
		lastSegment = urlSegments[urlSegments.length - 1];

		getProjectData(lastSegment);
	});
</script>

{#if activeProject}
	<h2>{lastSegment}</h2>
	<p>{activeProject.content}</p>
{:else if error}
	<section id="error">
		<p>Oops! {lastSegment} bestaat niet helaas</p>
		<a class="primary-button" href="/">Ik breng je terug naar home</a>
	</section>
{:else}
	<p>Project data aan het laden...</p>
{/if}


<style>
    section#error {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        height: 100vh;
    }
</style>
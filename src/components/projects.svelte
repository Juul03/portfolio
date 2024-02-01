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
	<h2>Mijn werk</h2>

	<section>
		<!-- For each -->
		{#if myProjectsData}
			{#each myProjectsData as project}
				<section>
					<h3>{project.project_name}</h3>
					<div>
						<h4>{project.project_tags}</h4>
						<img src="/img/icons/group-project.svg" alt="group project icon" />
					</div>

					<p>{project.project_description_short}</p>

					<ul>
						<li>Skills: {project.used_skills}</li>
						<li>
							Opdrachtgever: {project.client_name}
							{#if project.client_job_function !== ''}
								{project.client_job_function}
							{/if}

							{#if project.non_fiction_client == 'Y'}
								(non-fictief)
							{:else}
								(fictief)
							{/if}
						</li>
					</ul>

                    <!-- TODO: add link in json file and import here -->
                    <a href="/">Lees meer</a>

                    <img src={project.project_image_src} alt="">
				</section>
			{/each}
		{:else}
			<p>Sorry, er ging iets mis met het fetchen van mijn projecten. Laat het mij weten!</p>
		{/if}
	</section>
</section>

<style>
    img {
        max-width:40%;
    }
</style>

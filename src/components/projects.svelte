<script>
	import { onMount } from 'svelte';

	let myProjectsData = [
		{
			project_name: '',
			project_tags: [],
			project_type: '',
			project_duration: '',
			project_intensity: '',
			project_date_start: '',
			prrject_data_end: '',
			project_description_short: '',
			project_description_long: '',
			project_image_src: '',
			used_skills: [],
			client_name: '',
			client_job_function: '',
			non_fiction_client: ''
		}
	];

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

<section id="projects">
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

					<img src={project.project_image_src} alt="" />
				</section>
			{/each}
		{:else}
			<p>Sorry, er ging iets mis met het fetchen van mijn projecten. Laat het mij weten!</p>
		{/if}
	</section>
</section>

<style lang="scss">
	section {
		h2 {
			padding-left: var(--standard-padding-section);
		}

		> section > section {
			padding: var(--standard-padding-section);
		}
		> section > section:nth-of-type(odd) {
			background-color: rgba(var(--primary-color-rgb), var(--background-alpha));
		}

		> section > section:nth-of-type(even) {
			background: var(--secundary-color);
		}
	}
	img {
		max-width: 40%;
	}
</style>

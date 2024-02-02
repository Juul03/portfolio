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

	onMount(async () => {
		fetchData();
	});
</script>

<section id="projects">
	<h2>Mijn werk</h2>

	<section>
		<!-- For each -->
		{#if myProjectsData}
			{#each myProjectsData as project}
				<section>
					<div>
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
						<a class="primary-button" href="/">Lees meer</a>
					</div>

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
			font-size: var(--heading-1-font-size);
		}

		> section > section {
			padding: var(--standard-padding-section);
            display: flex;
		    justify-content: space-between;

			> div {
				display: flex;
				flex-direction: column;
                width: 50%;

				h3 {
					font-size: var(--heading-2-font-size);
				}

				> div:nth-of-type(1) {
					order: -1;

					display: flex;
					align-items: center; /* Align items vertically */
					gap: 1rem; /* Adjust the gap between h4 and img as needed */

					img {
						height: 2rem;
						width: auto;
						order: -1;
					}

					h4 {
						font-size: var(--heading-3-font-size);
						margin: 0; /* Remove default margin */
					}
				}

				ul li {
					color: var(--primary-color);
				}

                a {
                    width:max-content;
                }
			}

		}
		> section > section:nth-of-type(odd) {
			background-color: rgba(var(--primary-color-rgb), var(--background-alpha));

            > img {
				width: 40%;
                height:25rem;
                object-fit: cover;
			}
		}

		> section > section:nth-of-type(even) {
			background: var(--secundary-color);

            > img {
                width: 40%;
                height:25rem;
                background:red;
                object-fit: cover;
                order:-1;
            }
		}
	}
</style>

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
	<header>
		<div>
			<h2>{activeProject.project_name}</h2>
			<h3>
				{#if activeProject.project_type == 'group'}
					{activeProject.project_tags}
                    <img src="/img/icons/group-project.svg" alt="group project" />
				{/if}
			</h3>
			<p>{activeProject.project_header_descr}</p>

			<div>
				<a class="secundary-button" href={activeProject.github_link}>
					<img src="/img/icons/github.svg" alt="github" />
					Bekijk de code op Github</a
				>
				<a class="primary-button" href={activeProject.live_link}>Bekijk de Brassitol live</a>
			</div>
		</div>

		<img src={activeProject.project_image_src} alt="Dit ben ik! Julia" />
	</header>

    <main>
        <section>
            <h2>De opdracht</h2>
            <p>{activeProject.project_brief}</p>
        </section>
    </main>

{:else if error}
	<section id="error">
		<p>Oops! {lastSegment} bestaat niet helaas</p>
		<a class="primary-button" href="/">Ik breng je terug naar home</a>
	</section>
{:else}
	<p>Project data aan het laden...</p>
{/if}

<style lang="scss">
	section#error {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		height: 100vh;
	}

	header {
		background-color: rgba(var(--primary-color-rgb), var(--background-alpha));
		padding: var(--standard-padding-section) 0 var(--standard-padding-section);

		display: flex;
		justify-content: space-around;

		div {
			max-width: 50%;
			display: flex;
			flex-direction: column;

			h3 {
				order: -1;

                display:flex;
                gap:1rem;

                img {
                    order: -1;
                }
			}

			div {
				display: flex;
				flex-direction: row;
				width: 100%;

				gap: 1.4rem;
			}
		}

		img {
			max-width: 30%;
			// order: -1;
		}
	}

	a > img {
		/* TODO: nog aanpassen, alleen voor het gemak even gedaan */
		width: 1.5rem;
	}
</style>

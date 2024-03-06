<script>
	import { page } from '$app/stores';
	import { onMount } from 'svelte';

	import Header from '../../../components/header.svelte';
	import Footer from '../../../components/footer.svelte';

	let activeProjectName;
	let activeProjectData;
	let error = null;

	let getProjectData = async (project) => {
		try {
			const response = await fetch(`/data/${project}.json`);
			if (!response.ok) {
				throw new Error(`Failed to fetch data for ${project}.`);
			}
			const data = await response.json();
			console.log('dataaaa of the project', data);
			activeProjectData = data[0];
		} catch (err) {
			// Handle fetch errors
			error = `Error: ${err.message}`;
		}
	};

	onMount(() => {
		// Subscribe to changes in the page store
		const unsubscribe = page.subscribe(($page) => {
			// Access the route parameters
			activeProjectName = $page.params.projectId;

			getProjectData(activeProjectName);

			// Log the projectID
			console.log('Project ID:', activeProjectName);
		});

		return unsubscribe();
	});
</script>

<Header/>

{#if activeProjectName && activeProjectData}
	<header>
		<div>
			<h2>{activeProjectData.project_name}</h2>
			<h3>
				{#if activeProjectData.project_type == 'group'}
					{activeProjectData.project_tags}
					<img src="/img/icons/group-project.svg" alt="group project" />
				{/if}
			</h3>
			<p>{activeProjectData.project_header_descr}</p>

			{#if activeProjectData.github_link !== '' || activeProjectData.live_link !== ''}
				<div>
					<a class="secundary-button" href={activeProjectData.github_link}>
						<img src="/img/icons/github.svg" alt="github" />
						Bekijk de code op Github</a
					>
					<a class="primary-button" href={activeProjectData.live_link}>Bekijk de Brassitol live</a>
				</div>
			{/if}
		</div>

		<img src={activeProjectData.project_image_src} alt="projectafbeelding" />
	</header>

	<main>
		<section>
			<h2>De opdracht</h2>
			<p>{activeProjectData.project_brief}</p>
		</section>

		{#if activeProjectData.proces}
			<section id="proces">
				<h2>Het proces en ontwerpkeuzes</h2>
				{#each activeProjectData.proces as procesPart}
					<section>
						<h3>{procesPart.title}</h3>
						<p>{procesPart.text}</p>
						<img src={procesPart.img} alt="proces afbeelding" />
					</section>
				{/each}
			</section>
		{/if}
	</main>
{:else if error}
	<section id="error">
		<p>Oops! {activeProjectName} bestaat niet helaas</p>
		<a class="primary-button" href="/">Ik breng je terug naar home</a>
	</section>
{:else}
	<p>Project data aan het laden...</p>
{/if}

<Footer/>

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

				display: flex;
				gap: 1rem;

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

	#proces {
		section {
			display: flex;
            flex-direction:column;
            align-items: center;

			// flex-wrap: wrap;
			// justify-content: space-between;
			padding: var(--standard-padding-section);

			// h3 {
			// 	width: calc(100% / 3 * 2);
			// }

			// p {
			// 	width: calc(100% / 3 * 2);
			// }
            // TODO: OM DE IMG EEN FIGURE ZETTEN, DIE DE AFMETINGEN VAN EEN LAPTOP GEVEN en dan overflow-y scroll erp
			img {
				// height: 80vh;
                width:50%;
			}
		}
		section:nth-of-type(even) {
			background: rgba(var(--primary-color-rgb), var(--background-alpha));
		}
	}

	a > img {
		/* TODO: nog aanpassen, alleen voor het gemak even gedaan */
		width: 1.5rem;
	}
</style>

<script>
	import { page } from '$app/stores';
	import { onMount } from 'svelte';

	import Header from '../../../components/header.svelte';
	import Footer from '../../../components/footer.svelte';
	import Quotes from '../../../components/quotes.svelte';
	import MagazineLayout from '../../../components/magazine/magazine-pdf.svelte';
	import BackToTop from '../../../components/back-to-top.svelte';

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
				{#if activeProjectData.project_type == 'solo'}
					{activeProjectData.project_tags}
					<img src="/img/icons/individual-project.svg" alt="solo project">
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
				{#if activeProjectData.project_Id != "sav"}
				<h2>Het proces en ontwerpkeuzes</h2>
				{:else}
				<h2>Werkzaamheden</h2>
				{/if} 
				{#each activeProjectData.proces as procesPart}
					<section>
						<h3>{procesPart.title}</h3>
						<p>{procesPart.text}</p>

						{#if activeProjectData.project_medium == "website"}
						<figure class="desktop-mock-up">
							<div>
								<img src={procesPart.img} alt="proces afbeelding" />
							</div>
						</figure>
						{:else}
						<figure class="non-desktop">
							<div>
								{#each procesPart.img as procesImage}
								<img src={procesImage} alt="proces afbeelding" />
								{/each}
							</div>
						</figure>
						{/if}
						{#if procesPart.buttonLink}
						<a class="primary-button" href={procesPart.buttonLink}>
							{procesPart.buttonLinkText}
						</a>
						{/if}
					</section>
				{/each}
			</section>
		{/if}

		<Quotes/>

		{#if activeProjectData.project_tags.includes("ux-design")}
		<section id="more_projects">
			<h2>Nog trek in een toetje? Bekijk dit design!</h2>
			<ul>
				<li>
					<figure class="desktop-mock-up">
						<div>
							<img src="/img/projects/nailARt/nailArt-landing-page.png" alt="nailARt">
						</div>
					</figure>
				</li>
			</ul>
		</section>
		{/if}

		<BackToTop/>
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
					height:80%;
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
			height:auto;
			object-fit:cover;
		}
	}

	main > section:nth-of-type(1) {
		padding:var(--standard-padding-section);
	}

	#more_projects {
		padding-top:var(--standard-padding-section);
		h2{
			text-align:center;
		}
	}

	#proces {
		h2 {
			padding-left:var(--standard-padding-section);

		}
		section {
			display: flex;
            flex-direction:column;
            align-items: center;

			// flex-wrap: wrap;
			// justify-content: space-between;
			padding: var(--standard-padding-section);

			p {
				margin-bottom:var(--standard-padding-between-text);
			}
            

		}
		section:nth-of-type(even) {
			background: rgba(var(--primary-color-rgb), var(--background-alpha));
		}
	}

	figure.desktop-mock-up {
				margin:auto;
				width:38rem;
				height:32rem;
				background-image: url('/img/projects/desktop.png');
				background-size:cover;
				background-repeat:no-repeat;
				background-position: center;

				display:flex;

				div {
					width:95%;
					height:63%;
					margin:1.5rem auto;
					overflow-y: scroll;

					border-radius:.2rem;

					img {
						width:100%;
					}
				}
			}
	
	figure.non-desktop > div {
		display:flex;
		flex-direction:row;
		justify-content: space-evenly;
		flex-wrap:wrap;
		gap:1rem;
		width:75%;
		margin:auto;

		img {
			width:45%;
			height:auto;
		}
	}

			
	a > img {
		/* TODO: nog aanpassen, alleen voor het gemak even gedaan */
		width: 1.5rem;
	}

</style>

<script>
	import { dev } from '$app/environment';
	import { inject } from '@vercel/analytics';

	import Header from '../components/header.svelte';
	import Usps from '../components/usps/usps.svelte';
	import Projects from '../components/projects.svelte';
	import Footer from '../components/footer.svelte';
	import BackToTop from '../components/back-to-top.svelte';

	inject({ mode: dev ? 'development' : 'production' });
</script>

<Header />

<header>
	<div>
		<h1>Hey, ik ben Julia</h1>
		<h2>(Web)designer - frontend developer</h2>
		<p>
			Derdejaars Communicatie en Multimedia Design (CMD) student aan de HvA, die houdt van van de
			kracht en schoonheid van UX/UI design in combinatie met de uitdaging van het developen.
		</p>
		<div>
			<a class="secundary-button" href="/over-mij">Over mij</a>
			<a class="primary-button" href="#projects">Mijn werk</a>
		</div>
	</div>

	<img src="/img/people/me.svg" alt="Dit ben ik! Julia" />
</header>

<main>
	<Usps />

	<Projects />

	<BackToTop/>
</main>

<Footer />

<style lang="scss">
	header {
		background-color: rgba(var(--primary-color-rgb), var(--background-alpha));
		padding: var(--standard-padding-section) 0 var(--standard-padding-section);

		display: flex;
		justify-content: space-around;

		div {
			max-width: 50%;
			display: flex;
			flex-direction: column;

			h2 {
				order: -1;
			}

			div {
                display:flex;
                flex-direction:row;
                width:100%;

                gap:1.4rem;
            }
		}

		img {
			max-width: 30%;
			order: -1;
		}
	}
</style>

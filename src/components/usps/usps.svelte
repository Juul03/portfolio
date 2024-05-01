<script>
	import VisualThinker from './visual-thinker.svelte';
	import ZelfstandigeTeamplayer from './zelfstandige-teamplayer.svelte';
	import NieuwsgierigLeergierig from './nieuwsgierig-leergierig.svelte';
	import Verantwoordelijk from './verantwoordelijk.svelte';
	import Georganiseerd from './georganiseerd.svelte';
</script>

<section>
	<VisualThinker />
	<ZelfstandigeTeamplayer />
	<NieuwsgierigLeergierig />
	<Verantwoordelijk />
	<Georganiseerd />

	<img src="/img/icons/usp-icons.svg" alt="usp icons" />
</section>

<style lang="scss">
	section {
		padding: var(--standard-padding-section);
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		grid-template-rows: repeat(2, 1fr);
		gap: 4.3rem;

		img {
			grid-column: 2; 
            grid-row:2;
			justify-self: center;
			align-self: center;
            width:100%;
		}
	}
</style>

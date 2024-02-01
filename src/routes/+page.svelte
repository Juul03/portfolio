<script>
    import Header from '../components/header.svelte';
    import Usps from '../components/usps/usps.svelte';
    import Projects from '../components/projects.svelte';
    import Footer from '../components/footer.svelte';
</script>

<Header/>

<header>
    <h1>Hey, ik ben Julia</h1>
    <h2>(Web)designer - frontend developer</h2>
    <p>
        Derdejaars Communicatie en Multimedia Design (CMD) student aan de HvA, die houdt van van de kracht
        en schoonheid van UX/UI design in combinatie met de uitdaging van het developen.
    </p>
    <a href="/over-mij">Over mij</a>
    <a href="/">Mijn werk</a>

    <img src="/img/people/me.svg" alt="Dit ben ik! Julia">
</header>

<main>

    <Usps/>

    <Projects/>

</main>

<Footer/>

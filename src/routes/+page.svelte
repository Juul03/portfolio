<script>
    import Header from '../components/header.svelte';
    import Usps from '../components/usps/usps.svelte';
    import Projects from '../components/projects.svelte';
    import Footer from '../components/footer.svelte';
</script>

<Header/>

<header>
    <div>
        <h1>Hey, ik ben Julia</h1>
        <h2>(Web)designer - frontend developer</h2>
        <p>
            Derdejaars Communicatie en Multimedia Design (CMD) student aan de HvA, die houdt van van de kracht
            en schoonheid van UX/UI design in combinatie met de uitdaging van het developen.
        </p>
        <a class="secundary-button" href="/over-mij">Over mij</a>
        <a class="primary-button" href="/">Mijn werk</a>
    </div>
    
    <img src="/img/people/me.svg" alt="Dit ben ik! Julia">
</header>

<main>

    <Usps/>

    <Projects/>

</main>

<Footer/>

<style lang="scss">
    header {
        background-color: rgba(var(--primary-color-rgb), var(--background-alpha));
        padding:var(--standard-padding-section) 0 var(--standard-padding-section);

        display:flex;
        justify-content:space-around;

        div {
            max-width:50%;

            p {
                margin-bottom:3rem;
            }

            a {

            }
        }

        img {
            max-width:30%;
            order:-1;
        }

    }
</style>

<script>
	import Header from '../../components/header.svelte';
	import Footer from '../../components/footer.svelte';
    import Quotes from '../../components/quotes.svelte';
    import SkillLevel1 from '../../components/skill-level/skill-level1.svelte';
    import SkillLevel2 from '../../components/skill-level/skill-level2.svelte';
    import SkillLevel3 from '../../components/skill-level/skill-level3.svelte';
    import SkillLevel4 from '../../components/skill-level/skill-level4.svelte';
    import SkillLevel5 from '../../components/skill-level/skill-level5.svelte';

    import BackToTop from '../../components/back-to-top.svelte';
</script>

<Header />

<main>
    <section id="over-mij">
        <div>
            <h1>Over mij</h1>
            <h2>(Web)designer - frontend developer</h2>
            <p>
                Hey, ik ben Julia, 21 jarige derdejaars Communicatie en Multimedia Design (CMD) student aan de HvA, die houdt van van de
                kracht en schoonheid van UX/UI design in combinatie met de uitdaging van het developen. Daarom ben ik ook opzoek naar een
                leuke stage die een combinatie van beide biedt!
            </p>
            <p>
                Zelf ben ik een creatieve denker die graag haar ideeën op papier zet met ondersteundende tekeningen. Ik werk georganisseerd en hoor
                van anderen terug dat ze mijn time- en taskmanagment waarderen. Door deze manier van werken heb ik vaak tijd om anderen die het nodig
                hebben te helpen. Soms zet ik daardoor mijn eigen ontwikkeling wat op pauze, echter zou ik nu graag zelf dezelfde ondersteuning ontvangen
                om mijn professionele ontwikkeling naar een hoger niveau te tillen.
            </p>
            <p>
                De onderwerpen waarin ik me nog verder wil ontwikkelen, zowel op het gebied van development als design, zijn responsive webdesign. Hierbij 
                heb ik al wel een basis gelegd met mediaqueries, flexbox en grid. Daarnaast heb ik ook wat ervaring met mobile-first design, wat ik graag zou 
                willen uitbreiden. Op het gebied van webdesign, specifiek in UX-principes, wil ik mijn kennis vergroten om websites nog beter te laten 
                aansluiten bij de opdrachtgever en doelgroep.
            </p>
            <p>
                Tot slot wil ik benadrukken dat ik een creatieve student ben die op zoek is naar een gevarieerde en uitdagende stage in de creatieve sector. 
                Ben jij, of ken jij, een bedrijf dat niet alleen gespecialiseerd is in webdesign, maar ook een breed scala aan opdrachten aanbiedt? Neem 
                dan vooral contact op! 
            </p>
        </div>
    </section>
    
    <section id="skills">
        <div>
            <h2>Skills</h2>
            <section>
                <h3>Hardskills</h3>
                <section>
                    <h4>Tech</h4>
                    <ul class="listed">
                        <li>HTML
                            <SkillLevel4/>
                        </li>
                        <li>CSS
                            <SkillLevel4/>
                        </li>
                        <li>Javascript
                            <SkillLevel4/>
                        </li>
                        <li>Scss
                            <SkillLevel4/>
                        </li>
                        <li>Sveltekit
                            <SkillLevel2/>
                        </li>
                        <li>D3.js
                            <SkillLevel3/>
                        </li>
                        <li>Git(Hub)
                            <SkillLevel3/>
                        </li>
                    </ul>
                </section>
                <section>
                    <h4>Design</h4>
                    <ul class="listed">
                        <li>Adobe Indesign
                            <SkillLevel4/>
                        </li>
                        <li>Adobe XD/ Figma
                            <SkillLevel4/>
                        </li>
                        <li>Adobe Illustrator
                            <SkillLevel3/>
                        </li>
                        <li>Adobe Photoshop
                            <SkillLevel1/>
                        </li>
                        <li>UX-werk & onderzoeksmethoden
                        </li>
                    </ul>
                </section>
            </section>
            <section>
                <h3>Softskills</h3>
                <ul class="listed">
                    <li>Leergierig</li>
                    <li>Kritisch</li>
                    <li>Proactief</li>
                    <li>Behulpzaam</li>
                    <li>Zelfstandige teamplayer</li>
                    <li>Visual Thinker</li>
                </ul>
            </section>
        
            <section>
                <h3>Overig</h3>
                <ul class="listed">
                    <li>Nederlands (moedertaal)</li>
                    <li>Engels (afgerond niveau C1)</li>
                </ul>
            </section>
        </div>
    </section>

    <BackToTop/>
</main>

<Quotes/>

<Footer/>

<style lang="scss">
    main {
        display:flex;
        justify-content: center;

        > section:first-of-type#over-mij {
            flex-grow:3;
            width:75%;
            
            display:flex;
            flex-direction: column;
            align-items:flex-start;

            padding:var(--standard-padding-section) 0;

            h1, h2 {
                text-align:left;
            }

            p {
                padding: 1rem 0;
            }

            div {
                width:80%;
                margin:.5rem auto;
            }
        }

        > section:last-of-type#skills {
            flex-grow:1;
            width:25%;
            order:-1;

            background-color: rgba(var(--primary-color-rgb), var(--background-alpha));
            padding:2rem;

            display:flex;
            flex-direction:column;

            div {
                margin:auto;
                width:80%;
                > section {
                margin: var(--standard-padding-between-text) 0;

                > section {
                    margin: 1rem 0;

                    ul li {
                        display:flex;
                        flex-wrap:wrap;
                        gap:.5rem;
                        align-items:center;
                        justify-content: space-between;     
                    }

                }
            }

            }
        }
    }
</style>


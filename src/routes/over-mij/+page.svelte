<script>
	import Header from '../../components/header.svelte';
	import Footer from '../../components/footer.svelte';
    import Quotes from '../../components/quotes.svelte';
    import SkillLevel1 from '../../components/skill-level/skill-level1.svelte';
    import SkillLevel2 from '../../components/skill-level/skill-level2.svelte';
    import SkillLevel3 from '../../components/skill-level/skill-level3.svelte';
    import SkillLevel4 from '../../components/skill-level/skill-level4.svelte';
    import SkillLevel5 from '../../components/skill-level/skill-level5.svelte';
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
                iets over soft en hardskills, wat anderen over mij zeggen
                Ik help altijd anderen en ben nu zelf aan de beurt om dingen te leren
            </p>
            <p>leerdoelen (responsive webdesign, al wel wat mee gedaan met mediaqueries en flexbox, en mobile first design) en aflsuitng</p>
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
                    <li>Behulpzaam</li>
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


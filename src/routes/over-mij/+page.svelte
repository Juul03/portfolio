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
                        <li>Scss</li>
                        <li>Sveltekit</li>
                        <li>D3.js</li>
                    </ul>
                </section>
                <section>
                    <h4>Design</h4>
                    <ul class="listed">
                        <li></li>
                        <li>UX-werk & onderzoeksmethoden</li>
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

<style lang="scss">
    main {
        display:flex;
        justify-content: center;
        // flex-wrap:wrap;

        > section:first-of-type#over-mij {
            flex-grow:4;
            width:80%;
            
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
            width:20%;
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

                }
            }

            }
        }
    }
</style>


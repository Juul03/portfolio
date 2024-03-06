<section>
	<div class="h2-container">
		<h2>Quotes uit de korte stage van stagebegeleider en collega's (april 2023)</h2>

        <button>Nieuwe quote!</button>
	</div>

	<div>
		<figure>
			<img src="/img/quotes/Pelle/rechts/kritisch.svg" alt="" />
            <figcaption>Pelle Borst - UX designer bij SenS online solutions</figcaption>
		</figure>

		<figure>
			<img src="/img/quotes/Pelle/pelle.svg" alt="" />
		</figure>
	</div>
</section>

<style lang="scss">
	section {
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;

    border: black solid 2px;

    .h2-container {
        flex: 1;
        display: flex;
        align-items: center;
        flex-wrap:wrap;
        background: rgba(var(--primary-color-rgb), var(--background-alpha));

        h2 {
            width: 75%; /* Make the h2 take up 75% of its container */
        }

        button {
            background: var(--primary-color);
            color: var(--secundary-color);
            padding: 1rem 3rem;
            border-radius: var(--standard-border-radius-button);
            border: 2px solid transparent;

            transition: var(--standard-transition-time);
        }

        button:hover {
            background:var(--secundary-color);
            color:var(--primary-color);
            border:2px solid var(--primary-color);
        }
    }

    > div {
        flex: 1;
        display: flex;
        padding: 2.5rem;
        background: var(--secundary-color);

        figure {
            display: flex;
            align-items: center;
            justify-content: center;
            flex-wrap: wrap;

            figcaption {
                color: var(--primary-color);
            }
        }

        figure:first-of-type {
            flex: 3;

            img {
                height:65%;
                padding: 1rem; 
            }
        }

        figure:last-of-type {
            flex: 1;

            img {
                height:40%;
                margin: 0.5rem;
            }
        }
    }
}


	// ul {
	//     display:flex;
	//     flex-wrap:wrap;

	//     li:nth-of-type(odd) {
	//         background:rgba(var(--primary-color-rgb), var(--background-alpha));

	//         display:flex;

	//         figure:first-of-type {
	//             order:1;
	//         }

	//     }

	//     li:nth-of-type(even) {
	//         figure:last-of-type img {
	//             transform:scaleX(-1);
	//         }
	//     }

	//     li {
	//         width:50%;
	//         padding:4.5rem 0;

	//         display:flex;
	//         justify-content: space-evenly;

	//         h2 {
	//             width:75%
	//         }

	//         figure {
	//             display:flex;
	//             align-items: center;
	//             justify-content: center;
	//         }

	//         figure:first-of-type {
	//             width:65%;

	//             img {
	//                 width:75%;
	//             }
	//         }

	//         figure:last-of-type {
	//             width:25%;

	//             img {
	//                 width:75%;
	//             }
	//         }
	//     }
	// }
</style>

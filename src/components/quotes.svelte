<section id="quote">
	<div class="h2-container">
		<h2>Quotes uit de korte stage van stagebegeleider en collega's (april 2023)</h2>

		<!-- <button id="newQuoteButton">Nieuwe quote!</button> -->
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
	section#quote {
		width: 100%;
		display: flex;
		flex-wrap: wrap;
		justify-content: center;

		border: black solid 2px;

		.h2-container {
			flex: 1;
			display: flex;
			flex-direction: column;
			justify-content: space-evenly;
			// align-items: center;
			// flex-wrap:wrap;
			background: rgba(var(--primary-color-rgb), var(--background-alpha));

			h2 {
				width: 75%; /* Make the h2 take up 75% of its container */
			}

			button {
				width: max-content;
				background: var(--primary-color);
				color: var(--secundary-color);
				padding: 1rem 3rem;
				border-radius: var(--standard-border-radius-button);
				border: 2px solid transparent;

				transition: var(--standard-transition-time);
			}

			button:hover {
				background: var(--secundary-color);
				color: var(--primary-color);
				border: 2px solid var(--primary-color);
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
					height: 65%;
					padding: 1rem;
				}
			}

			figure:last-of-type {
				flex: 1;
				transform: scaleX(-1);

				img {
					height: 40%;
					margin: 0.5rem;
				}
			}
		}
	}
</style>

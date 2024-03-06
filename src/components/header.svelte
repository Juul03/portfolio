<!-- TODO: link the a elements to the right element on the page voor #mijn werk en # contact -->
<header>
	<nav>
		<ul>
			<li>
				<a href="/"><img src="/favicon.svg" alt="Home" /></a>
			</li>
			<li>
				<a href="#projects">Mijn werk</a>
			</li>
			<li>
				<a href="/over-mij">Over mij</a>
			</li>
			<li>
				<a href="#contact">Contact</a>
			</li>
		</ul>
	</nav>
</header>

<style lang="scss">
	header {
		width: 100%;
		background: var(--secundary-color);

		nav {
			width: 100%;

			ul {
				display: flex;
				flex-direction: row;
				align-items: center;

				li:first-child {
					flex-grow: 9;

					a img {
						transition:var(--standard-transition-time);
					}
					
				}

				li:first-child:hover a img {
					transform:translateX(.25rem) scale(1.2);
				}

				li:not(:first-child) {
					flex-grow: .5;
					text-align:center;
					text-decoration: underline var(--secundary-color);
					text-underline-offset: .5rem;
					text-decoration-thickness: .2rem;
					
					transition: var(--standard-transition-time);
				}

				li:not(:first-child):hover {
					text-decoration: underline var(--primary-color);
					text-underline-offset: 1rem;
					text-decoration-thickness: .2rem;
					transform:scale(1.1) translateY(-.3rem);

				}

                li > a {
                    color:var(--primary-color);
                }
			}
		}
	}
</style>

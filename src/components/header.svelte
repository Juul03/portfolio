<!-- TODO: link the a elements to the right element on the page voor #mijn werk en # contact -->
<header>
	<nav>
		<ul>
			<li>
				<a href="/"><img src="/favicon.svg" alt="Home" /></a>
			</li>
			<li>
				<a href="/">Mijn werk</a>
			</li>
			<li>
				<a href="/over-mij">Over mij</a>
			</li>
			<li>
				<a href="/">Contact</a>
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
				}

				li:not(:first-child) {
					flex-grow: .5;
				}

                li > a {
                    color:var(--primary-color);
                }
			}
		}
	}
</style>

<footer>
	<h2>Neem contact op!</h2>
	<h3>Tot hier gekomen? Interesse of vragen?</h3>
	<ul>
		<li>
			<!-- TODO: check if address tag is used correctly -->
			<address>
				<a href="mailto:julia.hoek@hva.nl">
					julia.hoek@hva.nl
					<img src="/img/icons/mail.svg" alt="mail icon" />
				</a>
			</address>
		</li>
		<li>
			<a href="https://www.linkedin.com/in/julia-hoek-89ba2125a/">
				Julia Hoek
				<img src="/img/icons/linkedin.svg" alt="linkedin icon" />
			</a>
		</li>
		<li>
			<a href="https://github.com/Juul03">
				Juul03
				<img src="/img/icons/github.svg" alt="github icon" />
			</a>
		</li>
	</ul>
</footer>

<style lang="scss">
	footer {
		display: flex;
		justify-content: center;
		flex-wrap: wrap;

        padding: var(--standard-padding-section) 0 var(--standard-padding-section);

		h2,
		h3 {
			width: 100%;
			text-align: center;
		}

        h3 {
            order:-1;
        }

		ul {
            display:flex;
            flex-direction:column;
            gap:2rem;
			li {
				display: flex;
				flex-direction: row;
                justify-content: left;

				a {
					display: flex;
                    align-items:center;
                    gap:1rem;
					img {
						order: -1;
                        max-width:7.5rem;
					}
				}
			}
		}
	}
</style>

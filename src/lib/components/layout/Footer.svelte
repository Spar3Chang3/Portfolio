<script lang="js">
	import { SocialLinks, IconLinks } from '$lib/index.js';

	let { prefersDarkMode = false } = $props();
	let githubLogo = $derived((prefersDarkMode ? IconLinks.github.dark : IconLinks.github.light));
	let emailIcon = $derived((prefersDarkMode ? IconLinks.email.dark : IconLinks.email.light));

</script>

<style lang="css">

    .footer {
        display: grid;
        grid-template-columns: 66% 34%;
        grid-template-rows: 1fr;
        min-height: 50px;
        max-height: 10vh;
        width: 100vw;

        background-color: var(--background-secondary);
        font-family: Hacked, sans-serif;
        border-top: 0.1vh solid var(--banner-accent);
    }

	.copyright {
			display: flex;
			flex-direction: column;
      min-height: 50px;
			max-height: 10vh;

			justify-content: center;
			align-items: flex-start;
			text-align: center;

			font-size: 1rem;
			color: grey;
			padding-left: 1rem;
	}
	.copyright a {
			text-decoration: none;
			color: var(--hyperlink);
	}

	.social-shelf {
			display: grid;
			grid-template-columns: 1fr 1fr 1fr;
			grid-template-rows: 1fr;
			height: 10vh;
      min-height: 50px;
			width: 100%;

			justify-content: center;
			justify-items: center;
			align-items: center;
	}

	.social-shelf a {
			height: 6vh;
			width: 6vh;
			max-height: 4rem;
			max-width: 4rem;
	}

	.social-shelf a > img {
			height: 100%;
			width: 100%;
			object-fit: contain;
			transition: 250ms ease;
	}

	.social-shelf a > img:hover {
			transform: scale(1.1);
	}

	@media only screen and (max-width: 768px) {
			.footer {
					grid-template-columns: 1fr;
					grid-template-rows: 1fr 1fr;

					max-height: fit-content;

					justify-items: center;
			}

			.copyright {
					width: 100%;
					align-items: center;
					padding: 0;
			}

			.social-shelf {
					width: 100%;
					justify-items: center;
			}

	}

</style>

<section class="footer">
	<div class="copyright">
		<p>© 2025 Daryk Baker - All Rights Thought About <br> This site is available for viewing at <a href={SocialLinks.websiteGit} target="_blank">GitHub.com</a></p>
	</div>
	<div class="social-shelf">

		<a href={SocialLinks.github} target="_blank">
			<img src={githubLogo} alt="Github Logo"/>
		</a>

		<a href={SocialLinks.linkedIn} target="_blank">
			<img src={IconLinks.linkedIn} alt="LinkedIn Logo"/>
		</a>

		<a href="mailto:darykdbaker@gmail.com" target="_blank">
			<img src={emailIcon} alt="Email Icon"/>
		</a>
	</div>
</section>
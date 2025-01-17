<script lang="js">
    import { onMount } from 'svelte';

    onMount(() => {
        document.title = "Portfolio - Daryk Baker";
    });
</script>
<style lang="css">
    a {
        text-decoration: underline;
        color: var(--hyperlink);
    }

    hr {
        width: 95%;
        height: 0.25rem;

        border: none;
        background-color: var(--banner-accent);
        border-radius: 25px;
    }

    .portfolio {
        position: relative;
        display: flex;
        flex-direction: column;

        min-height: 79.8vh;
        width: 100vw;

        align-items: center;

        color: whitesmoke;
        font-family: Roboto, sans-serif;
    }

    .portfolio h1 {
        width: 100%;

        text-align: center;
        font-size: 4rem;
    }

    .preface {
        height: fit-content;
        width: 95%;

        padding: 1rem;
        text-align: justify-all;
        font-size: 1.2rem;
    }
    .silhouette-project, .unthynck-project, .orion-project {
        height: fit-content;
        width: 95%;

        padding: 1rem;
        text-align: justify-all;
        font-size: 1.2rem;
    }

    .project-viewer {
        border: none;
        height: 60vh;
        width: 100%;
    }

    @media only screen and (max-width: 768px) {
        .preface {
            text-align: justify-all;
            font-size: 1rem;
        }
    }

</style>
<section class="portfolio">
    <h1>Portfolio</h1>
    <div class="preface">
        <h2>
            I have worked on a number of projects throughout my development lifecycle. Of these projects, here are three notable ones:
        </h2>
    </div>

    <div class="silhouette-project">
        <h3>Silhouette.band</h3>
        <p>
            This project was my first ever website to be commissioned for. Built in React, it serves as a milestone for my first major developer accomplishment.
        </p>
        <p>
            Unfortunately, Silhouette the band has been broken up since 2023, and the website is no longer active. For viewing, all sourcecode is available on <a href="https://github.com/Spar3Chang3/Silhouette-Website" target="_blank">GitHub</a>
        </p>
    </div>

    <hr/>

    <div class="unthynck-project">
        <h3>Unthynck.band</h3>
        <p>
            This project is my latest website offering for the local Springfield band known as Unthynck. With a wacky name comes a wacky website, yet still with a modicum of professionalism.
        </p>
        <p>
            I am particularly proud of Unthynck.band because it features almost entirely server-fed data. This allows me to create a dashboard login for the members, where they can edit multiple data points through a convenient UI.
        </p>
        <p>
            I actively maintain this website to this day, which uses a frontend in Svelte with a backend in Firebase. The website can be located at <a href="https://Unthynck.band" target="_blank">Unthynck.band</a> and the sourcecode on <a href="https://github.com/Spar3Chang3/Unthynck" target="_blank">GitHub</a>
        </p>
        <iframe class="project-viewer" src="https://Unthynck.band" title="Unthynck"></iframe>
    </div>

    <hr/>

    <div class="orion-project">
        <h3>Orion Labs</h3>
        <p>
            This project is my current volunteer work for the Orion Lab at University of Illinois Springfield. I have developed it in tandem with Edward Anderson, a student with a passion for raw HTML. It took some convincing for him to work with the frontend framework I chose, which was once again Svelte. I find this framework to be incredibly easy to work with while staying efficient.
        </p>
        <p>
            The backend is my first forte into using Go with creation of my own in-house encryption procedure, which implements the <a href="https://en.wikipedia.org/wiki/Bcrypt" target="_blank">BCrypt standard</a>.
        </p>
        <p>
            The website is currently domain-less and will likely continue to be that way until UIS purchases the domain. However, as always the sourcecode is available on <a href="https://github.com/Spar3Chang3/Orion-Labs" target="_blank">GitHub</a>
        </p>
    </div>
</section>
<script lang="js">
    import { onMount } from 'svelte';
    import { IconLinks } from '$lib/index.js';

    onMount(() => {
        document.title = "About Me - Daryk Baker";
    });
</script>
<style lang="css">
    .about {
        position: relative;
        display: flex;
        flex-direction: column;

        min-height: 79.8vh;
        width: 100vw;

        align-items: center;

        color: whitesmoke;
        font-family: Roboto, sans-serif;
    }

    .about h1 {
        width: 100%;

        text-align: center;
        font-size: 4rem;
    }

    .summary, .education, .skills, .experience, .goals {
        height: fit-content;
        width: 95%;

        padding: 1rem;
        text-align: justify-all;
        font-size: 1.2rem;
    }

    .education, .skills {
        line-height: 2rem;
    }

    .experience img {
        min-height: 10vh;
        min-width: 10vh;

        max-height: 10rem;
        max-width: 10rem;

        object-fit: contain;
    }

    .languages, .frameworks {
        position: relative;
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;

        height: fit-content;
        width: 95%;

        align-items: center;
        justify-content: flex-start;
        gap: 1rem;

        padding: 1rem;
        border-radius: 25px;

        background-color: var(--banner-standard);
    }

    .languages h4, .frameworks h4 {
        width: 100%;
        height: fit-content;
    }

</style>
<section class="about">
    <h1>About Me</h1>
    <div class="summary">
        <h3>Summary</h3>
        <p>
            Ever since I was a kid, I'd dreamed of working with computers. Phones, websites, data parsing, they're all actually interesting to me.
        </p>
        <p>
            OK, so that sounds a little weird to think someone WANTS to handle a bunch of data. But someone's got to do it! I believe in making things that are accessible to all parties, inclusive to all.
        </p>
        <p>
            That's where web design comes in. The web is such a dynamic, ever-updating platform, which is what gives it infinite flexibility. Don't believe me? Think about all the entirely web-based apps out there. Discord, Spotify, even Uber!
        </p>
        <p>
            And that's where I come in. Web design offers a platform of complete freedom with UI design, packaged in languages that every modern browser can understand. This lets me build you only the most tailored experience, with every component automatically fitting to nearly every screen.
        </p>
        <p>
            For 2 years now, I have been developing full stack applications that emphasize a brand's language. I'm a quick learner that picks up on frameworks within the week. And for the backend? I've been programming with Java since high school. So I can work with ol' reliable, or go modern with my latest forte into GoLang.
        </p>
    </div>

    <div class="education">
        <h3>Education</h3>
        <ul>
            <li>High school graduate from Greenview High School in 2022</li>
            <li>2 years of Computer Science at Illinois College from 2022-2024</li>
            <li>1 Year of technical education at Lincoln Community High School from 2021-2022</li>
            <li>Current Lincoln Land Community College undergrad for Computer Science, starting in 2025</li>
        </ul>
    </div>

    <div class="skills">
        <h3>Skills</h3>
        <ul>
            <li>Professional experience in device repair including phones, servers, desktops, and more</li>
            <li>Proficiency in using corporate applications such as Microsoft Word, Excel, and the Google suite</li>
            <li>An aptitude for learning programming languages, in-house tools, and more</li>
            <li>The ability to cooperate efficiently and accurately with team members</li>
        </ul>
    </div>

    <div class="goals">
        <h3>Goals</h3>
        <p>
            I aspire to reach senior developer status through schooling, working, and self-fulfillment.
        </p>
        <p>
            To do this I try to learn at least one new thing each day. My intent is to be flexible and always open to new implementations.
        </p>
        <p>
            Whether I am placed by my self, with a team, or simply as a code reviewer, I will always work to both my own and my employer's satisfaction.
        </p>
    </div>

    <div class="experience">
        <h3>Experience</h3>
        <div class="languages">
            <h4>Languages</h4>
            <img src={IconLinks.html} alt="Logo of HTML 5"/>
            <img src={IconLinks.css} alt="Logo of CSS"/>
            <img src={IconLinks.js} alt="Logo of JavaScript"/>
            <img src={IconLinks.java} alt="Logo of Java"/>
            <img src={IconLinks.go} alt="Logo of GoLang"/>
        </div>
        <br/>
        <div class="frameworks">
            <h4>Frameworks</h4>
            <img src={IconLinks.react} alt="Logo of the React framework"/>
            <img src={IconLinks.svelte} alt="Logo of the Svelte Framework"/>
        </div>
    </div>
</section>
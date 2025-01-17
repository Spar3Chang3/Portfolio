<script lang="js">
    import { onMount } from 'svelte';
    import { SocialLinks, IconLinks } from '$lib/index.js';

    onMount(() => {
        document.title = "Contact - Daryk Baker";
    });
</script>
<style lang="css">
    a {
        text-decoration: underline;
        color: var(--hyperlink);
    }

    .contact {
        position: relative;
        display: flex;
        flex-direction: column;

        min-height: 79.8vh;
        width: 100vw;

        align-items: center;

        color: whitesmoke;
        font-family: Roboto, sans-serif;
    }

    .contact h1 {
        width: 100%;

        text-align: center;
        font-size: 4rem;
    }

    .preface{
        height: fit-content;
        width: 95%;

        padding: 1rem;
        text-align: justify-all;
        font-size: 1.2rem;
    }

    .icons {
        position: relative;
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;

        height: fit-content;
        width: 95%;

        align-items: center;
        justify-content: center;
        gap: 1rem;

        padding: 1rem;
        border-radius: 25px;

        background-color: var(--banner-standard);
    }

    .icons img {
        min-height: 10vh;
        min-width: 10vh;

        max-height: 10rem;
        max-width: 10rem;

        object-fit: contain;
        transition: 250ms ease;
    }

    .icons img:hover {
        transform: scale(1.1);
    }
</style>
<section class="contact">
    <h1>Contact</h1>
    <div class="preface">
        <p>
            There are multiple ways to contact me. Most notably, I respond to <a href="mailto:darykdbaker@gmail.com" target="_blank">Emails</a> the best. However, you may also find me at <a href={SocialLinks.linkedIn} target="_blank">LinkedIn</a>, <a href={SocialLinks.fb} target="_blank">Facebook</a>, or <a href={SocialLinks.discord} target="_blank">Discord</a>
        </p>
    </div>
    <div class="icons">
        <a href="mailto:darykdbaker@gmail.com" target="_blank">
            <img src={IconLinks.email.dark} alt="Email icon"/>
        </a>
        <a href={SocialLinks.linkedIn} target="_blank">
            <img src={IconLinks.linkedIn} alt="LinkedIn logo"/>
        </a>
        <a href={SocialLinks.fb} target="_blank">
            <img src={IconLinks.fb} alt="Facebook logo"/>
        </a>
        <a href={SocialLinks.discord} target="_blank">
            <img src={IconLinks.discord} alt="Discord logo"/>
        </a>
    </div>
</section>
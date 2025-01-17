<script lang="js">
    import { StatLinks, PictureLinks } from '$lib/index.js';
    import { onMount } from 'svelte';

    let observeElements = $state([
        {id: 0, isVisible: false},
        {id: 1, isVisible: false},
        {id: 2, isVisible: false},
    ]);
    let elementRefs = $state([null, null, null]);

    let opacityLevel = $state();
    let scrollY = $state();

    onMount(() => {

        document.title = "Home - Daryk Baker";

        const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    const targetIndex = observeElements.findIndex(
                        target => target.id === Number(entry.target.dataset.id)
                    );

                    if (targetIndex > -1) {
                        observeElements[targetIndex] = {
                            ...observeElements[targetIndex],
                            isVisible: entry.isIntersecting
                        }
                    }
                });
            },
            {
                root: null,
                rootMargin: '0px',
                threshold: 0.8
            }
        );

        Object.values(elementRefs).forEach((ref) => {
           if (ref) {
               observer.observe(ref);
           }
        });

        window.addEventListener('scroll', (e) => {
            scrollY = window.scrollY;
            opacityLevel = 1 - (Math.min(window.scrollY / window.innerHeight, 1));
        });

        return () => {
            Object.values(elementRefs).forEach(element => {
                if (element) {
                    observer.unobserve(element);
                }
            });

            observer.disconnect();
        }

    });

</script>

<style lang="css">
    .home {
        position: relative;
        display: flex;
        flex-direction: column;

        min-height: 79.8vh;
        max-width: 100%;

        color: whitesmoke;
        font-family: Roboto, sans-serif;
        overflow: hidden; /*is this needed?*/
        background-color: #da897a;

    }

    .intro-background-wrapper {
        position: absolute;
        top: -5vh;
        left: -5vw;
        height: 105vh;
        width: 110vw;
        z-index: 0;
        filter: blur(10px);
    }

    .background-video {
        width: 100%;
        height: 100%;
        object-fit: cover;
        position: absolute;
        top: 0;
        left: 0;
    }


    .name {
        /*#bisexual. Too much? Added this ↴ */
        filter: drop-shadow(.3rem .3rem 0 #D60270) drop-shadow(.2rem .2rem 0 #9B4F96) drop-shadow(.3rem .3rem 0 #0038A8);
        position: relative;
        display: flex;
        height: fit-content;
        width: 50%; /*I hate that this is here. Forces name to collapse when not needed, but lets it stay above image*/



        justify-content: center;
        align-items: center;
        text-align: center; /*fuck you, this looks way better*/

        font-size: 3.5rem;
        line-height: 3.5rem;
    }

    .intro {
        position: relative;
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-template-rows: auto;
        align-items: center;
        width: 100%;
        gap: 1rem;

        padding: 1rem;
    }

    .left-top {
        display: flex;
        justify-content: center;
        align-items: end;
    }

    .pfp {
        max-height: 60vh;
        max-width: 100%;
        object-fit: contain;
        border-radius: 10%;
    }

    .right-bottom {
        display: flex;
        justify-content: flex-start;
        align-items: end;
        height: 100%;
        font-size: 2rem;
        line-height: 2.2rem;
    }

    .right-bottom h3 {
        width: 95%;
        text-align: justify-all;
    }

    .interact-tip {
        position: absolute;

        top: 75vh;

        width: 100%;
        height: fit-content;

        font-size: 2.5rem;
    }

    .interact-tip h3 {
        animation: gesture 6s infinite ease;
        text-align: center;
    }

    .spacer {
        height: 40vh;
        width: 100vw;
    }

    .stats-background-wrapper {
        position: absolute;

        top: 100vh;
        left: -5vw;


        height: 200vh;
        width: 110vw;

        z-index: 0;

        filter: blur(10px) saturate(75%);
        background-color: #413a55;
        animation: colorFlow 8s infinite;
    }

    .stats-background-overlay {
        position: relative;

        height: 100%;
        width: 100%;

        background-image: url('/assets/fog1.png');
        background-repeat: repeat-y;
        background-size: 110% 100vh;

        animation: scrollBackground 6s linear infinite;
    }

    .stats {
        position: relative;
        display: flex;
        flex-direction: column;

        min-height: 80vh;
        width: 100%;

        justify-content: center;
        align-items: center;
    }

    .stats h3 {
        font-size: 3rem;
    }

    .stats-list {
        list-style: none;
    }

    .stats-list-item {
        transform: translateX(-50vw);
        opacity: 0;
        height: 4rem;
        font-size: 1.5rem;
        transition: all 0.8s ease;
    }

    .stats-list li:nth-child(2) {
        transition-delay: 0.2s;
    }

    .stats-list li:nth-child(3) {
        transition-delay: 0.4s;
    }

    small {
        font-size: 0.6rem;
    }

    small a {
        text-decoration: underline;
        color: var(--hyperlink);
    }

    .sell-myself {
        position: relative;
        display: flex;
        flex-direction: column;

        min-height: 80vh;
        width: 100%;

        justify-content: center;
        align-items: center;
        text-align: center;

        font-size: 2rem;
    }

    .sell-myself-p {
        transform: translateX(-50vw);
        opacity: 0;
        transition: all 0.8s ease;
    }

    .sell-myself-p:nth-child(2) {
        transition-delay: 1.5s;
    }

    .sell-myself b {
        animation: textFlow 8s linear infinite;
    }


    .visible {
        opacity: 1;
        transform: translateX(0);
    }

    .hidden {
        transition: all 0s;
        transition-delay: 0s;
    }

    .hidden:nth-child(2), .hidden:nth-child(3), .hidden:nth-child(4), .hidden:nth-child(5) {
        transition-delay: 0s;
    }

    @media only screen and (max-width: 768px) {
        .name {
            font-size: clamp(1.8rem, 2rem, 3rem);
            width: 100%;
            text-align: center;
        }

        .intro {
            grid-template-columns: auto;
            grid-template-rows: auto auto;
            padding: 0;
        }

        .pfp {
            max-height: 45vh;
        }

        .left-top {
            width: 100%;
        }

        .right-bottom {
            width: 100%;
            justify-content: center;
            text-align: center;
        }

        .stats h3 {
            line-height: 1rem;
        }

        .stats-list {
            padding: 1.5rem;
        }

        .stats-list-item {
            height: 6rem;
        }
    }

    @keyframes colorFlow {
        0% {
            background: #da897a;
        }
        50% {
            background: #413a55;
        }
        100% {
            background: #da897a;
        }
    }

    @keyframes gesture {
        0% {
            transform: translateY(0);
        }
        50% {
            transform: translateY(8vh);
        }
        100% {
            transform: translateY(0);
        }
    }

    @keyframes scrollBackground {
        0% {
            background-position: 0 0;
        }
        100% {
            background-position: 0 100vh;
        }
    }

    @keyframes textFlow {
        0% {
            color: #413a55;
        }
        50% {
            color: #da897a;
        }
        100% {
            color: #413a55;
        }
    }

</style>

<section class="home">
    <div class="intro-background-wrapper"
         style:opacity={opacityLevel}
    >
        <video
                class="background-video"
                autoplay
                loop
                muted
                playsinline
        >
            <source src="/assets/clouds-broll.mp4" type="video/mp4">
        </video>
    </div>
    <div class="name"><h2>Daryk Baker</h2></div>
    <div class="intro">
        <div class="left-top">
            <img class="pfp" src={PictureLinks.pfp} alt="Portrait of Daryk Baker"/>
        </div>
        <div class="right-bottom">
            <h3>A next generation JavaScript developer</h3>
        </div>
    </div>

    <div class="spacer"></div>
    <div class="interact-tip"><h3>&darr;</h3></div>

    <div class="stats-background-wrapper">
        <div class="stats-background-overlay"></div>
    </div>
    <div class="stats" id="0" bind:this={elementRefs[0]} data-id="0">
        <h3>Did you know?</h3>
        <ul class="stats-list" id="1" bind:this={elementRefs[1]} data-id="1">
            <li class="stats-list-item" class:visible={observeElements[1].isVisible} class:hidden={!observeElements[1].isVisible}>
                Over 60% of website traffic comes from mobile devices in 2024
                <small><a href={StatLinks.mobileTraffic}>From Exploding Topics</a></small>
            </li>
            <li class="stats-list-item" class:visible={observeElements[1].isVisible} class:hidden={!observeElements[1].isVisible}>
                On average, 80% of websites are now mobile friendly
                <small><a href={StatLinks.mobileFriendly}>From OddBall Marketing</a></small>
            </li>
            <li class="stats-list-item" class:visible={observeElements[1].isVisible} class:hidden={!observeElements[1].isVisible}>
                75% of users judge a business's credibility based on it's website
                <small><a href={StatLinks.userJudge}>From BusinessDasher</a></small>
            </li>
        </ul>
    </div>

    <div class="sell-myself" bind:this={elementRefs[2]} data-id="2">
        <p class="sell-myself-p" class:visible={observeElements[2].isVisible} class:hidden={!observeElements[2].isVisible}>That's why you need a good website done right</p>
        <p class="sell-myself-p" class:visible={observeElements[2].isVisible} class:hidden={!observeElements[2].isVisible}>That's why you need <b style="color: #0073e6">me</b></p>
    </div>
</section>
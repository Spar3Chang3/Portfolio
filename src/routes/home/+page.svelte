<script lang="js">
    import { StatLinks, PictureLinks } from '$lib/index.js';
    import { onMount } from 'svelte';

    let observeElements = $state([
        {id: 0, isVisible: false},
        {id: 1, isVisible: false},
        {id: 2, isVisible: false},
    ]);
    let elementRefs = $state([null, null, null]);

    onMount(() => {

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
        /*got rid of min-width: 100%, width: 100vw, was a disaster.*/
        max-width: 100%;

        color: var(--text-standard);
        font-family: Roboto, sans-serif;
        overflow: hidden; /*is this needed?*/

        padding: 1rem;
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
        grid-template-columns: 50% 50%;
        grid-template-rows: auto auto;

        min-height: 90vh;
        width: 100%;

        justify-content: center;
        align-items: center;


    }

    .left-top {
        position: relative;
        display: flex;

        height: 60vh;

        justify-content: center;
        align-items: start;

    }

    .pfp {
        max-height: 95%;
        max-width: 95%;

        object-fit: contain;
        border-radius: 10%;
    }

    .right-bottom {
        position: relative;
        display: flex;
        flex-wrap: wrap;

        height: 40vh;
        width: 100%;

        justify-content: center;
        align-items: start;

        font-size: 2rem;
        line-height: 2.2rem;
        margin-bottom: 20vh;
    }

    .right-bottom h3 {
        width: 95%;
        text-align: justify-all;
    }

    .interact-tip {
        position: absolute;

        top: 80vh;

        width: 100%;
        height: fit-content;

        font-size: 1.5rem;
    }

    .interact-tip h3 {
        animation: gesture 5s infinite ease;
        text-align: center;
    }

    .stats {
        position: relative;
        display: flex;
        flex-direction: column;

        min-height: 90vh;
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
        transition: all 0.5s ease;
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

        min-height: 90vh;
        width: 100%;

        justify-content: center;
        align-items: center;

        font-size: 2rem;
    }

    .sell-myself-p {
        transform: translateX(-50vw);
        opacity: 0;
        transition: all 0.5s ease;
    }

    .sell-myself-p:nth-child(2) {
        transition-delay: 1s;
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

</style>

<section class="home">
    <div class="name"><h2>Daryk Baker</h2></div>
    <div class="intro">
        <div class="left-top">
            <img class="pfp" src={PictureLinks.pfp} alt="Portrait of Daryk Baker"/>
        </div>
        <div class="right-bottom">
            <h3>A next generation JavaScript developer</h3>
        </div>
    </div>
    <div class="interact-tip"><h3>&darr;</h3></div>

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
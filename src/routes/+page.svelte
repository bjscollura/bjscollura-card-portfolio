<svelte:head>
    <title>Brian Collura</title>
</svelte:head>

<div class="page-wrapper">
    <div class="brian">
        <div class="hero-text">
            <h1>
            Brian
            Collura.
            </h1>
        </div>
    </div>
    <div class="description">
        <div class="hero-text">
            <h2>
            Designer,
            Developer,
            Dreamer.
            </h2>
        </div>
    </div>
    
    <div class="buttons">
    <!-- buttons -->
        <button>Projects</button>
        <button>About Me</button>
    </div>
    
    <div class="links">
    <!-- social links and resume -->
        <button class='icon'>
            <i class="fab fa-linkedin-in fa-lg" />
        </button>
        <button class='icon'>
            <i class="fab fa-github fa-lg" />
        </button>
        <button>Resume.pdf</button>
    </div>
</div>

<style>
* {
    /* outline: 1px solid salmon; */
}
@media (orientation: portrait) {
    .page-wrapper {
        display: grid;
        grid-template-areas:
        "."
        "brian"
        "description"
        "."
        "buttons"
        "."
        "links";
        grid-template-rows: 2fr auto auto 5fr auto 5fr auto;
        height: 100vh;
        margin-inline-start: .6rem;
    }
    .brian {
        grid-area: brian;
    }
    .description {
        grid-area: description;
    }
    .buttons {
        grid-area: buttons;
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: .8rem;
        width: min(50vw, 300px);
        margin: 0 auto;
    }
    .buttons > button {
        width: 100%;
    }
    .links {
        grid-area: links;
        display: flex;
        flex-direction: row;
        justify-content: center;
        gap: 1rem;
        margin-block-end: 5px;
    }
    .hero-text {
        font-family: 'Josefin Sans', sans-serif;
        width: 1px;
        line-height: 14vmin;
    }
    h1 {
        font-size: 12vmin;
        color: var(--color-second);
    }
    h2 {
        font-size: 12vmin;
        color: var(--color-accent);
    }
    
}
@media (orientation: landscape) {

}

</style>
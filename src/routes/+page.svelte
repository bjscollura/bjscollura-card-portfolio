<script>
    import ThemePicker from "$lib/ThemePicker.svelte";
    
    let pageHeight, pageWidth;
</script>

<svelte:head>
    <title>Brian Collura</title>
</svelte:head>
<svelte:window bind:innerHeight={pageHeight} bind:innerWidth={pageWidth} />

<div class="page-wrapper">
    <header>
    <!-- social links and resume -->
        {#if (pageWidth / pageHeight < 1)}
            <ThemePicker labelSide="top"/>
        {:else}
            <ThemePicker labelSide="bottom"/>
        {/if}
        <div class="iconlinks">
            <a class='icon' href="https://www.linkedin.com/in/bjscollura/" target="_blank">
                <i class="fab fa-linkedin-in" />
            </a>
            <a class='icon' href="https://github.com/bjscollura" target="_blank">
                <i class="fab fa-github" />
            </a>
        </div>
        <a class='cta' href='Resume_March2024_Recent.pdf' target="_blank">Resume.pdf</a>
    </header>
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
    <nav>
    <!-- buttons -->
        <a class='cta' href='/work'>Work</a>
        <a class='cta' href='/about'>About Me</a>
    </nav>
</div>

<style>
/* * {
    outline: 1px solid salmon;
} */
.page-wrapper {
    display: grid;
    height: 100vh; /* fallback */
    height: 100svh;
}
.brian {
    grid-area: brian;
}
.description {
    grid-area: description;
}
.iconlinks {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    gap: 1rem;
}
.hero-text {
    font-family: 'Josefin Sans', sans-serif;
}
h1 {
    color: var(--color-second);
}
h2 {
    color: var(--color-accent);
}
@media (orientation: portrait) {
    .page-wrapper {
        grid-template-areas:
        "."
        "brian"
        "description"
        "."
        "buttons"
        "."
        "links";
        grid-template-rows: 2fr auto auto 5fr auto 5fr auto;
        margin-inline-start: .6rem;
    }
    nav {
        grid-area: buttons;
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: .8rem;
        width: min(50vw, 300px);
        margin: 0 auto;
    }
    nav > * {
        width: 100%;
    }
    header {
        grid-area: links;
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        gap: 2rem;
        margin-block-end: 5px;
    }
    .hero-text {
        width: 1px;
        line-height: 14vmin;
    }
    h1 {
        font-size: 12vmin;
    }
    h2 {
        font-size: 12vmin;
    }
}
@media (orientation: landscape) {
    .page-wrapper {
        grid-template-areas:
        "links"
        "."
        "brian"
        "description"
        "."
        "buttons"
        ".";
        grid-template-rows: auto 2fr auto auto 3fr auto .7fr;
        margin-inline: .5rem;
    }
    nav {
        grid-area: buttons;
        display: flex;
        flex-direction: row;
        justify-content: center;
        gap: 1.5rem;
        /* margin-block-end: 3rem; */
        margin-inline: auto;
        width: max(30vw, 332px);
    }
    nav > * {
        width: 100%;
    }
    header {
        grid-area: links;
        display: flex;
        flex-direction: row;
        justify-content: flex-end;
        align-items: center;
        gap: 2rem;
        margin-block-start: 1rem;
        margin-inline-end: .5rem;
    }
    .hero-text {
        /* width: 1px; */
        line-height: min(160px, 8vmax);
    }
    h1 {
        font-family: 'Josefin Sans', sans-serif;
        font-size: min(140px, 7vmax);
    }
    h2 {
        /* font-family: 'Tangerine', cursive; */
        font-weight: 700;
        font-size: min(100px, 5vmax);
    }
}
</style>
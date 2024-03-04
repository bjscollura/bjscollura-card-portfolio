<script>
    import ThemePicker from "$lib/ThemePicker.svelte";
    import { page } from "$app/stores";
    
    let pageHeight, pageWidth;
    let urlregex = /\/work\/\w+/g;
</script>
<svelte:window bind:innerHeight={pageHeight} bind:innerWidth={pageWidth} />

<div class="content-grid">
    <div class="full {(pageHeight > 600) ? 'sticky' : ''}">
        <div class="headerwrapper">
            {#if ($page.url.pathname.search(urlregex) > -1)}
                <div class="back">
                    <a href="/work">&larr; Back</a>
                </div>
            {/if}
            <header>
                <!-- social links and resume -->
                <ThemePicker labelSide="bottom"/>
                <div class="iconlinks">
                    <a class='icon' href='/'>
                        <i class="fas fa-home"></i>
                    </a>
                    <a class='icon' href='https://www.linkedin.com/in/bjscollura/' target="_blank">
                        <i class="fab fa-linkedin-in" />
                    </a>
                    <a class='icon' href="https://github.com/bjscollura" target="_blank">
                        <i class="fab fa-github" />
                    </a>
                </div>
                <a class='cta' href='/Resume_March2024_Recent.pdf' target="_blank">Resume.pdf</a>
            </header>
        </div>
    </div>
    <div class='full slot'>
        <slot />
    </div>
    
    <nav></nav>
    <footer></footer>
</div>

<style>
    .content-grid,
    .slot :global(.content-grid) {
        display: grid;
        grid-template-columns: [full-start] 8fr [breakout-start] 5fr [content-start] 75ch [content-end] 5fr [breakout-end] 8fr [full-end];
    }
    .content-grid .content,
    .slot :global(.content-grid .content) {
        grid-column: content;
    }
    .content-grid .breakout,
    .slot :global(.content-grid .breakout) {
        grid-column: breakout;
    }
    .content-grid .full,
    .slot :global(.content-grid .full) {
        grid-column: full;
    }
    :global(.centered) {
        display: flex;
        flex-direction: column;
        align-items: center;
        text-align: center;
    }

    .iconlinks {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        gap: 1.5rem;
    }
    .headerwrapper {
        display: grid;
        margin-inline-start: .6rem;
        margin-block-end: 1.8rem;
        grid-template-areas: ". links .";
        grid-template-columns: 1fr auto 1fr;
    }
    .sticky {
        position: sticky;
        top: 0px;
        background-color: var(--color-bg);
    }
    .back {
        /* margin-block-end: 2rem; */
        /* height: 2rem; */
        /* width: 100%; */
        align-self: center;
        justify-self: center;
    }
    .sticky + .slot {
        padding-top: 75px;
    }
@media (orientation: portrait) {
    /* .headerwrapper {
        display: grid;
        margin-inline-start: .6rem;
        grid-template-areas: ". links .";
        grid-template-columns: 1fr auto 1fr;
    } */
    header {
        grid-area: links;
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        gap: 2rem;
        margin-block-end: 5px;
    }
}
@media (orientation: landscape) {
    header {
        grid-area: links;
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        gap: 2rem;
        margin-block-start: 1rem;
        margin-inline-end: .5rem;
    }
}
</style>
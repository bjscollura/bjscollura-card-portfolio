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
        <button>Projects ></button>
        <button>About Me ></button>
    </div>
    
    <div class="links">
    <!-- social links and resume -->
        <button>in</button>
        <button>github</button>
        <button>Resume.pdf</button>
    </div>
</div>

<style>
* {
    /* outline: 1px solid salmon; */
}
button {
    display: inline-block;
    border: none;
    border-radius: 7px;
    margin: 0;
    padding: .8rem 1.6rem;
    background: none;
    font: inherit;
    font-weight: 700;
    text-align: center;
    cursor: pointer;
    outline: none;
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
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
    }
    .links {
        grid-area: links;
        display: flex;
        flex-direction: row;
        justify-content: center;
    }
    .hero-text {
        font-family: 'Montserrat', sans-serif;
        width: 1px;
    }
    h1 {
        font-size: 12vmin;
    }
    h2 {
        font-size: 12vmin;
    }
    
}
@media (orientation: landscape) {

}

</style>
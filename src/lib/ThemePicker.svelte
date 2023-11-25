<script>
    import Dice from "$lib/Dice.svelte";
    
    export let labelSide = 'bottom';
    
    let themeArray = ["BlueJean","Monokai","CoffeeLeaf","LimeRickey","Nantucket"];
    let props = {
        displayNumber: 5,
        themeName: themeArray[4] //dice number is base-1
    };
    let diceLabelWrapperEl;
    let isLabelVisible = false;
    let labelTimeoutID;
    
    function changeTheme() {
        let currentTheme = document.body.className;
        let randNum = Math.floor(Math.random() * themeArray.length);
        let newTheme = `theme-${(themeArray[randNum]).toLowerCase()}`;
        while (currentTheme === newTheme) {
            randNum = Math.floor(Math.random() * themeArray.length);
            newTheme = `theme-${(themeArray[randNum]).toLowerCase()}`;
        }
        document.body.className = '';
        document.body.classList.add(newTheme);
        
        props.displayNumber = randNum + 1; //change number for Dice.svelte to display, base 1 vs base 0
        props.themeName = themeArray[randNum];
        
        //Label
        window.clearTimeout(labelTimeoutID); //reset timout from previous clicks within 2s
        isLabelVisible = false;
        window.requestAnimationFrame(() => isLabelVisible = true);
        window.requestAnimationFrame(() => diceLabelWrapperEl.classList.remove("animate"));
        window.requestAnimationFrame(() => diceLabelWrapperEl.classList.add("animate")); //reapply animate class
        // if (isLabelVisible) { diceLabelWrapperEl.style.animationPlayState = 'paused' }
        labelTimeoutID = window.setTimeout(() => {
            isLabelVisible = false;
            console.log('time!');
        }, 2000);
    }
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<div class="diceWrapper">
    <div class='svgWrapper' on:click={changeTheme}>
        <svelte:component this={Dice} {...props} />
    </div>
    {#if isLabelVisible}
        <div class="diceLabelWrapper" bind:this={diceLabelWrapperEl}>
            <div class="diceLabel {labelSide}">
                {props.themeName}
            </div>
        </div>
    {/if}
</div>

<style>
    div.svgWrapper {
        display: flex;
        flex-direction: column;
        justify-content: center;
        cursor: pointer;
    }
    p {
        color: var(--color-accent)
    }
    @keyframes labelAppear {
        0% {
            opacity: 0;
        }
        10% {
            opacity: 1;
        }
        50% {
            opacity: 1;
        }
        100% {
            opacity: 0;
        }
    }
    .diceWrapper {
        position: relative;
    }
    .diceLabel {
        position: absolute;
        background-color: var(--color-accent);
        color: var(--color-bg);
        left: -8px;
        padding: 0.5rem;
        border-radius: 7px;
    }
    .diceLabel.bottom {
        top: 100%;
        margin-top: 0.5rem;
    }
    .diceLabel.top {
        bottom: 100%;
        margin-bottom: 0.6rem;
    }
    .diceLabel::after {
        content: "";
        position: absolute;
        left: 0.75rem;
        width: 0;
        height: 0;
        /* opacity: 0; */
    }
    .diceLabel.bottom::after {
        top: 1px;
        border: 0.5rem solid transparent;
        border-bottom-color: var(--color-accent);
        border-top-width: 0;
        margin-top: -0.5rem;
    }
    .diceLabel.top::after {
        bottom: 1px;
        border: 0.6rem solid transparent;
        border-top-color: var(--color-accent);
        border-bottom-width: 0;
        margin-bottom: -0.5rem;
    }
    .diceLabelWrapper {
        opacity: 1;
    }
    .diceLabelWrapper.animate {
        animation: 2s linear 0s labelAppear;
        opacity: 0;
    }
    /* .diceLabel.animate::after {
        animation: 2s linear 0s labelAppear;
        opacity: 0;
    } */
</style>
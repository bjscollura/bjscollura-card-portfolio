<script>
    import Dice from "$lib/Dice.svelte";
    import { theme } from "./LocalStore";
    import { browser } from "$app/environment";
    import { onMount } from "svelte";
    
    export let labelSide = 'bottom';
    
    let themeArray = ["BlueJean","Monokai","CoffeeLeaf","LimeRickey","Nantucket","BunnyRose"];
    let tempThemeArray = themeArray.slice(0);
    let props = {
        displayNumber: 1,
        themeName: themeArray[0] //dice number is base-1
    };
    let diceLabelWrapperEl;
    let isLabelVisible = false;
    let labelTimeoutID;
    
    onMount(() => {
        let storedTheme = localStorage.getItem('theme'); 
        let startTheme = (themeArray.indexOf(storedTheme) >= 0) ? storedTheme : themeArray[0];
        document.body.classList.add(`theme-${startTheme.toLowerCase()}`);
        
        tempThemeArray = themeArray.filter(val => val !== startTheme);
        props.themeName = startTheme;
        props.displayNumber = themeArray.indexOf(startTheme) + 1;
    });
    
    function changeTheme() {
        let currentTheme = document.body.className;
        let randNum = Math.floor(Math.random() * tempThemeArray.length);
        let newTheme = tempThemeArray[randNum];
        let newThemeName = `theme-${newTheme.toLowerCase()}`;
        localStorage.setItem("theme", newTheme); //local cookie
        tempThemeArray = tempThemeArray.filter( (val, ii) => newTheme !== val );
        if (!tempThemeArray.length) {
            tempThemeArray = themeArray.filter(val => newTheme !== val);
        }
        // while (currentTheme === newThemeName) {
        //     randNum = Math.floor(Math.random() * themeArray.length);
        //     newThemeName = `theme-${(themeArray[randNum]).toLowerCase()}`;
        // }
        document.body.className = '';
        document.body.classList.add(newThemeName);
        
        props.displayNumber = themeArray.indexOf(newTheme) + 1; //change number for Dice.svelte to display, base 1 vs base 0
        props.themeName = newTheme;
        
        //Label
        window.clearTimeout(labelTimeoutID); //reset timout from previous clicks within 2s
        isLabelVisible = false;
        window.requestAnimationFrame(() => isLabelVisible = true);
        window.requestAnimationFrame(() => diceLabelWrapperEl.classList.remove("animate"));
        window.requestAnimationFrame(() => diceLabelWrapperEl.classList.add("animate")); //reapply animate class
        // if (isLabelVisible) { diceLabelWrapperEl.style.animationPlayState = 'paused' }
        labelTimeoutID = window.setTimeout(() => {
            isLabelVisible = false;
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
                Theme: {props.themeName}
            </div>
        </div>
    {/if}
</div>

<style>
    div.svgWrapper {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        padding-top: .5rem;
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
        
        /* overflow-x: visible; */
        min-width: max-content;
    }
    .diceLabel.bottom {
        top: 100%;
        margin-top: 0.75rem;
    }
    .diceLabel.top {
        bottom: 100%;
        margin-bottom: 0.75rem;
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
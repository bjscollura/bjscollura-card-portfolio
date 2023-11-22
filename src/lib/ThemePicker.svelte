<script>
    import Dice from "$lib/Dice.svelte";
    
    export let labelSide = 'bottom';
    
    let themeArray = ["BlueJean","Monokai","CoffeeLeaf","LimeRickey","Nantucket"];
    let props = {
        displayNumber: 5,
        themeName: themeArray[4] //dice number is base-1
    };
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
    }
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<div class="diceWrapper">
    <div on:click={changeTheme}>
        <svelte:component this={Dice} {...props} />
    </div>
    <div class="diceLabel {labelSide}">
        {props.themeName}
    </div>
</div>

<style>
    div {
        display: flex;
        flex-direction: column;
        justify-content: center;
        cursor: pointer;
        /* outline: 1px solid red; */
    }
    p {
        color: var(--color-accent)
    }
    
    .diceWrapper {
        position: relative;
    }
    .diceLabel.bottom {
        position: absolute;
        top: 100%;
        left: -8px;
        margin-top: 0.5rem;
        padding: 0.5rem;
        border-radius: 7px;
        background-color: var(--color-accent);
        color: var(--color-bg);
    }
    .diceLabel.bottom::after {
        content: "";
        position: absolute;
        top: 1px;
        left: 0.75rem;
        width: 0;
        height: 0;
        border: 0.5rem solid transparent;
        border-bottom-color: var(--color-accent);
        border-top-width: 0;
        margin-top: -0.5rem;
    }
    .diceLabel.top {
        position: absolute;
        bottom: 100%;
        left: -8px;
        margin-bottom: 0.6rem;
        padding: 0.5rem;
        border-radius: 7px;
        background-color: var(--color-accent);
        color: var(--color-bg);
    }
    .diceLabel.top::after {
        content: "";
        position: absolute;
        bottom: 1px;
        left: 0.75rem;
        width: 0;
        height: 0;
        border: 0.6rem solid transparent;
        border-top-color: var(--color-accent);
        border-bottom-width: 0;
        margin-bottom: -0.5rem;
    }
</style>
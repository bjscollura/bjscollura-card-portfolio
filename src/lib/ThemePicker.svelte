<script>
    import Dice from "$lib/Dice.svelte";
    
    let themeArray = ["BlueJean","Monokai","Coffee","LimeRickey","Nantucket"];
    let props = {
        displayNumber: 5,
        themeName: themeArray[displayNumber - 1] //dice number is base-1
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
<div on:click={changeTheme}>
    <svelte:component this={Dice} {...props} />
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
</style>
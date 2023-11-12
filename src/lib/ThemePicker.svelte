<script>
    import Dice from "$lib/Dice.svelte";

    let themeArray = ["BlueJean","Monokai","Coffee","LimeRickey","Nantucket"];
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
    }
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<div on:click={changeTheme}>
    <Dice />
</div>

<style>
p {
    color: var(--color-accent)
}
div {
    display: flex;
    flex-direction: column;
    justify-content: center;
    cursor: pointer;
    /* outline: 1px solid red; */
}
</style>
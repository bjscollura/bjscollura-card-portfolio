<script>
    let themeArray = ["theme-bluejean","theme-monokai","theme-coffee","theme-limerickey","theme-nantucket"];
    function changeTheme(themeNumber) {
        document.body.className = '';
        document.body.classList.add(themeArray[themeNumber]);
    }
</script>

<div>
    <button on:click={() => changeTheme(Math.floor(Math.random() * 5))}>change theme</button>
</div>
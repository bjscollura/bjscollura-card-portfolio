<div class="content-grid">
    <header></header>
    <p class="breakout">testing</p>
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
    grid-template-columns: [full-start] 100px [breakout-start] 100px [content-start] 1fr [content-end] 100px [breakout-end] 100px [full-end];
}
.content-grid > *,
.slot :global(.content-grid > *) {
    grid-column: content;
}
.content-grid > .breakout,
.slot :global(.content-grid > .breakout) {
    grid-column: breakout;
}
.content-grid > .full,
.slot :global(.content-grid > .full) {
    grid-column: full;
}
</style>
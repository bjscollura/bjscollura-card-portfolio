<script>
    export let size = 24;
</script>

<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100' style='width: {size}px; height: {size}px;'>
    <rect x='2' y='2' width='96' height='96' rx='7' ry='7' style='fill: none;stroke-width: 5' />
    <ellipse cx='50' cy='50' rx='7' ry='7' />
    <ellipse cx='25' cy='75' rx='7' ry='7' />
    <ellipse cx='75' cy='75' rx='7' ry='7' />
    <ellipse cx='25' cy='25' rx='7' ry='7' />
    <ellipse cx='75' cy='25' rx='7' ry='7' />
</svg>

<style>
    rect {
        stroke: var(--color-accent, green);
    }
    ellipse {
        stroke: var(--color-accent, green);
        fill: var(--color-accent, green);
    }
</style>
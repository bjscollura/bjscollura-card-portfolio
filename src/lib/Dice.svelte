<script>
    export let size = 24;
    export let displayNumber = 5;
    export let themeName;
</script>

<svg tabIndex='0' xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100' style='width: {size}px; height: {size}px;'>
    <defs>
        <rect id='diceBorder' x='2' y='2' width='96' height='96' rx='7' ry='7' style='fill: none;stroke-width: 5' />
        <g id='dice1'>
            <ellipse cx='50' cy='50' rx='7' ry='7' />
        </g>
        <g id='dice2'>
            <ellipse cx='25' cy='25' rx='7' ry='7' />
            <ellipse cx='75' cy='75' rx='7' ry='7' />
        </g>
        <g id='dice3'>
            <ellipse cx='25' cy='25' rx='7' ry='7' />
            <ellipse cx='50' cy='50' rx='7' ry='7' />
            <ellipse cx='75' cy='75' rx='7' ry='7' />
        </g>
        <g id='dice4'>
            <ellipse cx='25' cy='25' rx='7' ry='7' />
            <ellipse cx='25' cy='75' rx='7' ry='7' />
            <ellipse cx='75' cy='25' rx='7' ry='7' />
            <ellipse cx='75' cy='75' rx='7' ry='7' />
        </g>
        <g id='dice5'>
            <ellipse cx='50' cy='50' rx='7' ry='7' />
            <ellipse cx='25' cy='75' rx='7' ry='7' />
            <ellipse cx='75' cy='75' rx='7' ry='7' />
            <ellipse cx='25' cy='25' rx='7' ry='7' />
            <ellipse cx='75' cy='25' rx='7' ry='7' />
        </g>
        <g id='dice6'>
            <ellipse cx='25' cy='25' rx='7' ry='7' />
            <ellipse cx='25' cy='50' rx='7' ry='7' />
            <ellipse cx='25' cy='75' rx='7' ry='7' />
            <ellipse cx='75' cy='25' rx='7' ry='7' />
            <ellipse cx='75' cy='50' rx='7' ry='7' />
            <ellipse cx='75' cy='75' rx='7' ry='7' />
        </g>
    </defs>
    <use href="#diceBorder" />
    <use href='#dice{displayNumber}' />
</svg>
{themeName}

<style>
    @keyframes diceroll {
        0% {
            transform: rotate(0turn);
        }
        37% {
            transform: rotate(-0.25turn);
        }
        100% {
            transform: rotate(0.75turn);
        }
    }
    svg:focus {
        animation: 0.5s linear 0s diceroll;
        /* animation-play-state: paused; */
        outline: none;
    }
    svg:active {
        animation: none;
    }
    rect {
        stroke: var(--color-accent, green);
    }
    ellipse {
        stroke: var(--color-accent, green);
        fill: var(--color-accent, green);
    }
</style>
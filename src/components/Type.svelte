<script lang="ts">
    export let text : string;
    export let speed : number;
    let x = 0;

    const letters = text.split('');
</script>

<span>
    {#each letters as letter}
        <span class="letter" style={`--time: ${x = x + speed}ms`}>{letter}</span>
    {/each}
    <div class="cursor"></div>
</span>

<style lang="scss">
    @keyframes blinker {
        50% {
            outline: 0.1px solid black;
            background-color: currentColor;
        }
    }

    @keyframes show {
        100% {
            opacity: 1;
            width: initial;
        }
    }
    .letter {
        opacity: 0;
        width: 0%;
        animation: show var(--time) forwards step-end;
    }

    span {
        display: flex;
    }

    .cursor {
        width: 0.5em;
        height: 0.2em;
        margin-left: 0.1em;
        margin-top: 0.8em;
        animation: blinker 1000ms step-start infinite;
        outline: 0.1px solid #333e;
    }
</style>
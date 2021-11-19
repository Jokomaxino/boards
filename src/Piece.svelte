<script>
    import { draggable } from "svelte-drag";

    export let id;
    export let symbol;
</script>

{#if symbol == "red checker" || symbol == "black checker"}
    <div class={symbol} use:draggable />
{:else}
    <div {id} class="chess-piece" use:draggable>
        {symbol}
    </div>
{/if}

<style>
    .chess-piece {
        font-size: 48px;
    }

    .checker {
        width: 40px;
        height: 40px;
        border-radius: 20px;
    }
    .red {
        background-color: red;
        margin: auto;
    }
    .black {
        background-color: black;
        margin: auto;
    }
</style>

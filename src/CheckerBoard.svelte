<script>
    import Piece from "./Piece.svelte";

    function num2Letter(i) {
        return String.fromCharCode(97 + i);
    }
</script>

<div id="checker-board">
    {#each Array(8) as _, i}
        {#each Array(8) as _, j}
            {#if (i + j) % 2 == 0}
                <div
                    id={num2Letter(j) + (8 - i).toString()}
                    class="light square"
                />
            {:else}
                <div
                    id={num2Letter(j) + (6 - i).toString()}
                    class="dark square"
                >
                    {#if i > 4}
                        <Piece symbol="black checker" />
                    {:else if i < 3}
                        <Piece symbol="red checker" />
                    {/if}
                </div>
            {/if}
        {/each}
    {/each}
</div>

<style>
    #checker-board {
        width: 400px;
        height: 400px;
        background-color: #ffbc00;
        border: 10px solid rgba(0, 0, 0, 0.65);
        border-radius: 10px;
        margin: auto;
    }

    .square {
        width: 50px;
        height: 50px;
        float: left;
    }
    .dark {
        background-color: rgba(0, 0, 0, 0.25);
    }
    .light {
        background-color: rgba(255, 255, 255, 0.25);
    }
</style>

<script>
    import Piece from "./Piece.svelte";
    const blackPieces = {
        rook: "\u265C",
        knight: "\u265E",
        bishop: "\u265D",
        queen: "\u265B",
        king: "\u265A",
        pawn: "\u265F",
    };

    const whitePieces = {
        rook: "\u2656",
        knight: "\u2658",
        bishop: "\u2657",
        queen: "\u2655",
        king: "\u2654",
        pawn: "\u2659",
    };

    function num2Letter(i) {
        return String.fromCharCode(97 + i);
    }
</script>

<div id="checker-board">
    <div id="a8" class="light square">
        <Piece id="black_rook_1" symbol={blackPieces.rook} />
    </div>
    <div id="b8" class="dark square">
        <Piece id="black_knight_1" symbol={blackPieces.knight} />
    </div>
    <div id="c8" class="light square">
        <Piece id="black_bishop_1" symbol={blackPieces.bishop} />
    </div>
    <div id="d8" class="dark square">
        <Piece id="black_queen_1" symbol={blackPieces.queen} />
    </div>
    <div id="e8" class="light square">
        <Piece id="black_king_1" symbol={blackPieces.king} />
    </div>
    <div id="f8" class="dark square">
        <Piece id="black_bishop_2" symbol={blackPieces.bishop} />
    </div>
    <div id="g8" class="light square">
        <Piece id="black_knight_2" symbol={blackPieces.knight} />
    </div>
    <div id="h8" class="dark square">
        <Piece id="black_rook_2" symbol={blackPieces.rook} />
    </div>

    <!-- black pawn row -->
    {#each Array(8) as _, i}
        {#if i % 2 == 0}
            <div id={num2Letter(i + 1) + "7"} class="dark square">
                <Piece
                    id={"black_pawn_" + (i + 1).toString()}
                    symbol={blackPieces.pawn}
                />
            </div>
        {:else}
            <div id={num2Letter(i + 1) + "7"} class="light square">
                <Piece
                    id={"black_pawn_" + (i + 1).toString()}
                    symbol={blackPieces.pawn}
                />
            </div>
        {/if}
    {/each}

    <!-- middle four rows -->
    {#each Array(4) as _, i}
        {#each Array(8) as _, j}
            {#if (i + j) % 2 == 0}
                <div
                    id={num2Letter(j) + (6 - i).toString()}
                    class="light square"
                />
            {:else}
                <div
                    id={num2Letter(j) + (6 - i).toString()}
                    class="dark square"
                />
            {/if}
        {/each}
    {/each}

    <!-- white pawn row -->
    {#each Array(8) as _, i}
        {#if i % 2 == 0}
            <div id={num2Letter(i + 1) + "2"} class="light square">
                <Piece
                    id={"white_pawn_" + (i + 1).toString()}
                    symbol={whitePieces.pawn}
                />
            </div>
        {:else}
            <div id={num2Letter(i + 1) + "2"} class="dark square">
                <Piece
                    id={"white_pawn_" + (i + 1).toString()}
                    symbol={whitePieces.pawn}
                />
            </div>
        {/if}
    {/each}

    <div id="a1" class="dark square">
        <Piece id="white_rook_1" symbol={whitePieces.rook} />
    </div>
    <div id="b1" class="light square">
        <Piece id="white_knight_1" symbol={whitePieces.knight} />
    </div>
    <div id="c1" class="dark square">
        <Piece id="white_bishop_1" symbol={whitePieces.bishop} />
    </div>
    <div id="d1" class="light square">
        <Piece id="white_queen_1" symbol={whitePieces.queen} />
    </div>
    <div id="e1" class="dark square">
        <Piece id="white_king_1" symbol={whitePieces.king} />
    </div>
    <div id="f1" class="light square">
        <Piece id="white_bishop_2" symbol={whitePieces.bishop} />
    </div>
    <div id="g1" class="dark square">
        <Piece id="white_knight_2" symbol={whitePieces.knight} />
    </div>
    <div id="h1" class="light square">
        <Piece id="white_rook_2" symbol={whitePieces.rook} />
    </div>
</div>

<style>
    #checker-board {
        width: 400px;
        height: 400px;
        background-color: #0aec4e;
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
        background-color: rgba(41, 122, 243, 0.849);
    }
    .light {
        background-color: rgb(243, 220, 9);
    }
</style>

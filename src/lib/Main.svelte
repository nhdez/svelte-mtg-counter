<script>
    import PlayerCard from "./PlayerCard.svelte";

    export let playerCount = 2;
    export let players = Array(playerCount).fill().map((_,i) => ({
        name: `Player ${i + 1}`,
        score: 20
    }))

    function checkPlayerCount() {
        if (playerCount > 4 || playerCount < 2) {
        
            if (playerCount > 4) {
                alert("Too many players!");
                playerCount = 4;
            } else {
                alert("Too few players!");
                playerCount = 2;
            }
        }

        players = Array(playerCount).fill().map((_,i) => ({
            name: `Player ${i + 1}`,
            score: 20
        }))
    }

</script>



<div class="container">
    <div class="controls">
        <label>
            Number of players:
            <input type="number" bind:value={playerCount} on:change={checkPlayerCount} min="2" max="4">
        </label>
        <p>Player count is {playerCount}</p>
    </div>

    <div class="player-grid">
        {#each players as player, i (i)}
            <PlayerCard bind:playerName={player.name} bind:score={player.score} />
        {/each}
    </div>
</div>

<style>
    .container {
        padding: 1rem;
    }

    .controls {
        margin-bottom: 1rem;
    }

    .player-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
        gap: 1rem;
    }
</style>

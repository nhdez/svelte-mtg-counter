<script>
    export let playerName;
    export let score = 20;

    function addPoint() {
        score += 1;
    }

    function removePoint() {
        if (score === 0) {
            alert(playerName + " lost the game");
        } else {
            score -= 1;
        }
    }
</script>

<div class="player-card" class:lost={score === 0}>
    <p>Player name: {playerName}</p> 
    <p>Score: {score}</p>

    <button on:click={addPoint}>+</button>
    <button on:click={removePoint}>-</button>
</div>

<style>
    .player-card {
        border: 1px solid #ccc;
        padding: 1rem;
        margin: 0.5rem;
        border-radius: 4px;
        transition: background-color 0.3s ease;
    }

    .lost {
        background-color: #ffebee;
        border-color: #ef5350;
    }

    .buttons {
        display: flex;
        gap: 0.5rem;
    }

    button {
        padding: 0.5rem 1rem;
        cursor: pointer;
    }
</style>

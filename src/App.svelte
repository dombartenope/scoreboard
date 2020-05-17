<script>
  import Navbar from "./Navbar.svelte";
  import Player from "./Player.svelte";
  import AddPlayer from "./AddPlayer.svelte";

  let players = [];

  const addPlayer = e => {
    const newPlayer = e.detail;
    players = [...players, newPlayer];
  };

  const removePlayer = e => {
    players = players.filter(player => player.name !== e.detail);
  };
</script>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 411px;
    margin: 0 auto;
  }

  .container {
    background: white;
    border: solid 2px #b34b89;
    width: 350px;
    margin: auto;
    padding: 15px;
    -webkit-box-shadow: 10px 9px 21px 0px rgba(0, 0, 0, 0.75);
    -moz-box-shadow: 10px 9px 21px 0px rgba(0, 0, 0, 0.75);
    box-shadow: 10px 9px 21px 0px rgba(0, 0, 0, 0.75);
  }

  p {
    text-transform: uppercase;
    color: #a958eb;
    font-size: 3em;
    font-weight: 100;
  }
</style>

<main>
  <Navbar />

  <div class="container">
    {#if players.length === 0}
      <p>Add A Player</p>
    {:else}
      {#each players as player}
        <Player
          name={player.name}
          points={player.points}
          on:removeplayer={removePlayer} />
      {/each}
    {/if}
    <AddPlayer on:addplayer={addPlayer} />
  </div>

</main>

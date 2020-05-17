<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();
  export let name;
  export let points;
  let showControls = false;

  const addPoint = () => (points += 1);
  const removePoint = () => (points -= 1);
  const toggleControls = () => (showControls = !showControls);
  const onDelete = () => dispatch("removeplayer", name);
</script>

<style>
  h1 {
    display: inline-block;
    color: #a958eb;
    text-transform: uppercase;
    font-size: 3em;
    font-weight: 100;
    margin-top: 0;
    margin-bottom: 0;
  }

  h3 {
    text-align: center;
    display: block;
    margin-top: 0;
    margin-bottom: 40px;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }

  .btn {
    width: 5em;
    color: white;
    border-radius: 5px;
    background: #9f91ff;
    transition: all 0.2s;
  }

  .btn:active {
    width: 6em;
    background: #7988e8;
  }

  .btn-dark {
    background: #776fb3;
  }

  .btn-sm {
    width: 2em;
    color: white;
    border-radius: 5px;
    background: #9f91ff;
    transition: all 0.3s;
    float: right;
    margin-top: 20px;
  }

  .btn-sm:active {
    width: 3em;
    background: #7988e8;
  }

  .btn-red {
    padding: 0;
    font-size: 7pt;
    text-align: center;
    float: left;
    width: 19px;
    height: 19px;
    background: #ff522d;
    transition: all 0.1s;
  }
  .btn-red:active {
    width: 22px;
    height: 22px;
    background: #cc4c47;
  }

  input {
    text-align: center;
    margin: auto;
    display: block;
    border-radius: 5px;
    color: white;
    background: #3d78bf;
  }
</style>

<main>

  <div class="card">
    <button class="btn btn-red" on:click={onDelete}>X</button>
    <h1>{name}</h1>
    <button class="btn-sm" on:click={toggleControls}>
      {#if showControls}-{:else}+{/if}
    </button>

    {#if points !== undefined}
      <h3>{points}</h3>
    {/if}

    {#if showControls}
      <button class="btn" on:click={addPoint}>+1</button>
      <button class="btn btn-dark" on:click={removePoint}>-1</button>
      <input type="number" bind:value={points} />
    {/if}
    <hr />
  </div>

</main>

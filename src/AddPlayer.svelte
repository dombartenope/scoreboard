<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  let player = {
    name: "",
    points: 0
  };

  const onSubmit = e => {
    e.preventDefault();
    dispatch("addplayer", player);
    player = {
      name: "",
      points: 0
    };
  };
</script>

<style>
  form {
    margin-top: 10px;
  }
  .input {
    width: 100%;
    margin: 1 auto;
    text-align: center;
    padding: 10px;
    display: inline-block;
    border-radius: 5px;
    color: white;
    background: #3d78bf;
  }

  input::placeholder {
    color: white;
  }

  .btn {
    display: block;
    margin: auto;
    width: 6em;
    color: white;
    border-radius: 5px;
    background: #8ca1ff;
    transition: all 0.2s;
  }

  .btn:active {
    width: 7em;
    background: #7988e8;
  }
</style>

<form on:submit={onSubmit}>
  <input
    class="input"
    type="text"
    placeholder="Player Name"
    bind:value={player.name} />
  <input
    class="input"
    type="number"
    placeholder="Player Points"
    bind:value={player.points} />
  <input type="submit" class="btn" value="Add Player" />
</form>

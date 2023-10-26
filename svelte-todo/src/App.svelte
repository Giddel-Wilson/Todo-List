<script>
  import svelteLogo from "./assets/svelte.svg";
  import viteLogo from "/vite.svg";
  import Counter from "./lib/Counter.svelte";

  let newItem = "";
  let todoList = [];

  const addItem = () => {
    todoList = [...todoList, {text: newItem, complete: false}]
    newItem = "";
  }
  const delItem = (index) => {
    todoList.splice (index, 1);
    todoList = todoList;
  }
</script>

<main>
  <div>
    <a href="https://vitejs.dev" target="_blank" rel="noreferrer">
      <img src={viteLogo} class="logo" alt="Vite Logo" />
    </a>
    <a href="https://svelte.dev" target="_blank" rel="noreferrer">
      <img src={svelteLogo} class="logo svelte" alt="Svelte Logo" />
    </a>
  </div>
  <h1>Vite + Svelte</h1>
  <h2>Svelte Todo</h2>
  
  <section class="input">
    <form action="" method="get" on:submit|preventDefault>
      <label for="in1">Input task:</label>
      <input type="text" class="in1" bind:value={newItem} on:keydown="{e => e.key === 'Enter' && addItem()}" placeholder="New task...">
    </form>
    <br>
    <button type="submit" on:click={addItem}>Add</button>
  </section>

  <section class="view">
    {#each todoList as task, index}
      <ul>
        <li>{task.text} <span class="del" on:click={() => delItem(index)}>🗑️</span></li>
      </ul>
    {/each}
  </section>
</main>

<style>
  .logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
    transition: filter 300ms;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .logo.svelte:hover {
    filter: drop-shadow(0 0 2em #ff3e00aa);
  }
  li {
    display: flex;
    justify-content: space-between;
    padding: 1%;
  }
  ul {
    margin: 0%;
    text-align: justify;
  }
  ul:hover {
    background-color: #646cffaa;
    transform: scale(1.03, 1.2);
    transition-duration: 0.5s;
    transition-timing-function: ease-in-out;
    border-radius: 30px;
    box-shadow: 5px black;
    cursor: pointer;
  }
  ul:active {
    background-color: darkred;
  }
</style>

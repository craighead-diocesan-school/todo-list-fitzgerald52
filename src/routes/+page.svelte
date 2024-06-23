<script>
  import Header from '$lib/Header.svelte'

  let tasks = []

  function addTask() {
    tasks = [...tasks, '']
  }
</script>

<Header />

<button on:click={addTask}>📝 Add</button>
{#each tasks as task, index}
  <div class="task">
    <input bind:value={tasks[index]} />
  </div>
{/each}

<style>
  .task {
    display: block;
  }
</style>

<script>
  import Header from '$lib/Header.svelte'

  let tasks = []

  function addTask() {
    tasks = [...tasks, '']
  }
  function removeTask(index) {
    tasks = [...tasks.slice(0, index), ...tasks.slice(index + 1)]
  }
</script>

<Header />
<button on:click={addTask}>📝 Add</button>

{#each tasks as task, index}
  <div class="task">
    <input bind:value={tasks[index]} />

    <button
      on:click={() => {
        removeTask(index)
      }}>🗑</button
    >
  </div>
{/each}

<style>
  .task {
    display: block;
  }
</style>

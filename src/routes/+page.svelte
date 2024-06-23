<script>
  import Header from '$lib/Header.svelte'

  let tasks = []

  function addTask() {
    tasks = [...tasks, '']
  }
  function removeTask(index) {
    tasks = [...tasks.slice(0, index), ...tasks.slice(index + 1)]
  }
  function saveTasks() {
    localStorage.todos = JSON.stringify(tasks)
  }
  function loadTasks() {
    tasks = JSON.parse(localStorage.todos)
  }
</script>

<Header />
<button on:click={addTask}>📝 Add</button>
<button on:click={saveTasks}>💾 Save</button>
<button on:click={loadTasks}> 📡 Load</button>
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

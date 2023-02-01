<script>
  let tasks = [];

  let data = {
    id: null,
    task: "",
  };
  const addTask = (e) => {
    e.preventDefault();
    const newTask = {
      id: Date.now() + Math.random(),
      task: data.task,
    };
    tasks = tasks.concat(newTask);
    data = {
      id: null,
      task: "",
    };
  };
  const deleteTask = (id) => {
    tasks = tasks.filter((task) => task.id !== id);
  };
</script>

<main>
  <div class="main">
    <h1>Items List</h1>
    <div class="addItem">
      <input bind:value={data.task} type="text" class="addText" />
      <button class="button" on:click={addTask}>Add</button>
    </div>
    {#each tasks as task}
      <ul>
        <li>
          {task.task}<span on:click={deleteTask(task.id)}>x</span>
        </li>
      </ul>
    {/each}
  </div>
</main>

<style>
  body {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
  }
  ::-webkit-scrollbar {
    width: 3px;
  }
  ::-webkit-scrollbar-track {
    display: none;
  }
  ::-webkit-scrollbar-thumb {
    background: #888;
  }
  .main {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    width: 500px;
    height: 70vh;
    text-align: center;
    border: 2px solid #d7d7d7;
    font-family: sans-serif;
    border-radius: 10px;
    overflow-y: scroll;
    overflow-x: hidden;
  }
  .button {
    background: rgb(56, 111, 160);
    border-radius: 10px;
  }
  h1 {
    text-align: center;
    background-color: rgb(56, 111, 160);
    padding: 30px 0;
    margin-top: 0;
    color: white;
    border-radius: 10px;
  }

  ul {
    list-style: none;
    font-size: 20px;
    color: #686868;
    margin-left: -40px;
    margin-bottom: 0;
  }

  li {
    border-bottom: 1px solid #ededed;
    background-color: #f4f4f4;
    padding: 10px 0;
    margin-bottom: 5px;
  }

  li span {
    cursor: pointer;
    position: relative;
    float: right;
    margin-right: 30px;
  }

  .addItem {
    position: relative;
    padding-bottom: 0;
    height: 30px;
  }

  .addText {
    width: 80%;
    height: 30px;
  }

  .addItem button {
    height: 35px;
    width: 50px;
  }
</style>

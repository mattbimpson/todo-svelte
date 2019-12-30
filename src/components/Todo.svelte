<script>
    export let todo;

    function completedChanged() {
        todo.completed = !todo.completed;
    }

    function remove() {

    }
</script>

<div class={`todo-container ${todo.completed ? 'completed' : ''}`} on:click={completedChanged}>
    <div class='todo-item'>
        {todo.text}
    </div>
    <div class='todo-controls'>
        <input type="button" class="btn" value="X" on:click={remove} />
    </div>
</div>

<style>
  .todo-container.completed {
    text-decoration: line-through;
    color: darkgray;
    background-color: darkgreen;
  }

  .todo-item, .todo-controls {
      display: block;
  }

  .todo-controls {
      font-size: small;
      text-align: right;
  }

  .todo-container {
      border-radius: 5px;
      background: darkgray;
      padding: 5px;
      margin-top: 5px;
      width: 600px;
  }

  .btn {
      border-radius: 5px;
  }

</style>

<script>
  let confirming = false;
  export let buttonText = '';
  export let action;

  function toggleConfirm(toggle) {
    confirming = toggle;
  }
</script>

<div>
    {#if !confirming}
      <input type="button" id="btnMain" value={buttonText} on:click={ () => toggleConfirm(true) } />
    {/if}
    {#if confirming}
      <div>
            <input type="button" class="confirm-yes" value={"Yes"} on:click={ () => {
                action();
                toggleConfirm(false);
            }} />
            <input type="button" class="confirm-no" value={"No"} on:click={ () => toggleConfirm(false) } />
        </div>
    {/if}
</div>

<style>
  input {
    border-radius: 5px;
    border: 0px;
  }

  .confirm-yes {
      background-color: lightgreen;
      padding: 5px;
      margin-right: 5px;
  }
  .confirm-no {
      background-color: lightcoral;
      padding: 5px;
  }
</style>
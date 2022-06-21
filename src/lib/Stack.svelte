<script>
  import { stackStore } from "./stores";
  import StackPush from "./StackPush.svelte";
  import StackPop from "./StackPop.svelte";

  let itemName = "";
  let storeStack = [];

  stackStore.subscribe((value) => {
    storeStack = value;
    itemName = "";
  });
</script>

<div>
  <input bind:value={itemName} placeholder="Item Name" />

  <div class="main-flex-container">
    <div class="stack-item">
      <p>{itemName}</p>
    </div>

    <StackPush item={{ name: itemName }} />

    <div class="stack-list">
      {#each storeStack as { name }, i}
        {#if name}
          <div class="stack-item">
            <p>{i}</p>
            <h3>{name}</h3>
          </div>
        {/if}
      {/each}
    </div>

    <StackPop />
  </div>
</div>

<style>
  .main-flex-container {
    font-family: arial;
    font-size: 18px;
    margin: 25px;
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    width: 600px;
  }

  .stack-item {
    color: #393939;
    border-radius: 1em;
    border: 2px solid rgba(191, 25, 209, 0.847);
    height: 100px;
    width: 200px;
  }

  .stack-list {
    display: flex;
    flex-direction: column-reverse;
    justify-content: space-evenly;
    color: #393939;
    border-radius: 1em;
    padding: 15px;
    border: 2px dashed rgba(6, 6, 6, 0.847);
    width: 200px;
  }
</style>

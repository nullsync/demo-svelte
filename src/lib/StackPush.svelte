<script>
  import { stackStore } from "./stores";

  export let item;
  let storeStack;

  stackStore.subscribe((value) => {
    storeStack = value;
  });

  function stackPush() {
    if (item && item.name) {
      stackStore.update((value) => {
        value.push(item);
        return value;
      });
    }
  }
</script>

<button on:click={stackPush}> Push </button>

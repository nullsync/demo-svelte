<script>
  import { stackStore } from "./stores";

  let storeStack;

  stackStore.subscribe((value) => {
    storeStack = value;
  });

  function stackPop() {
    stackStore.update((value) => {
      value.pop();
      return value;
    });
  }
</script>

<button on:click={stackPop}> Pop </button>

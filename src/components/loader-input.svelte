<script lang="ts">
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  function start(seconds: number) {
    dispatch("start", { seconds });
  }
</script>

<div class="flex gap-2 text-gray-900">
  <button on:click={() => start(60)} class="rounded bg-gray-100 px-4 py-2">
    1m
  </button>
  <button on:click={() => start(300)} class="rounded bg-gray-100 px-4 py-2">
    5m
  </button>
  <button on:click={() => start(900)} class="rounded bg-gray-100 px-4 py-2">
    15m
  </button>
  <button on:click={() => start(1800)} class="rounded bg-gray-100 px-4 py-2">
    30m
  </button>
</div>

<script lang="ts">
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  function start(seconds: number) {
    dispatch("start", { seconds });
  }
</script>

<div class="flex h-full justify-between gap-4 text-purple-50">
  <button
    on:click={() => start(60)}
    class="w-full bg-purple-950/70 px-3 py-2 hover:bg-purple-900/70"
  >
    1m
  </button>
  <button
    on:click={() => start(300)}
    class="w-full bg-purple-950/70 px-3 py-2 hover:bg-purple-900/70"
  >
    5m
  </button>
  <button
    on:click={() => start(900)}
    class="w-full bg-purple-950/70 px-3 py-2 hover:bg-purple-900/70"
  >
    15m
  </button>
  <button
    on:click={() => start(1800)}
    class="w-full bg-purple-950/70 px-3 py-2 hover:bg-purple-900/70"
  >
    30m
  </button>
</div>

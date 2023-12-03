<script lang="ts">
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  export let loadingSeconds: number;
  let progress = 0;

  const interval = setInterval(() => {
    progress += 1;
    if (progress === 100) {
      clearInterval(interval);
      dispatch("complete");
    }
  }, loadingSeconds * 10);
</script>

<div class="h-4 w-96 overflow-hidden rounded bg-gray-300">
  <div
    class="h-4 bg-red-300 duration-1000 ease-linear"
    style="width: {progress}%"
  ></div>
</div>

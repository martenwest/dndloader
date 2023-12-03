<script lang="ts">
  import type { ComponentEvents } from "svelte";
  import LoaderBar from "./loader-bar.svelte";
  import LoaderHint from "./loader-hint.svelte";
  import LoaderInput from "./loader-input.svelte";

  let status: "idle" | "loading" | "complete" = "idle";
  let loadingSeconds = 0;

  function handleStart(event: ComponentEvents<LoaderInput>["start"]) {
    status = "loading";
    loadingSeconds = event.detail.seconds;
  }

  function handleComplete() {
    status = "complete";
    loadingSeconds = 0;
  }

  function handlePlay() {
    status = "idle";
  }
</script>

<div class="fixed flex h-screen w-screen justify-center">
  <div
    class="absolute flex h-48 w-full flex-col justify-between self-end bg-black/80 px-96 py-8 text-white"
  >
    {#if status === "idle"}
      <LoaderInput on:start={handleStart} />
    {:else}
      <div>
        <LoaderHint />
      </div>
      <div class="flex justify-center">
        {#if status === "complete"}
          <button
            class="w-96 bg-purple-950/70 px-4 py-2 text-purple-50 hover:bg-purple-900/70"
            on:click={handlePlay}
          >
            Play
          </button>
        {:else}
          <LoaderBar {loadingSeconds} on:complete={handleComplete} />
        {/if}
      </div>
    {/if}
  </div>
</div>

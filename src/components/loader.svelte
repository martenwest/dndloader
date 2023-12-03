<script lang="ts">
  import type { ComponentEvents } from "svelte";
  import LoaderBar from "./loader-bar.svelte";
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

<div class="fixed flex h-screen w-screen justify-center p-4">
  {#if status === "idle"}
    <div class="absolute">
      <LoaderInput on:start={handleStart} />
    </div>
  {:else if status === "loading"}
    <div class="absolute self-center">
      <LoaderBar {loadingSeconds} on:complete={handleComplete} />
    </div>
  {:else if status === "complete"}
    <div class="absolute self-center">
      <button class="rounded bg-gray-100 px-4 py-2" on:click={handlePlay}>
        Play
      </button>
    </div>
  {/if}
</div>

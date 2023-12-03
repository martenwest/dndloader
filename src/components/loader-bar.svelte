<script lang="ts">
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  export let loadingSeconds: number;
  let progress = 0;
  let index = 0;

  const possibleProgressSteps = [
    1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 2, 0, 2, 0, 2, 0, 2, 0, 2, 0, 2, 0, 2, 0, 2,
    0, 2, 0, 2, 0, 2, 0, 2, 0, 2, 0, 2, 0, 2, 0, 3, 0, 0, 3, 0, 0, 3, 0, 0, 3,
    0, 0, 3, 0, 0, 3, 0, 0, 3, 0, 0, 3, 0, 0, 3, 0, 0, 3, 0, 0, 4, 0, 0, 0, 4,
    0, 0, 0, 4, 0, 0, 0, 4, 0, 0, 0, 4, 0, 0, 0, 5, 0, 0, 0, 0, 5, 0, 0, 0, 0,
  ];

  function shuffle(array: number[]) {
    let currentIndex = array.length,
      randomIndex;

    while (currentIndex != 0) {
      randomIndex = Math.floor(Math.random() * currentIndex);
      currentIndex--;

      [array[currentIndex], array[randomIndex]] = [
        array[randomIndex],
        array[currentIndex],
      ];
    }

    return array;
  }

  const shuffledProgressSteps = shuffle(possibleProgressSteps);

  const interval = setInterval(() => {
    progress += shuffledProgressSteps[index];
    index++;

    if (progress === 100) {
      setTimeout(() => {
        clearInterval(interval);
        dispatch("complete");
      }, 400);
    }
  }, loadingSeconds * 10);
</script>

<div class="h-6 w-full bg-black/70">
  <div
    class="h-6 bg-purple-950/70 duration-200 ease-linear"
    style="width: {progress}%"
  ></div>
</div>

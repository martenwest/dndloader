<script lang="ts">
  import hints from "../data/hints.json";

  const FIFTEEN_SECONDS = 15000;

  let hint = hints[Math.floor(Math.random() * hints.length)];

  function refreshHint() {
    const newHint = hints[Math.floor(Math.random() * hints.length)];
    if (newHint === hint) {
      refreshHint();
      return;
    }
    hint = hints[Math.floor(Math.random() * hints.length)];
  }

  setInterval(() => {
    refreshHint();
  }, FIFTEEN_SECONDS);
</script>

<div class="text-center text-xl">
  {hint}
</div>

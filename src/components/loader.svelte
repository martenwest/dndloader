<script>
    let progress = 0;

    const interval = setInterval(() => {
        progress += 1;
        if (progress === 100) {
            clearInterval(interval);
        }
    }, 20);
</script>

<div class="fixed h-screen w-screen flex items-center justify-center">
    <div class="w-96 h-4 bg-gray-300">
        <div class="h-4 bg-red-300" style="width: {progress}%"></div>
    </div>
</div>

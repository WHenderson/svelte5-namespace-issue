<script>
    let { children, width, height } = $props();

    let clientWidth = $state();
    let clientHeight = $state();
</script>
<svg bind:clientWidth bind:clientHeight {width} {height}>
    {@render children?.({ color: 'green', n: 12 })}
</svg>
<pre>{JSON.stringify({clientWidth,clientHeight})}</pre>
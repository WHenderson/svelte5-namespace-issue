<script lang="ts">
    let { children, width, height, ...props } = $props();

    let clientWidth = $state();
    let clientHeight = $state();
</script>
<svg bind:clientWidth bind:clientHeight {width} {height} {...props}>
    {@render children?.({ color: 'green', n: 10 })}
</svg>
<pre>{JSON.stringify({clientWidth,clientHeight})}</pre>
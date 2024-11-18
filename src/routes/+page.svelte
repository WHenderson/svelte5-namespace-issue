<script lang="ts">
    import Svg from "./Svg.svelte";

    let namespace = $state();
    function ns(node) {
        namespace = node.namespaceURI;
    }
</script>
<div>
    <Svg width={100} height={100}>
        {#snippet children({color, n})}
            {@const cx = 50}
            {@const cy = 50}
            {@const arr = Array.from(new Array(5), (_, i) => ({ r: i + 1 })).reverse()}
            {#each arr as {r}}
                <circle {cx} {cy} r={r*n} fill="black" stroke={color} stroke-width={1} class="ssdgyzzda" use:ns/>
            {/each}
        {/snippet}
    </Svg>
</div>
<pre>{namespace}</pre>
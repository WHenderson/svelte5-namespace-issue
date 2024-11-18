<script>
    import Svg from "./Svg.svelte";

    let namespace = $state();
    function ns(node) {
        namespace = node.namespaceURI;
    }
</script>
<div>
    <Svg width={100} height={100}>
        {#snippet children({color, n})}
            {@const cx = 5*n}
            {@const cy = 5*n}
            {@const r = 2.5*n}
            <circle {cx} {cy} {r} fill="black" stroke={color} stroke-width={1} class="xyzzdassdfsasfds" use:ns/>
        {/snippet}
    </Svg>
</div>
<pre>{namespace}</pre>
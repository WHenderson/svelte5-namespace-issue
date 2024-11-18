<script lang="ts">

    import Svg from './Svg.svelte';

    const data = $state([
        { year: '2015', apples: 1 },
        { year: '2016', apples: 10 },
        { year: '2017', apples: 12 },
        { year: '2018', apples: 5 },
        { year: '2019', apples: 2 }
    ]);

    let sort = $state(false);

    // eslint-disable-next-line @typescript-eslint/no-explicit-any
    function stringify(value: any) {
        return JSON.stringify(
            value,
            (key, value) => {
                if (value instanceof Set)
                    return [...value];
                return value;
            },
            2
        )
    }

    let namespace = $state(new Map());

    function ns(node: Element) {
        namespace = new Map([...namespace, [node, node.namespaceURI]]);
        console.log(node.namespaceURI, namespace);
    }
</script>
<input bind:checked={sort} type="checkbox" />
<input bind:value={data[2].year} />
<input bind:value={data[2].apples} type="number"/>

<div>
    <Svg>
        {#snippet children()}
            {@const scaled = [{x: 50,y: 50}]}

            {#each scaled as { x, y }}
                <circle cx={x} cy={y} r={5} class="ssdfasdfasdff" use:ns />
            {/each}

        {/snippet}
    </Svg>
</div>
<pre>{JSON.stringify([...namespace.values()], null, 2)}</pre>

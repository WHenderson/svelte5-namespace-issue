<script lang="ts">
    import type { Snippet } from 'svelte';
    import type { SVGAttributes } from 'svelte/elements';

    type Props =
        Omit<Partial<SVGAttributes<SVGSVGElement>>, 'children'> &
        {
            width?: number | undefined,
            height?: number | undefined,
            children?: Snippet
        };

    let { children, ...props }: Props = $props();

    let clientWidth = $state(props.width ?? 0);
    let clientHeight = $state(props.height ?? 0);

</script>
<svg bind:clientWidth bind:clientHeight {...props}>
    {@render children?.()}
</svg>
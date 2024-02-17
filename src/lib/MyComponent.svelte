<script>
    import { navigating } from "$app/stores"
    import MyInnerComponent from './MyInnerComponent.svelte'
    import { onDestroy, onMount } from "svelte"

    navigating.subscribe(navigatingValue => {
        console.log('navigating changed: ', navigatingValue)
    })

    export let delay = 250

    let timeoutId
    let delayedPreloading = false

    onMount(() => {
        navigating.subscribe(navigatingValue => {
            clearTimeout(timeoutId)
            timeoutId = setTimeout(() => {
                delayedPreloading = !!navigatingValue
            }, delay)
        })
    })

    onDestroy(() => {
        clearTimeout(timeoutId)
    })
</script>

<p>Hello from MyComponent.svelte</p>

{#if delayedPreloading}
aaa
{/if}

<MyInnerComponent />

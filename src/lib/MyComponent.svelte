<script>
    import { navigating } from "$app/stores"
    import MyInnerComponent from './MyInnerComponent.svelte'

    navigating.subscribe(navigatingValue => {
        console.log('navigating changed: ', navigating)
    })
</script>

<p>Hello from MyComponent.svelte</p>

<MyInnerComponent />

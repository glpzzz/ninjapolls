<script>

    // import {onMount, onDestroy} from 'svelte';

    import Card from "../shared/Card.svelte";
    import PollDetails from "./PollDetails.svelte";

    import PollStore from "../stores/PollStore";

    export let polls = [];

</script>

<section class="poll-list">
    {#each $PollStore as poll (poll.id)}
        <Card>
            <PollDetails {poll} on:vote/>
        </Card>
    {/each}
</section>

<style>

    .poll-list {
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 20px;
    }

</style>

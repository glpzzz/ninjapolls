<script>

    import Card from "../shared/Card.svelte";
    import PollDetails from "./PollDetails.svelte";

    export let polls = [];
</script>

<section class="poll-list">
    {#each polls as poll (poll.id)}
        <Card>
            <PollDetails {poll}/>
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

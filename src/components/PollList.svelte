<script>
    export let polls = [];
</script>

<section class="poll-list">
    {#each polls as poll (poll.id)}
        <article>
            <h2>{poll.question}</h2>
        </article>
    {/each}
</section>

<style>

    .poll-list {
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 20px;
    }

</style>

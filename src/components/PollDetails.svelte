<script>

    import {createEventDispatcher} from "svelte";

    export let poll = null;

    const dispatch = createEventDispatcher();

    // reactive values
    $: totalVotes = poll.votesA + poll.votesB;
    $: widthA = Math.floor(poll.votesA * 100 / totalVotes);
    $: widthB = Math.floor(poll.votesB * 100 / totalVotes);

    // handling the votes
    const handleVote = (option, id) => {
        dispatch('vote', {
            option,
            id,
        });
    }

</script>

<article>
    <h2>{poll.question}</h2>
    <p>Total votes: {totalVotes}</p>
    <div class="answer" on:click={() => handleVote('a', poll.id)}>
        <div class="percent percent-a" style="width: {widthA}%"></div>
        <span>{poll.answerA} ({poll.votesA})</span>
    </div>
    <div class="answer" on:click={() => handleVote('b', poll.id)}>
        <div class="percent percent-b" style="width: {widthB}%"></div>
        <span>{poll.answerB} ({poll.votesB})</span>
    </div>
</article>

<style>

    h2 {
        margin: 0 auto;
        color: #555;
    }

    p {
        margin-top: 6px;
        font-size: 14px;
        color: #aaa;
        margin-bottom: 30px;
    }

    .answer {
        background: #fafafa;
        cursor: pointer;
        margin: 10px auto;
        position: relative;
    }

    .answer:hover {
        opacity: 0.6;
    }

    span {
        display: inline-block;
        padding: 10px 20px;
    }

    .percent {
        height: 100%;
        position: absolute;
        box-sizing: border-box;
        border-left: 4px solid;
    }

    .percent-a {
        background: rgba(217, 27, 66, 0.2);
        border-left-color: #d91b42;
    }

    .percent-b {
        background: rgba(69, 196, 150, 0.2);
        border-left-color: #45c496;
    }

</style>

<script>

    import Header from './components/Header.svelte';
    import Footer from './components/Footer.svelte';
    import PollList from './components/PollList.svelte';
    import CreatePollForm from './components/CreatePollForm.svelte';
    import Tabs from './shared/Tabs.svelte';

    // tabs
    let items = [
        'Current Polls',
        'Add New Poll',
    ];
    let activeItem = items[0];

    const tabsChanged = (e) => {
        activeItem = e.detail.item;
        console.log(activeItem);
    };

    let polls = [
        {
            id: 1,
            question: 'Python or JavaScript?',
            answerA: 'Python',
            answerB: 'JavaScript',
            votesA: 9,
            votesB: 15,
        },
        {
            id: 2,
            question: 'Python or JavaScript?',
            answerA: 'Python',
            answerB: 'JavaScript',
            votesA: 9,
            votesB: 15,
        }
    ];

    const createPollFormCreated = (e) => {
        console.log(e.detail.poll);
        polls = [...polls, e.detail.poll];
        activeItem = items[0];
    }

</script>

<Header/>
<main>
    <Tabs {items} {activeItem} on:Tabs.change={tabsChanged}/>
    {#if activeItem === items[0]}
        <PollList {polls} />
    {:else if activeItem === items[1]}
        <CreatePollForm on:created={createPollFormCreated}/>
    {/if}
</main>
<Footer/>

<style>
    main {
        max-width: 960px;
        margin: 40px auto;
    }
</style>

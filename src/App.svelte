<script>

    import Header from './components/Header.svelte';
    import Footer from './components/Footer.svelte';
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
</script>

<Header/>
<main>
    <Tabs {items} {activeItem} on:Tabs.change={tabsChanged}/>
    {#if activeItem === items[0]}
        <p>list of polls</p>
    {:else if activeItem === items[1]}
        <CreatePollForm />
    {/if}
</main>
<Footer/>

<style>
    main {
        max-width: 960px;
        margin: 40px auto;
    }
</style>

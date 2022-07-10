<script>
    import {createEventDispatcher} from 'svelte';

    const dispatch = createEventDispatcher();

    export let items;
    export let activeItem;

</script>

<div class="tabs">
    <nav>
        <ul>
            {#each items as item}
                <li on:click={() => dispatch('Tabs.change', {item: item})}>
                    <a href="#"
                       class:active={activeItem === item}>
                        {item}
                    </a>
                </li>
            {/each}
        </ul>
    </nav>
</div>

<style>

    .tabs {
        margin-bottom: 40px;
    }

    ul {
        display: flex;
        justify-content: center;
        list-style: none;
        padding: 0;
    }

    li {
        margin: 0 16px;
        font-size: 18px;
        color: #555;
    }

    li > a:hover {
        text-decoration: none;
    }

    .active {
        color: #d91b42;
        border-bottom: 2px solid #d91b42;
        padding-bottom: 8px;
    }
</style>

<script>

    export let type = 'primary';
    export let flat = true;
    export let inverse = false;

</script>

<button class={type} class:flat={flat} class:inverse={inverse}>
    <slot></slot>
</button>

<style>

    button {
        border: 0;
        cursor: pointer;
        border-radius: 6px;
        padding: 8px 12px;
        font-weight: bold;
        box-shadow: 1px 2px 3px rgba(0, 0, 0, 0.2);
    }

    .primary {
        background: #d91b42;
        color: white;
    }

    .primary.inverse {
        background: white;
        color: #d91b42;
        border-color: #d91b42;
    }

    .secondary {
        background: #45c496;
        color: white;
    }

    .secondary.inverse {
        background: white;
        color: #45c496;
        border-color: #45c496;
    }

    .inverse {
        border: 2px solid;
    }

    .flat {
        box-shadow: none;
    }


</style>

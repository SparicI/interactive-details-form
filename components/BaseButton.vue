
<template>
    <button
        :type="buttonType"
        class="form__button"
    >
        <slot />
    </button>
</template>


<script setup>

defineProps({
    buttonType: {
        type: String,
        default: 'button'
    }
})

</script>

<style scoped>
.form__button {
    margin-block-start: var(--spacing-400);
    padding: var(--spacing-300);
    width: min(380px, 100%);

    border-radius: var(--border-radius-soft);
    border: 1px solid var(--very-dark-violet);

    background-color: var(--very-dark-violet);
    color: var(--white);
}

.form__button:hover {
    background-color: var(--very-dark-violet-hover);
}
</style>
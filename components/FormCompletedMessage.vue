<template>
    <div class="completed flex-column">
        <img
            src="/icon-complete.svg"
            alt="Form completed"
            class="completed__icon"
        >
        <div>
            <h2 class="completed__heading margin-block-end-300">Thank you!</h2>
            <p class="completed__description">We've added your card details</p>
        </div>

        <BaseButton button-type="button">Continue</BaseButton>
    </div>
</template>

<script setup>


</script>
<style scoped>
.completed {
    width: min(400px, 100%);
    align-items: center;
    gap: var(--spacing-700);
    text-align: center;
}

.completed__icon {
    max-width: 75px;
}

.completed__heading {
    text-transform: uppercase;
    letter-spacing: 3px;
    color: var(--very-dark-violet);
    font-weight: var(--font-weight-normal);
    font-size: var(--font-size-700);
}

.completed__description {
    color: var(--dark-grayish-violet);
    font-size: var(--font-size-300);
}
</style>
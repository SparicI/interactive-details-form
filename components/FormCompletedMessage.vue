<template>
    <div class="completed">
        <img
            src="/icon-complete.svg"
            alt="Form completed"
            class="completed__icon"
        >
        <h2 class="completed__heading">Thank you!</h2>
        <p class="completed__description">We've added your card details</p>

        <BaseButton button-type="button">Continue</BaseButton>
    </div>
</template>

<script setup>




</script>
<style scoped>
.completed {
    width: min(400px, 100%);
    text-align: center;
}

.completed>* {
    margin-block-end: 2rem;
}
</style>
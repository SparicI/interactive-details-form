<template>
    <form
        @submit.prevent="submit"
        class="form flex-column"
    >
        <div class="form__group flex-column">
            <label
                for="cardholderName"
                class="form__label"
            >
                Cardholder name
            </label>
            <input
                id="cardholderName"
                class="form__input"
                type="text"
                name="cardholderName"
                v-model="form.cardholderName"
                placeholder=" e.g. Jane Appleseed"
            />
        </div>

        <div class="form__group flex-column">
            <label
                for="cardNumber"
                class="form__label"
            >
                Card number
            </label>
            <input
                id="cardNumber"
                class="form__input"
                type="text"
                name="cardNumber"
                v-model="form.cardNumber"
                placeholder="e.g. 1234 5678 9123 0000"
            />
        </div>

        <div class="flex-row">
            <div class="form__group flex-column width-50">
                <label
                    for="number"
                    class="form__label"
                >
                    Exp. date (mm/yy)
                </label>
                <div class="flex-row">
                    <input
                        id="month"
                        class="form__input"
                        type="text"
                        name="month"
                        v-model="form.month"
                        placeholder="MM"
                    />
                    <input
                        id="year"
                        class="form__input"
                        type="text"
                        name="year"
                        v-model="form.year"
                        placeholder="YY"
                    />
                </div>
            </div>

            <div class="form__group flex-column width-50">
                <label
                    for="cvc"
                    class="form__label"
                >
                    Cvc
                </label>
                <input
                    id="cvc"
                    class="form__input"
                    type="number"
                    name="cvc"
                    v-model="form.cvc"
                    placeholder="e.g. 123"
                />
            </div>
        </div>

        <button
            type="submit"
            class="form__button"
        >Confirm</button>
    </form>
</template>

<script setup>

const form = useState('form', () => ({
    cardholderName: '',
    cardNumber: '',
    month: '',
    year: '',
    cvc: ''
}))


</script>
<style scoped>
.form {
    max-width: 400px;
    gap: var(--spacing-400);
    padding-inline: var(--spacing-600);
}

.form__label {
    font-size: var(--font-size-200);
    text-transform: uppercase;
    letter-spacing: 2px;
}

.form__input {
    padding: var(--spacing-200);
    border: 1.4px solid var(--light-grayish-violet);
    border-radius: var(--border-radius-soft);
    width: 100%;
}

.form__input::placeholder {
    font-size: var(--font-size-400);
    color: var(--dark-grayish-violet);
    font-weight: var(--font-weight-bold);
    opacity: 0.37;
}

.form__button {
    margin-block-start: var(--spacing-400);
    padding: var(--spacing-300);
    border-radius: var(--border-radius-soft);

    background-color: var(--very-dark-violet);
    color: var(--white);
}

@media (min-width: 1024px) {

    .form__input::placeholder {
        font-size: var(--font-size-600);
    }
}
</style>
<template>
    <form
        @submit.prevent="submitForm"
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
                :class="{ error: emptyFieldErrors.includes('cardholderName') }"
                type="text"
                name="cardholderName"
                v-model="form.cardholderName"
                placeholder=" e.g. Jane Appleseed"
                required
                @invalid.prevent="validateField('cardholderName')"
            />
            <div class="error-message">
                <p v-if="emptyFieldErrors.includes('cardholderName')">Can't be blank</p>
            </div>
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
                :class="{ error: emptyFieldErrors.includes('cardNumber') || formErrors.cardNumber }"
                type="text"
                name="cardNumber"
                v-model="form.cardNumber"
                placeholder="e.g. 1234 5678 9123 0000"
                required
                pattern="[0-9 ]+"
                @invalid.prevent="validateField('cardNumber')"
            />
            <div class="error-message">
                <p v-if="emptyFieldErrors.includes('cardNumber')">Can't be blank</p>
                <p v-if="formErrors.cardNumber">Wrong format, numbers only</p>
            </div>
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
                        :class="{ error: emptyFieldErrors.includes('month') || formErrors.month }"
                        type="text"
                        name="month"
                        v-model="form.month"
                        placeholder="MM"
                        required
                        pattern="\d{2}"
                        @invalid.prevent="validateField('month')"
                    />
                    <input
                        id="year"
                        class="form__input"
                        :class="{ error: emptyFieldErrors.includes('year') || formErrors.year }"
                        type="text"
                        name="year"
                        v-model="form.year"
                        placeholder="YY"
                        required
                        pattern="\d{2}"
                        @invalid.prevent="validateField('year')"
                    />
                </div>
                <div class="error-message">
                    <p v-if="emptyFieldErrors.includes('month') || emptyFieldErrors.includes('year')">Can't be blank</p>
                    <p v-if="formErrors.month || formErrors.year">Wrong format, two numbers only</p>

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
                    :class="{ error: emptyFieldErrors.includes('cvc') || formErrors.cvc }"
                    type="text"
                    name="cvc"
                    v-model="form.cvc"
                    placeholder="e.g. 123"
                    required
                    pattern="\d{3}"
                    @invalid.prevent="validateField('cvc')"
                />
                <div class="error-message">
                    <p v-if="emptyFieldErrors.includes('cvc')">Can't be blank</p>
                    <p v-if="formErrors.cvc">Wrong format, three numbers only</p>
                </div>
            </div>
        </div>

        <BaseButton button-type="submit">Confirm</BaseButton>

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

const formCompleted = useState('formCompleted', () => false)

// Empty input fields errors
let emptyFieldErrors = ref([])

// Format input fields errors
let formErrors = ref({
    cardholderName: false,
    cardNumber: false,
    month: false,
    year: false,
    cvc: false
})

// Event listener for invalid events on form input fields
const validateField = (fieldName) => {

    if (form.value[fieldName] === '') {
        // console.log("Empty field", fieldName)
        emptyFieldErrors.value.push(fieldName)
    } else {
        // console.log("Format error", fieldName)
        formErrors.value[fieldName] = true
    }
}

const resetFormErrors = () => {
    formErrors.value.cardholderName = false
    formErrors.value.cardNumber = false
    formErrors.value.month = false
    formErrors.value.year = false
    formErrors.value.cvc = false
}

watch(form.value, (newForm) => {
    // Reset empty field and format errors
    emptyFieldErrors.value = []
    resetFormErrors()
})

const submitForm = () => {

    // Reset empty field and format errors
    emptyFieldErrors.value = []
    resetFormErrors()

    // When formCompleted composable is set to TRUE FormCompletedMessage component renders
    formCompleted.value = true

}


</script>
<style scoped>
.form {
    max-width: 400px;
    gap: var(--spacing-400);
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

.form__input.error {
    border: 1.4px solid var(--input-errors)
}

.form__input:focus,
.form__input:active {
    outline: none;
    border: 1.4px solid var(--active-input-border);
}

.form__input::placeholder {
    font-size: var(--font-size-400);
    color: var(--dark-grayish-violet);
    font-weight: var(--font-weight-bold);
    opacity: 0.37;
}


.error-message {
    color: var(--input-errors);
    font-size: var(--font-size-100);
}

@media (min-width: 1024px) {
    .form__input::placeholder {
        font-size: var(--font-size-600);
    }
}
</style>
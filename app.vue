<template>
  <main class="grid-container">
    <h1 class="visually-hidden">Credit card form</h1>
    <div class="cards-section">
      <div>
        <img
          src="/bg-card-back.png"
          alt="Card back"
          class="card__back"
        >

        <client-only>
          <div class="card__wrapper card__wrapper--back">
            <p class="card__data">{{ data?.cvc === '' ? '000' : data?.cvc }}</p>
          </div>
        </client-only>

      </div>

      <div>
        <img
          src="/bg-card-front.png"
          alt="Card Front"
          class="card__front"
        >
        <div class="card__wrapper card__wrapper--front">
          <img
            src="/card-logo.svg"
            alt="Card logo"
            class="card__logo"
          >
          <div>
            <client-only>
              <p class="card__data card__data--large">{{ data?.cardNumber === '' ? '0000 0000 0000 0000' :
                data?.cardNumber }}
              </p>
            </client-only>
            <div class="flex-row margin-block-start-300 justify-content-space-between">
              <client-only>
                <p class="card__data text-transform-uppercase">{{ data?.cardholderName === '' ? 'Jane Appleseed'
                  :
                  data?.cardholderName }}</p>
              </client-only>
              <client-only>
                <p class="card__data">{{ data?.month === '' ? '00' : data?.month }}/{{ data?.year === '' ? '00'
                  : data?.year
                }}</p>
              </client-only>
            </div>

          </div>
        </div>

      </div>


    </div>
    <div class="form-section">
      <BaseForm v-if="!formCompleted" />
      <FormCompletedMessage v-else />
    </div>
  </main>
</template>

<script setup>

const data = useState('form')
const formCompleted = useState('formCompleted')

</script>

<style scoped>
.grid-container {
  display: grid;
  grid-template-rows: 235px 1fr;
}

.cards-section {
  position: relative;

  background-image: url('/bg-main-mobile.png');
  background-repeat: no-repeat;
  background-size: cover;
}

.form-section {
  display: flex;
  align-items: center;
  justify-content: center;

  padding-block: 5.5rem var(--spacing-400);
  padding-inline: var(--spacing-300);
}

.card__back,
.card__front,
.card__wrapper {
  position: fixed;
  width: 285px;
  height: 160px;
}

.card__wrapper {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: var(--spacing-400);
}

.card__wrapper--back {
  justify-content: center;
  align-items: flex-end;
  padding-inline-end: var(--spacing-900);
}

.card__back,
.card__wrapper--back {
  top: var(--spacing-800);
  right: 50%;
  transform: translateX(50%);
}

.card__front,
.card__wrapper--front {
  top: 7.65rem;
  left: 50%;
  transform: translateX(-50%);
}

.card__data {
  color: var(--white);
  font-size: var(--font-size-100);
  letter-spacing: 1.5px;
}

.card__data--large {
  font-size: var(--font-size-500);
}

.card__logo {
  width: 50px;
}

@media (min-width: 375px) {

  .card__front,
  .card__wrapper--front {
    left: 50%;
    transform: translateX(-70%);
  }
}



@media (min-width: 1024px) {

  .grid-container {
    display: grid;
    grid-template-columns: 30vw 1fr;
    grid-template-rows: auto;
  }

  .cards-section {
    flex: 1;
    background-image: url('/bg-main-desktop.png');
  }


  .card__back,
  .card__front,
  .card__wrapper {
    width: 445px;
    height: 245px;

  }

  .card__front,
  .card__wrapper--front {
    left: 130px;
    top: 50%;
    transform: translateY(-100%);
  }

  .card__back,
  .card__wrapper--back {
    top: 50%;
    transform: translateY(10%);
    left: 200px;
    right: auto;
  }

  .card__wrapper {
    padding-block: var(--spacing-700);
    padding-inline: var(--spacing-800);
  }

  .card__wrapper--back {
    padding-inline-end: var(--spacing-1000);
  }

  .card__data {
    font-size: var(--font-size-400);
  }

  .card__data--large {
    font-size: var(--font-size-1000);
  }

  .card__logo {
    width: 75px;
  }

  .form-section {
    justify-content: flex-end;
  }
}

@media (min-width: 1200px) {
  .form-section {
    padding-inline-end: 20%;
  }
}
</style>
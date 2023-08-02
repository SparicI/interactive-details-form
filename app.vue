<template>
  <main>
    <h1 class="visually-hidden">Credit card form</h1>
    <section class="cards-section">
      <div>
        <img
          src="./assets/images/bg-card-back.png"
          alt="Card back"
          class="card__back"
        >

        <p class="card__data card__data--cvc">{{ data?.cvc === '' ? '000' : data?.cvc }}</p>

      </div>

      <div>
        <img
          src="./assets/images/bg-card-front.png"
          alt="Card Front"
          class="card__front"
        >
        <div class="card__wrapper">
          <img
            src="./assets/images/card-logo.svg"
            alt="Card logo"
            class="card__logo"
          >
          <div>
            <p class="card__data font-size-500">{{ data?.cardNumber === '' ? '0000 0000 0000 0000' : data?.cardNumber }}
            </p>
            <div class="flex-row margin-block-start-300 justify-content-space-between">
              <p class="card__data text-transform-uppercase">{{ data?.cardholderName === '' ? 'Jane Appleseed'
                :
                data?.cardholderName }}</p>
              <p class="card__data">{{ data?.month === '' ? '00' : data?.month }}/{{ data?.year === '' ? '00'
                : data?.year
              }}</p>
            </div>

          </div>
        </div>

      </div>


    </section>
    <section class="form-section">
      <BaseForm />
    </section>
  </main>
</template>

<script setup>

const data = useState('form')

</script>

<style scoped>
.cards-section {
  min-height: 235px;
  position: relative;

  background-image: url('./assets/images/bg-main-mobile.png');
  background-repeat: no-repeat;
  background-size: cover;
}

.form-section {
  display: flex;
  align-items: center;
  justify-content: center;
  padding-block: 5.5rem 1rem;
}

.card__back,
.card__front {
  position: fixed;
  width: 285px;
  height: 160px;
}

.card__back {
  top: 2rem;
  right: 1rem;
}

.card__front {
  top: 7.65rem;
  left: 1rem;
}

.card__data {
  color: var(--white);
  font-size: var(--font-size-100);
  letter-spacing: 1.5px;
}

.card__logo {
  width: 50px;
}

.card__wrapper {
  position: fixed;
  top: 137px;
  left: 33px;
  display: flex;
  flex-direction: column;
  gap: 2.5rem;
}

.card__data--cvc {
  position: fixed;
  top: 103px;
  right: 50px;
}

@media (min-width: 600px) {

  main {
    flex-direction: row;
  }

  .cards-section {
    flex: 1;
    background-image: url('./assets/images/bg-main-desktop.png');
  }


  .card__back,
  .card__front {
    width: 445px;
    height: 245px;
  }
}
</style>
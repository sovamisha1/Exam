<template>
  <div class="donation-container">
    <div class="donate">
      <h1 class="heading">Поддержите наш проект</h1>
      <p class="subheading">
        Если вы хотите помочь проекту, внесите свой вклад.
      </p>
      <div class="donation-form">
        <label for="amount" class="amount-label">Сумма пожертвования:</label>
        <input
          type="number"
          id="amount"
          v-model="donationAmount"
          class="amount-input"
          min="1"
          placeholder="Введите сумму"
        />
        <button @click="donate" class="donate-button">Пожертвовать</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "DonationContent",
  data() {
    return {
      donationAmount: "",
    };
  },
  methods: {
    donate() {
      if (this.donationAmount) {
        alert(
          "Функция пожертвования находится в разработке, но спасибо за готовность помочь!"
        );
        this.donationAmount = "";
      } else {
        alert("Пожалуйста, введите сумму пожертвования.");
      }
    },
  },
};
</script>

<style>
.donation-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  max-width: 600px;
  margin: auto;
  background-color: #b19f9e;
  padding: 40px;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  width: 100%;
}

.heading {
  font-size: 24px;
  text-align: center;
  margin-bottom: 20px;
}

.subheading {
  font-size: 16px;
  text-align: center;
  margin-bottom: 40px;
}

.donation-form {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.amount-label {
  font-size: 18px;
  margin-bottom: 10px;
}

.amount-input {
  font-size: 16px;
  padding: 10px;
  border: 1px solid #cccccc;
  border-radius: 4px;
  margin-bottom: 20px;
  outline: none;
  text-align: left;
}

.donate-button {
  font-size: 16px;
  padding: 10px 20px;
  background-color: #a16e83;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.donate-button:hover {
  background-color: #8a5b6f;
}

.donate-button:focus {
  outline: none;
}
</style>

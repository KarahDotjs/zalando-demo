<script setup>
const props = defineProps({
  productInfos: {
    type: Object,
    required: true
  }
})
</script>

<template>
  <div>
    <div>
      <h2>{{ productInfos.brand }}</h2>
      <h1>{{ productInfos.name }}</h1>
      <p>{{ productInfos.price }}€ <span>TVA incluse</span></p>
      <div class="rate">
        <font-awesome-icon :icon="['fas', 'star']" size="lg" />
        <font-awesome-icon :icon="['fas', 'star']" size="lg" />
        <font-awesome-icon :icon="['fas', 'star']" size="lg" />
        <font-awesome-icon :icon="['fas', 'star']" size="lg" />
        <font-awesome-icon :icon="['fas', 'star-half-alt']" size="lg" />
        <span>{{ productInfos.rate }}</span>
      </div>
      <p class="advise">
        Nous vous recommandaons de choisir une taille au-dessus de celle habituelle
      </p>
      <div class="cart-bloc">
        <button>Ajouter au panier</button>
        <div>
          <font-awesome-icon :icon="['far', 'heart']" />
        </div>
      </div>
    </div>
  </div>
</template>

<style scope>
h1 + p {
  font-size: 22px;
  margin-bottom: 25px;
}
h1 + p span {
  color: #66676e;
  font-size: 14px;
  font-weight: lighter;
}

/*rate bloc*/

.rate {
  margin-bottom: 40px;
}
.rate svg {
  margin-right: 4px;
}
/*advise*/
.advise {
  background-color: #efeff0;
  padding: 20px;
  font-size: 14px;
  line-height: 20px;
  font-weight: lighter;
  margin-bottom: 10px;
}
/* cart-bloc */
.cart-bloc {
  display: flex;
  gap: 10px;
}
.cart-bloc button {
  font-family: inherit;
  font-size: inherit;
  font-weight: bold;
  background-color: var(--main-black);
  color: white;
  flex: 1;
  border: none;
  cursor: pointer;
}
.cart-bloc button:hover {
  opacity: 0.7;
}

.cart-bloc div {
  width: 50px;
  height: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
  border: 2px solid var(--main-black);
  color: var(--main-black);
}

.cart-bloc div:hover {
  border-width: 3px;
}
.cart-bloc svg {
  width: 25px;
  height: 25px;
  cursor: pointer;
}
</style>

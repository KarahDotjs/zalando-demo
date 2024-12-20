<script setup>
const props = defineProps({
  productInfos: {
    type: Object,
    required: true
  },
  selectedVariant: {
    type: Object,
    required: true
  }
})
const isVariantSoldOut = (sizes) => {
  for (const key in sizes) {
    if (sizes[key] > 0) {
      return false
    }
  }
  return true
}

const emit = defineEmits(['changeSelectedVariant', 'addProductToCart'])

const handleEmitNewVariant = (variant) => {
  const isSoldOut = isVariantSoldOut(variant.sizes)

  if (!isSoldOut) {
    emit('changeSelectedVariant', variant)
  }
}

const handleSelectSize = (size, quantity) => {
  const newObj = { ...props.selectedVariant }
  if (quantity > 0) {
    newObj.selectedSize = size

    emit('changeSelectedVariant', newObj)
  }
}
const handleAddToCart = () => {
  if (!props.selectedVariant.selectedSize) {
    alert('Veuillez séléctionner une taille !')
  } else {
    emit('addProductToCart')
  }
}
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
      <p>
        Couleur <span class="selectedColor">{{ selectedVariant.color }}</span>
      </p>

      <div class="img-bloc">
        <img
          v-for="variant in productInfos.variants"
          :src="variant.image.url"
          :alt="variant.image.alt"
          :class="{
            selectedImg: variant.id === selectedVariant.id,
            outOfStock: isVariantSoldOut(variant.sizes)
          }"
          @click="handleEmitNewVariant(variant)"
        />
      </div>

      <p class="advise">
        Nous vous recommandaons de choisir une taille au-dessus de celle habituelle
      </p>
      <div class="sizes-bloc">
        <div
          v-for="(quantity, size) in selectedVariant.sizes"
          :key="size"
          :class="{
            outOfStock: quantity === 0,
            selectedSize: size === selectedVariant.selectedSize
          }"
          @click="handleSelectSize(size, quantity)"
        >
          {{ size }}
        </div>
      </div>
      <div class="cart-bloc">
        <button @click="handleAddToCart">Ajouter au panier</button>
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

.selectedColor {
  font-weight: bold;
}
/* --- image bloc --- */
.img-bloc {
  display: flex;
  gap: 10px;
  margin: 10px 0;
}
.img-bloc img {
  width: 60px;
  height: 70px;
  object-fit: cover;
}
.selectedImg {
  border: 2px solid black;
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

/* --- sizes bloc -- */
.sizes-bloc {
  display: flex;
  gap: 10px;
  padding-bottom: 10px;
}
.sizes-bloc div {
  border: 1px solid black;
  height: 40px;
  width: 40px;
  padding-top: 2px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.outOfStock {
  /* .sizes-bloc */
  opacity: 0.3;
  /* background: yellow; */
}
.sizes-bloc .selectedSize {
  border-width: 2px;
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

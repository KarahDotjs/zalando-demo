<template>
  <header>
    <div class="header-top">
      <div class="container">
        <p>Essayer d'abord, <span>payez après</span></p>
        <p>LIVRAISON & RETOUR <span>GRATUITS*</span></p>
        <p>Retour et remboursement</p>
      </div>
    </div>
    <div class="header-bottom">
      <div class="container">
        <nav>
          <a href="#">Femme</a>
          <a href="#">Homme</a>
          <a href="#">Enfant</a>
        </nav>
        <img src="../assets/img/logo_fcp7ga.svg" alt="logo zalando" />
        <nav>
          <p>Icone 1</p>
          <p>Icone 2</p>
          <p>Icone 3</p>
        </nav>
      </div>
    </div>
  </header>
</template>

<style scoped>
.header-top {
  background-color: var(--light-grey);
}
.header-top .container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: var(--header-top-height);
  color: var(--dark-grey);
}
span {
  color: var(--main-orange);
}
/* --------------------------------------------- */
.header-bottom {
  border-bottom: var(--header-bottom-height);
}

.header-bottom {
  border-bottom: 1px solid #d0d1d3;
}

.header-bottom .container {
  height: var(--header-bottom-height);
  display: flex;
  justify-content: space-between;
  align-items: center;
}

img {
  width: 155px;
  cursor: pointer;
  /* border: 1px solid green; */
}
nav {
  display: flex;
  flex: 1;
  gap: 10px;
  /* border: 1px solid green; */
}
nav:last-of-type {
  justify-content: flex-end;
}
a {
  
  color: inherit;
  font-weight: bold;
  padding: 10px 15px;
}
a:first-child {
  background: var(--main-black);
  color: #fff;
}
</style>

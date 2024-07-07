<script setup>
import { ref } from "vue";

function getRandomNumber(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

function fixName(word) {
  const firstLetter = word.charAt(0);
  const upperFirst = firstLetter.toUpperCase();

  const preName = word.replace(firstLetter, "");
  const fixedName = `${upperFirst}${preName}`;

  return fixedName;
}

const pokname = ref("");
const pokimage = ref("");

function obtainPokemon() {
  const pokemon = `https://pokeapi.co/api/v2/pokemon/${getRandomNumber(
    1,
    1008
  )}`;

  fetch(pokemon).then(async (res) => {
    const response = await res.json();

    pokname.value = fixName(response.name);
    pokimage.value = response.sprites.front_default;
  });
}
function click() {
  obtainPokemon();
}
obtainPokemon();
</script>
<template>
  <section class="pokemon">
    <article class="pokemon__info">
      <h2 class="pokemon__name">{{ pokname }}</h2>
      <img class="pokemon__image" :src="pokimage" />
    </article>
    <button class="pokemon__button" @click="click">Boton</button>
  </section>
</template>

<style scoped>
.pokemon {
  display: flex;
  align-items: center;
  gap: 3em;
}
.pokemon__info {
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.pokemon__name {
  font-size: 2.0625rem;
  text-align: center;
}
.pokemon__button {
  width: 5em;
  height: 5em;
  background-color: brown;
  border: none;
  transition: all 0.3s ease-in-out;
}

.pokemon__button:hover {
  scale: 1.3;
  cursor: pointer;
}

.pokemon__image {
  width: 10em;
}
</style>

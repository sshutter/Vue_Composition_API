<template>
  <div class="home">
    <h1>Home</h1>
    <h2>Refs</h2>
    <p>{{ ninjaOne.name }} - {{ ninjaOne.age }}</p>
    <button @click="updateNinjaOne">Update ninja one</button>
    <h2>Reactive</h2>
    <p>{{ ninjaTwo.name }} - {{ ninjaTwo.age }}</p>
    <button @click="updateNinjaTwo">Update ninja two</button>
  </div>
</template>

<script>
import { ref, reactive } from "vue";

export default {
  name: "HomeView",
  setup() {
    // const pRef = ref(null);

    const ninjaOne = ref({ name: "mario", age: 30 });
    const ninjaTwo = reactive({ name: "luigi", age: 35 });

    // NOTE Reactive cannot change the primitive value,
    // but ref can ( The positive about ref )
    const nameOne = ref("mario");
    const nameTwo = reactive("luigi");

    const updateNinjaOne = () => {
      ninjaOne.value.age = 40;
    };

    // NOTE: The difference about ref and reactive is
    // the reactive didn't need .value to access the value of constance
    const updateNinjaTwo = () => {
      ninjaTwo.age = 45;
    };

    return {
      ninjaOne,
      updateNinjaOne,
      ninjaTwo,
      updateNinjaTwo,
      nameOne,
      nameTwo,
    };
  },
};
</script>

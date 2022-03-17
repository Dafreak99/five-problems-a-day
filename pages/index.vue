<template>
  <div class="w-screen h-screen bg-blue-700 flex justify-center items-center">
    <div class="bg-white py-12 px-16 shadow-md rounded-md">
      <ul>
        <li
          v-for="(problem, index) in problems"
          :key="problem.name"
          class="text-xl mb-4"
        >
          {{ `${index + 1}. ${problem.name}` }} -
          <span
            ><a
              :href="problem.url"
              target="_blank"
              class="inline-block py-2 px-6 bg-gray-400 text-white rounded-xl cursor-pointer hover:bg-gray-700 duration-300"
              >Open</a
            ></span
          >
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import fixture from "../fixture.js";

export default {
  name: "IndexPage",
  mounted() {},
  computed: {
    indices() {
      let indices = [];
      while (indices.length < 5) {
        let index = this.randomIntFromInterval(0, fixture.questions.length - 1);
        if (!indices.includes(index)) {
          indices.push(index);
        }
      }

      return indices;
    },
    problems() {
      return this.indices.map((index) => fixture.questions[index]);
    },
  },
  methods: {
    randomIntFromInterval(min, max) {
      return Math.floor(Math.random() * (max - min + 1) + min);
    },
  },
};
</script>

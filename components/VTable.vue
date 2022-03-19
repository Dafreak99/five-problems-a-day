<template>
  <div>
    <h3 class="text-3xl mb-8">Today's Problems</h3>
    <vs-table v-model="selected" class="theme">
      <template #thead>
        <vs-tr>
          <vs-th> Name </vs-th>
          <vs-th> Difficulty </vs-th>
          <vs-th> Category </vs-th>
          <vs-th> Action </vs-th>
        </vs-tr>
      </template>
      <template #tbody>
        <vs-tr
          :key="i"
          v-for="(tr, i) in problems"
          :data="tr"
          :is-selected="!!selected.includes(tr)"
        >
          <vs-td>
            {{ tr.name }}
          </vs-td>
          <vs-td class="capitalize">
            <div
              class="badge"
              :class="
                tr.difficulty === 'easy'
                  ? 'success'
                  : tr.difficulty === 'medium'
                  ? 'warning'
                  : 'danger'
              "
            >
              {{ tr.difficulty }}
            </div>
          </vs-td>
          <vs-td>
            {{ tr.type }}
          </vs-td>
          <vs-td>
            <a :href="tr.url" target="__blank"><external-link-icon /></a>
          </vs-td>
        </vs-tr>
      </template>
    </vs-table>
  </div>
</template>

<script>
import { CheckCircleIcon, ExternalLinkIcon } from "vue-feather-icons";
import fixture from "@/fixture.js";

export default {
  name: "v-table",
  components: {
    CheckCircleIcon,
    ExternalLinkIcon,
  },
  data: () => ({
    allCheck: false,
    selected: [],
    problems: [],
  }),
  methods: {
    randomIntFromInterval(min, max) {
      return Math.floor(Math.random() * (max - min + 1) + min);
    },
  },
  mounted() {
    let indices = [];

    while (indices.length < 5) {
      let index = this.randomIntFromInterval(0, fixture.questions.length - 1);

      if (!indices.includes(index)) {
        indices.push(index);
      }
    }

    this.problems = indices.map((index) => fixture.questions[index]);
  },
};
</script>

<style>
.check-icon:hover {
  @apply text-green-400 duration-300;
}
</style>

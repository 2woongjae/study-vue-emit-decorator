<template>
  <div>
    <h1>{{ count }}</h1>
    <p>
      <button v-on:click="addToCount(1)">addToCount</button>
    </p>
    <p>
      <button @click="resetCount">resetCount</button>
    </p>
    <p>
      <button @click="returnValue">returnValue</button>
    </p>
    <p>
      <button @click="promise">promise</button>
    </p>
    <p>
      <button @click="test(10)">test</button>
    </p>
  </div>
</template>

<script lang="ts">
import { Vue, Component, Emit } from "vue-property-decorator";

@Component
export default class EmitTest extends Vue {
  count = 0;

  @Emit()
  addToCount(n: number) {
    this.count += n;
  }

  @Emit("reset")
  resetCount() {
    this.count = 0;
  }

  @Emit()
  returnValue() {
    return 10;
  }

  @Emit()
  promise() {
    return new Promise(resolve => {
      setTimeout(() => {
        resolve(20);
      }, 0);
    });
  }

  @Emit()
  test(n: number) {
    this.count = n;
    return 0;
  }
}
</script>


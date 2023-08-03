<template>
  <div class="home">
    <h2>{{ appTitle }}</h2>
    <h3>{{ counterData.title }}:</h3>

    <div>
      <button @click="decreaseCounter(2)" class="btn">--</button>
      <button @click="decreaseCounter(1)" class="btn">-</button>
      <span class="counter">{{ counterData.count }}</span>
      <button @click="increaseCounter(1, $event)" class="btn">+</button>
      <button @click="increaseCounter(2)" class="btn">++</button>
    </div>

    <p>This counter is {{ oddOrEven }}.</p>

    <div class="edit">
      <h4>Edit counter title:</h4>
      <input v-model="counterData.title" type="text" />
    </div>
  </div>
</template>

<script setup>
// Import

import {
  reactive,
  computed,
  watch,
  onMounted,
} from "vue";

// Title
const appTitle = "My Ok Counter App";

onMounted(() => {
  console.log("Do some stuff related to title.")
});

// Counter
const counterData = reactive({
  count: 0,
  title: "My Counter",
});

watch(
  () => counterData.count,
  (newCount, oldCount) => {
    if (newCount === 20) {
      alert("20!!!");
    }
  }
);

const oddOrEven = computed(() => {
  if (counterData.count % 2 === 0) return "even";
  return "odd";
});

const increaseCounter = (amount, e) => {
  counterData.count += amount;
};

const decreaseCounter = (amount) => {
  counterData.count -= amount;
};

onMounted(() => {
  console.log("Do some stuff related to counter.")
});

</script>

<!--
 
<script>
export default {
  data() {
   return {
    count: 0
   }
  },
  computed: {
    myComputedProperty() {
      // perform some logic based on data property
      return "my result"
    }
  },
  watch: {
    count(newCount, oldCount) {
      if (newCount === 20) alert("car")
    }
  },
  mounted() {
    // do staff when the component is loaded,
    console.log("mounted")
  },
  unmounted() {
    // do staff when the component is unloaded
    console.log("unmounted")
  }
}
</script>
 -->

<!--
<script>
import { ref } from "vue";

export default {
  setup() {
    const counter = ref(0);

    const increaseCounter = () => {
      counter.value++;
    };
    
    const decreaseCounter = () => {
      counter.value--;
    };

    return {
      counter,
      increaseCounter,
      decreaseCounter
    }
  }
}
</script>
-->

<!--
<script>
export default {
  data() {
    return {
      counter: 0
    }
  },
  methods: {
    increaseCounter() {
      this.counter++;
    },
    decreaseCounter() {
      this.counter--;
    }
  }
}
</script>
-->

<style>
.home {
  text-align: center;
  padding: 20px;
}

.btn,
.counter {
  font-size: 40px;
  margin: 10px;
}

.edit {
  margin-top: 60px;
}
</style>

<template>
  <div class="home">
    <transition name="toast">
      <Toast v-if="showToast" />
      <!-- <div v-if="showP">Hello ninjas</div> -->
    </transition>

    <Todos @badValue="triggerToast" />

    <!-- <button @click="showP = !showP">toggle</button> -->
  </div>
</template>

<script>
import { ref } from "vue";
import Toast from "../components/Toast";
import Todos from "../components/Todos";

export default {
  components: { Toast, Todos },
  setup() {
    const showToast = ref(false);
    // const showP = ref(false);

    const triggerToast = () => {
      showToast.value = true;
      setTimeout(() => (showToast.value = false), 3000);
    };

    return { showToast, triggerToast };
  },
};
</script>

<style>
/*enter class*/
.toast-enter-from {
  opacity: 0;
  transform: translateY(-60px);
}
/* enter-to default state so no need code out  */
.toast-enter-to {
  opacity: 1;
  transform: translateY(0);
}

.toast-enter-active {
  transition: all 0.3s ease;
}
/*leave class*/
/* leave-from default state so no need code out  */
.toast-leave-from {
  opacity: 1;
  transform: translateY(0);
}

.toast-leave-to {
  opacity: 0;
  transform: translateY(-60px);
}

.toast-leave-active {
  transition: all 0.3s ease;
}

/* .fade-enter-from {
  opacity: 0;
}

/* default state so no need code out  */
/* .fade-enter-to {
  opacity: 1;
} */

/* .fade-enter-active {
  transition: all 2s ease;
} */
/* default state so no need code out  */
/* .fade-leave-from {
  opacity: 1;
} */

/* .fade-leave-to {
  opacity: 0;
} */

/* .fade-leave-active {
  transition: all 2s ease;
} */
</style>
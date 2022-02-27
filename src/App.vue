<template>
  <AdviceGeneratorApp />
</template>

<script>
import AdviceGeneratorApp from "./components/AdviceGeneratorApp.vue";

export default {
  name: "App",
  components: {
    AdviceGeneratorApp,
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Manrope:wght@800&display=swap");

:root {
  --dark-blue: hsl(218, 37%, 20%);
  --light-cyan: hsl(193, 38%, 86%);
  --neon-green: hsl(150, 100%, 66%);
  --grayish-blue: hsl(217, 19%, 38%);
  --dark-grayish-blue: hsl(217, 19%, 24%);
}
* {
  box-sizing: border-box;
  font-family: "Manrope";
  font-weight: 800;
  text-align: center;
}

body {
  margin: 0;
}
</style>

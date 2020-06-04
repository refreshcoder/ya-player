<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <Player></Player>
  </div>
</template>

<script>
// @ is an alias to /src

import Player from "@/components/Player.vue"
export default {
  components: {
    Player
  }
}
</script>

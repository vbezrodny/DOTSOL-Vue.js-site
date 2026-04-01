<script setup>
  components: { Vheader }
  components: { Vflashcards }
components: { Vfooter }
components: { Vfeedback }
components: { Vtech }
components: { Vprojects }
components: { Vpromo }
import Vfooter from "./components/VFooter.vue";
import Vfeedback from "./components/Vfeedback.vue";
import Vpromo from "./components/Vpromo.vue";
import Vprojects from "./components/Vprojects.vue";
import Vtech from "./components/Vtech.vue";
import Vflashcards from "./components/Vflashcards.vue"
import Vheader from "./components/Vheader.vue"
  
</script>

<template>
    <vheader/>
    <main>
        <vpromo/>
        <vflashcards/>
        <vprojects/>
        <vtech/>
        <vfeedback/>
    </main>
    <vfooter/>
</template>

<style scoped>

</style>
 
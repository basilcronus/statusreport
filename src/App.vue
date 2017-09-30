<template>
  <div>
    <app-header></app-header>
    <add-report></add-report>
    <app-footer></app-footer>
  </div>
</template>

<script>
import addReport from './components/addReport.vue'
import header from './components/header.vue'
import footer from './components/footer.vue'
export default {
  components: {
    'add-report': addReport,
    'app-header': header,
    'app-footer': footer
  },
  data() {
    return {

    }
  }
}
</script>

<style>

</style>

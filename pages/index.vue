<template>
  <div>
    <div class="mb-3">
      <b-form inline>
        <label class="sr-only" for="brand-name">Name</label>
        <b-input
          id="brand-name"
          v-model="brandName"
          class="mb-2 mr-sm-2 mb-sm-0"
          placeholder="銘柄名: pets"
        />
        <b-button
          variant="primary"
          @click="getData"
        >
          Save
        </b-button>
      </b-form>
    </div>
    <b-table striped hover :items="items" />
  </div>
</template>

<script>
export default {
  data () {
    return {
      brandName: '',
      items: []
    }
  },
  methods: {
    async getData () {
      const response = await this.$axios.$get(`http://localhost/theme/${this.brandName}`)
      this.items = response.result
    }
  }
}
</script>

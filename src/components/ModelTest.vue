<template>
  <div>
    <p>{{ checked ? 'ON' : 'OFF' }}</p>
    <p><button @click="changed">토글</button></p>
  </div>
</template>

<script lang="ts">
  import {Vue, Component, Model, Prop} from 'vue-property-decorator'

  @Component
  export default class ModelTest extends Vue {
    @Prop()
    @Model('change')
    readonly checked!: boolean

    changed() {
      this.$emit('change', !this.checked)
    }
  }
</script>
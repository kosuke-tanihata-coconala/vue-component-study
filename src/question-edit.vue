<template>
  <div>
    <span
      v-if="!isEditing"
      @click="openEditArea"
    >{{ value }}</span>
    <textarea
      v-else
      @blur="applyParent"
      class="form-control"
      type="text"
      v-model="value"
      ref="ref"
      rows="3"
    ></textarea>
  </div>
</template>
<script>
  export default {
    props: {
      initialValue: {
        type: String,
        required: true
      },
      contentKey: {
        type: String,
        required: true
      }
    },
    data() {
      return {
        value: this.initialValue,
        isEditing: false
      }
    },
    methods: {
      openEditArea(){
        this.isEditing = true;
        this.$nextTick(function () { this.$refs.ref.focus() });
      },
      applyParent() {
        this.isEditing = false;
        this.$emit('child-update', { [this.contentKey]: this.value} );
      }
    }
  }
</script>
<style>

</style>

<template>
  <div class="form-group" :class="{'has-error': error}" v-on="listeners">
    <label v-if="label" :for="name">{{label}}</label>
    <input :name="name" v-model="value" :placeholder="placeholder" />
    <span v-if="error" class="help-block">{{error}}</span>
  </div>
</template>

<script>
export default {
  name: "TextFieldGroup",
  props: {
    name: {
      type: String
    },
    value: String,
    placeholder: String,
    label: String,
    error: String,
    type: {
      type: String
      // required: false
    },
    onChange: {
      type: Function
      // required: true
    },
    onBlur: {
      type: Function
      // required: false
    }
  },
  methods: {
    // onChange(ev) {
    //   debugger;
    //   // this.$emit("update:currentPage", goToPage);
    // },
    // onBlur(ev) {
    //   debugger;
    //   // this.$emit("update:currentPage", goToPage);
    // }
  },

  computed: {
    /**
     * Filter listeners
     * @returns {Object} Return filtered listeners.
     */
    listeners() {
      const listeners = { ...this.$listeners };
      delete listeners.change;
      return listeners;
    }
  }
};
</script>
<template>
  <div class="mail-address row">
    <div class="col-sm-12 col-md-6">
      <div class="row">
        <div class="col col-md-5">
          <input v-model="address.line1" @change="updateAddress" />
        </div>
        <div class="col col-md-5">
          <input v-model="address.line2" @change="updateAddress" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "MailAddress",
    props: {
      addressProp: {
        type: Object,
        required: true
      }
    },
    data() {
      return {
        // NOTE: Initializing child 'address' object directly from prop parent 'address' object will cause the
        // parent 'address' object to change when this child 'address' object is changed, which Vue does not recommend.
        address: this.copyAddressProp()
      };
    },
    methods: {
      updateAddress() {
        this.$emit("update-address", this.address);
      },
      copyAddressProp() {
        let localObj = {};
        Object.assign(localObj, this.addressProp);
        return localObj;
      }
    },
  };
</script>
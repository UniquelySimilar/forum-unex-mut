<template>
  <div class="mail-list">
    <mail-address class="address" v-for="address in addresses" :key="address.id"
      :addressProp="address" @update-address="updateAddress" />
    <hr>
    <div class="row">
      <div class="col-md-6">
        <table class="table table-bordered">
          <thead>
            <tr>
              <th>ID</th>
              <th>LINE 1</th>
              <th>LINE 2</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="address in addresses" :key="address.id">
              <td>{{ address.id }}</td>
              <td>{{ address.line1 }}</td>
              <td>{{ address.line2 }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
  import MailAddress from "./MailAddress.vue";

  export default {
    name: "MailList",
    data() {
      return {
        addresses: [
          {
            id: 1,
            line1: "Address1Line1",
            line2: "Address1Line2",
          },
          {
            id: 2,
            line1: "Address2Line1",
            line2: "Address2Line2",
          },
        ],
      };
    },
    components: {
      MailAddress,
    },
    methods: {
      updateAddress(address) {
        let id = address.id;
        let foundIndex = this.addresses.findIndex(address => address.id == id);
        let addressCopy = {};
        Object.assign(addressCopy, address);
        this.addresses.splice(foundIndex, 1, addressCopy);
      },
    },
  };
</script>

<style scope>
  .address {
    margin-bottom: 1rem;
  }
</style>
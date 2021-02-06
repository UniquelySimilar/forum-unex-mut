<template>
  <div class="hello">
    <MailAddress v-for="address in addresses" :key="address.id" :addressProp="address" @update-address="updateAddress" />
    <br />
    <table>
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
</template>

<script>
  import MailAddress from "./MailAddress.vue";

  export default {
    name: "HelloWorld",
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
  h3 {
    margin: 40px 0 0;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    display: inline-block;
    margin: 0 10px;
  }
</style>
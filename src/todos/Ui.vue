<template>
  <div>
    <div>
      <span
        class="field-value"
        v-show="!showField('name')"
        @click="focusField('name')"
      >{{user.name}}</span>
      <input
        v-model="user.name"
        v-show="showField('name')"
        id="user-name"
        type="text"
        class="field-value form-control"
        @focus="focusField('name')"
        @blur="blurField"
      />
    </div>
    <div class="field">
      <span
        class="field-value"
        v-show="!showField('email')"
        @click="focusField('email')"
      >{{user.email}}</span>
      <input
        v-model="user.email"
        v-show="showField('email')"
        type="email"
        class="field-value form-control"
        @focus="focusField('email')"
        @blur="blurField"
      />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      user: {
        name: "",
        email: ""
      },
      editField: ""
    };
  },
  methods: {
    focusField(name) {
      this.editField = name;
    },
    blurField() {
      this.editField = "";
    },
    showField(name) {
      return this.user[name] == "" || this.editField == name;
    }
  }
};
</script>

<style>
</style>
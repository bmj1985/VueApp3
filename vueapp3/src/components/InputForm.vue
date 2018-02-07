<template>
  <div>
<form id="application-input">
      <label>Apply Here: </label>
      <textarea id="application-text" rows="8"
      cols="100" v-model="formText"
      @keyup="bindMessageToPreview(formText)">
      </textarea>
      <input id="submit" type="submit" value="submit" 
      @click.prevent="submitMessage"/>
    </form>
    <p id="message">{{success}}</p>
  </div>
</template>

<script>
export default {
  name: 'InputForm',
  data() {
    return {
      success: '',
      formText: ''
    };
  },
  methods: {
    clearMessage() {
      this.success = '';
    },
    submitMessage() {
      if (this.formText === '') {
        this.success = 'You submitted a blank application. Please try again.';
        setTimeout(() => {
          this.clearMessage();
        }, 2000);
      } else {
        this.success = 'Your application was submitted!';
        this.formText = '';
        setTimeout(() => {
          this.clearMessage();
        }, 2000);
      }
    }
  },
  props: ['bindMessageToPreview']
};
</script>

<style scoped>
#application-text {
  max-width: 786px;
  min-height: 100px;
  margin-top: 20px;
  padding: 10px;
}
</style>

<template>
  <div>
<form id="application-input">
      <label>Apply Here: </label>
      <textarea id="application-text" rows="8" cols="100" v-model="message"></textarea>
      <input id="submit" type="submit" value="Submit" @click.prevent="submitMessage"/>
    </form>
    <p id="message">&nbsp;{{success}}</p>
    <button id="preview-toggle" @click="showPreview =! showPreview">Show Preview</button>
    <section id="application-preview" :class="{hidden: showPreview}">
      <p id="message">{{message}}</p>
    </section>
  </div>
</template>

<script>
export default {
  name: 'InputForm',
  data() {
    return {
      success: '',
      showPreview: true,
      message: ''
    };
  },
  methods: {
    clearMessage() {
      this.success = '';
    },
    submitMessage() {
      if (this.message === '') {
        this.success = 'You submitted a blank application. Please try again.';
        setTimeout(() => {
          this.clearMessage();
        }, 4000);
      } else {
        this.success = 'Your application was submitted!';
        this.message = '';
        setTimeout(() => {
          this.clearMessage();
        }, 4000);
      }
    }
  }
};
</script>

<style scoped>
#application-preview {
  border-radius: 6px;
  box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.3);
  border: 1px solid darkgrey;
  min-height: 100px;
  margin-top: 20px;
  padding: 10px;
  max-width: 786px;
}
.hidden {
  display: none;
}

#application-text {
  max-width: 786px;
  min-height: 100px;
  margin-top: 20px;
  padding: 10px;
}
</style>

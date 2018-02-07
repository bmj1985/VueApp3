<template>
  <div id="app">
    <TheHeader/>
    <main>
    <JobDetails/>
    <InputForm :bindMessageToPreview="bindMessageToPreview"
    :submitMessage="submitMessage" :success="success" :formText="formText"/>
    <ThePreview :preview="formText"/>
    </main>
    <TheFooter/>
  </div>
</template>

<script>
import TheHeader from '@/components/TheHeader';
import InputForm from '@/components/InputForm';
import JobDetails from '@/components/JobDetails';
import ThePreview from '@/components/ThePreview';
import TheFooter from '@/components/TheFooter';

export default {
  name: 'App',
  components: { TheHeader, InputForm, JobDetails, ThePreview, TheFooter },
  data() {
    return {
      formText: '',
      success: ''
    };
  },
  methods: {
    clearMessage() {
      this.success = '';
      this.formText = '';
    },
    submitMessage() {
      if (this.formText === '') {
        this.success = 'You submitted a blank application. Please try again.';
        setTimeout(() => {
          this.clearMessage();
        }, 5000);
      } else {
        this.success = 'Your application was submitted!';
        setTimeout(() => {
          this.clearMessage();
        }, 5000);
      }
    },
    bindMessageToPreview(preview) {
      this.formText = preview;
    }
  }
};
</script>

<style>
#app {
  margin: 8px 30px 0 30px;
  padding: 0;
  font-family: sans-serif;
  color: #1b997a;
  display: grid;
  grid-template-rows: 15% 75% 10%;
}
header {
  grid-row: 1 / 2;
  display: grid;
  grid-template-columns: 25% 50% 15%;
  grid-template-rows: 50% 50%;
  padding-top: 10px;
}

main {
  grid-row: 2/3;
  width: 70%;
  margin: 0 auto;
  padding: 10px;
}

footer {
  position: fixed;
  bottom: 0;
  padding: 5px;
}
</style>

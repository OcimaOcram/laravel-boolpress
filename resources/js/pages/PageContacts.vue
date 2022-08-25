<template>
  <div>
    <h1>Contact us</h1>
    <form @submit.prevent="submitMessage">
        <div class="mb-3">
            <label class="form-label" for="name">Name</label>
            <input class="form-control" type="text" name="name" id="name" v-model="name"> 
        </div>
        <div class="mb-3">
            <label class="form-label" for="email">email</label>
            <input class="form-control" type="text" name="email" id="email" v-model="email"> 
        </div>
        <div class="mb-3">
            <label class="form-label" for="message">message</label>
            <textarea class="form-control" name="message" id="message" cols="30" rows="10" v-model="message"></textarea>
        </div>
        <div>
          <input class="form-check-input" type="checkbox" name="newsletter" id="newsletter" v-model="mailinglist">
          <label class="form-check-label" for="newsletter">Iscrivimi alla newsletter</label>
        </div>
        <button type="submit" class="btn btn-primary">Send</button>
    </form>
  </div>
</template>

<script>
import Axios from 'axios';

export default {
    name: 'PageContacts',
    data() {
      return {
        name: '',
        mail: '',
        message: '',
        mailinglist: true,
      }
    },
    methods: {
      submitMessage() {
        console.log('funziona');
        axios.post('/aoi/leads/create', {
          name: this.name,
          email: this.email,
          message: this.message,
          mailingList: this.mailingList
        })
         .then(res => console.log(res.data));
      }
    }
}
</script>

<style lang="scss" scoped>

</style>
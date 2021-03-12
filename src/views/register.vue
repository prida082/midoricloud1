<template>
  <div class="register">
    <b-container>
      <br />
      <b-card bg-variant="dark" text-variant="white" title="Register">
        <b-form v-if="show">
          <b-row>
            <b-col cols="6">
              <b-form-group
                id="input-group-1"
                label="Email address"
                label-for="input-1"
              >
                <b-form-input
                  id="input-1"
                  v-model="email"
                  type="email"
                  placeholder="Enter email"
                  required
                ></b-form-input>
              </b-form-group>
            </b-col>
            <b-col class="6">
              <b-form-group
                id="input-group-1"
                label="Password"
                label-for="input-1"
              >
                <b-form-input
                  id="input-1"
                  v-model="pass"
                  type="password"
                  placeholder="Enter password"
                  required
                ></b-form-input>
              </b-form-group>
            </b-col>
          </b-row>
          <b-row>
            <b-col class="6">
              <b-form-group
                id="input-group-2"
                label="First name"
                label-for="input-2"
              >
                <b-form-input
                  id="input-2"
                  v-model="name"
                  placeholder="Enter First name"
                  required
                ></b-form-input>
              </b-form-group>
            </b-col>
            <b-col class="6">
              <b-form-group
                id="input-group-2"
                label="Last name"
                label-for="input-2"
              >
                <b-form-input
                  id="input-2"
                  v-model="surname"
                  placeholder="Enter Last name"
                  required
                ></b-form-input>
              </b-form-group>
            </b-col>
          </b-row>
          <b-row>
            <b-col class="3">
              <b-form-group
                id="input-group-3"
                label="Phone"
                label-for="input-3"
              >
                <b-form-input
                  id="input-3"
                  v-model="phone"
                  placeholder="Enter phone number"
                  type="tel"
                  required
                ></b-form-input>
              </b-form-group>
            </b-col>
            <b-col class="3">
              <b-form-group
                id="input-group-3"
                label="Gender"
                label-for="input-3"
              >
                <b-form-select
                  id="input-3"
                  v-model="gender"
                  :options="[ 'Male', 'Female', 'Other']"
                  required
                ></b-form-select>
              </b-form-group>
            </b-col>
          </b-row>
          <b-button
            v-on:click="$store.state.say('Register success!')"
            variant="success"
            @click="addData()"
            >Submit</b-button
          >&nbsp;
          <b-button onClick="javascript:location.reload();" variant="danger">Reset</b-button>
        </b-form>
      </b-card>
    </b-container>
  </div>
</template>

<script>
export const db = firebase.firestore();
import firebase from "firebase/app";
export default {
  data() {
    return {
      data: [],
      gender: '',
      show: true,
      email:'',
      name:'',
      surname:'',
      pass:'',
      phone:'',


    };
  },
  methods: {
    addData() {
      // เก็บข้อมูล Form ใน collection MyForm ( มี 1 document แต่จะ update ข้อมูลเรื่อย ๆ )
      const data = {
        Email: this.email,
        Firstname: this.name,
        Lastname: this.surname,
        Password: this.pass,
        Phone: this.phone,
        Gender: this.gender,
      };
      db.collection("User")
        .doc()
        .set(data)
        .then(function () {
          console.log("Document successfully written! -> User");
        })
        .catch(function (error) {
          console.error("Error writing document: ", error);
        });
      const dataText = {
        Email: this.email,
        Firstname: this.name,
        Lasttname: this.surname,
        Phone: this.phone,
        timestamp: firebase.firestore.FieldValue.serverTimestamp(),
      };
      db.collection("MyText")
        .doc()
        .set(dataText)
        .then(function () {
          console.log("Document successfully written! -> MyText");
        })
        .catch(function (error) {
          console.error("Error writing document: ", error);
        });
    },
    reset() {},
  },
};
</script>
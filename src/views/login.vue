<template>
  <div class="login">
    <br />
    <br />
    <br />
    <b-container>
      <b-card bg-variant="dark" text-variant="white" title="LOGIN">
        <b-row class="text-center">
          <b-col></b-col>
          <b-col class="8">
            <b-card-text>
              <b-form @submit.stop.prevent>
                <label for="text-password">Email</label>
                <b-form-input
                  type="email"
                  id="text-email"
                  aria-describedby="password-help-block"
                ></b-form-input>
              </b-form>
            </b-card-text>
          </b-col>
          <b-col></b-col>
        </b-row>
        <br>
        <b-row class="text-center">
          <b-col></b-col>
          <b-col class="8">
            <b-card-text>
              <b-form @submit.stop.prevent>
                <label for="text-password">Password</label>
                <b-form-input
                  type="password"
                  id="text-password"
                  aria-describedby="password-help-block"
                ></b-form-input>
              </b-form>
            </b-card-text>
          </b-col>
          <b-col></b-col>
        </b-row>
        <br>
        <b-button href="#" variant="info">Login</b-button>&nbsp;
        <b-button href="/register" variant="primary">Sign in now</b-button>
      </b-card>
    </b-container>
  </div>
</template>

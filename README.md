# @nuts-foundation/auth

[![npm (scoped)](https://img.shields.io/npm/v/@nuts-foundation/auth)](https://www.npmjs.com/package/@nuts-foundation/auth)

An easy to use client js library to authenticate a user with nuts-auth.

It connects to the auth server, polls for status, updates the UI and forwards the user to a given URL at success.

## Install

From CDN:

```html
<script src="https://cdn.jsdelivr.net/npm/@nuts-foundation/auth/index.min.js"></script>
```

## Style guide

Combine it with the NUTS style guide and get the frontend for free!
https://github.com/nuts-foundation/irma-web-frontend

## Dependencies:

This library depends on the [qrcodejs package from davidshumjs](https://davidshimjs.github.io/qrcodejs/)

## Usage

```html
<!--The nuts auth styleguide -->
<link rel="stylesheet" href="//nuts-foundation.github.io/irma-web-frontend/application.css" />
<!--A lib to render qr-codes -->
<script src="https://cdn.jsdelivr.net/gh/davidshimjs/qrcodejs@gh-pages/qrcode.min.js"></script>
<!--The nuts auth js lib -->
<script src="https://cdn.jsdelivr.net/npm/@nuts-foundation/auth@0.1.0/index.min.js"></script>


<section class="nuts-login-form irma-web-form">
  <header class="header">
    <p>Login with <i class="irma-web-logo">IRMA</i></p>
    <section class="helper">
      <p>Don't know what to do here? Take a look at the <a href="https://privacybydesign.foundation/irma-begin/">de
          website of IRMA</a>.</p>
    </section>
  </header>
  <section class="content">
    <section class="centered loading">
      <div class="irma-web-loading-animation"><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i>
      </div>
      <p>One moment please...</p>
    </section>
    <section class="centered initialized">
      <div id="qrcode"></div>
    </section>
    <section class="centered waiting-for-user">
      <div class="irma-web-waiting-for-user-animation"></div>
      <p>Follow the instructions on your phone</p>
    </section>
    <section class="centered success">
      <div class="irma-web-checkmark-animation"></div>
      <p>Success!</p>
    </section>
    <section class="centered expired">
      <p>The transaction took long</p>
      <p><a href="#" onclick="nutsLogin.start()">Try again</a></p>
    </section>
    <section class="centered cancelled">
      <p>The transaction got cancelled</p>
      <p><a href="#" onclick="nutsLogin.start()">Try again</a></p>
    </section>
    <section class="centered errored">
      <p>Something went wrong</p>
      <p><a href="#" onclick="nutsLogin.start()">Try again</a></p>
    </section>
  </section>
</section>
```

```js
nutsLogin = NutsLogin.init({
    nutsAuthUrl: "http://localhost:1323",
    qrEl: 'qrcode',
    logLevel: 'debug',
    postTokenPath: '/login',
    afterSuccessPath: '/user'
  })
nutsLogin.start();
````

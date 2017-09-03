<template>
  <section class="section">
    <div class="container">
      <h1 class="title">
        Push
      </h1>
      <p class="subtitle">
        Push client with <strong>Bulma</strong>!
      </p>
    </div>
    <div class="container">
      <div class="field">
        <label class="label">DeviceToken</label>
        <div class="control">
          <input class="input" type="text" placeholder="Text input">
        </div>
      </div>
      <div class="field">
        <label class="label">Payload</label>
        <div class="control">
          <textarea class="textarea" placeholder="Payload JSON"></textarea>
        </div>
      </div>
      <div class="file">
        <label class="file-label">
          <input class="file-input" type="file" name="resume">
          <span class="file-cta">
            <span class="file-icon">
              <i class="fa fa-upload"></i>
            </span>
            <span class="file-label">
              Choose a PrivateKey
            </span>
          </span>
        </label>
      </div>
      <div class="field" id="send">
        <a class="button is-primary" @click="sendPushNotification">
          Send
        </a>
      </div>
    </div>
  </section>
</template>

<script>

import { ipcRenderer } from 'electron'
// const { ipcRenderer } = require('electron');

export default {
  name: 'form',
  methods: {
    sendPushNotification: (event) => {
      console.log(event);
      
      ipcRenderer.on('asynchronous-reply', (response) => {
        alert(`asynchronousMessage response : ${response}`);
      });
      
      ipcRenderer.send('asynchronous-message', 'asynchronous-message render process.');
    },
  },
};

</script>

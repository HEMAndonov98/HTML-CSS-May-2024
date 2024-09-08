---
layout: page
title: Contacts
description: If you wish to collaborate you can reach out through the methods I've given below
background: "/images/Crumpled Yellow Papers.jpg"
---

<form
  action="https://formspree.io/f/xzzpwyow"
  method="POST"
>
  <div class="control-group">
    <div class="form-group floating-label-form-group controls">
      <label>Name</label>
      <input type="text" class="form-control" placeholder="Name" id="name" name="name" required data-validation-required-message="Please enter your name.">
      <p class="help-block text-danger"></p>
    </div>
  </div>
  <div class="control-group">
    <div class="form-group floating-label-form-group controls">
      <label for="email">Email Address</label>
      <input type="email" class="form-control" name="email" placeholder="Email Address" id="email" required data-validation-required-message="Please enter your email address.">
      <p class="help-block text-danger"></p>
    </div>
  </div>
  <div class="control-group">
    <div class="form-group col-xs-12 floating-label-form-group controls">
      <label for="phone">Phone Number</label>
      <input type="tel" class="form-control" placeholder="Phone Number" name="phone" id="phone" required data-validation-required-message="Please enter your phone number.">
      <p class="help-block text-danger"></p>
    </div>
  </div>
  <div class="control-group">
    <div class="form-group floating-label-form-group controls">
      <label for="message">Message</label>
      <textarea rows="5" class="form-control" placeholder="Message" name="message" id="message" required data-validation-required-message="Please enter a message."></textarea>
      <p class="help-block text-danger"></p>
    </div>
  </div>
  <br>
  <div id="success"></div>
  <div class="form-group">
    <button type="submit" class="btn btn-primary" id="sendMessageButton">Send</button>
  </div>
</form>

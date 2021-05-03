<template>
  <form name="contact" method="POST" data-netlify-recaptcha="true" data-netlify="true" >
    <!-- Name -->
    <input type="hidden" name="form-name" value="contact">
    <div class="field">
      <label class="label is-medium">Name</label>
      <div class="control has-icons-left">
        <input
          class="input is-medium"
          type="text"
          placeholder="John Smith"
          name="name"
        />
        <span class="icon is-small is-left">
          <font-awesome-icon icon="user" />
        </span>
      </div>
    </div>
    <!-- Email -->
    <div class="field">
      <label class="label is-medium">Email</label>
      <div class="control has-icons-left">
        <input
          name="email address"
          class="input is-medium"
          type="email"
          placeholder="you@email.com"
        />
        <span class="icon is-small is-left">
          <font-awesome-icon icon="envelope" />
        </span>
      </div>
    </div>
    <!-- Subject -->
    <div class="field">
      <label class="label is-medium">Subject</label>
      <div class="control has-icons-left">
        <input
          name="subject"
          class="input is-medium"
          type="text"
          placeholder="Brief Summary"
        />
        <span class="icon is-small is-left">
          <font-awesome-icon icon="briefcase" />
        </span>
      </div>
    </div>
    <!-- Message -->
    <div class="field">
      <label class="label is-medium">Message</label>
      <div class="control">
        <textarea
          name="message"
          class="textarea"
          placeholder="Detailed description of your comment, request, etc"
          rows="8"
        ></textarea>
      </div>
    </div>
    <div class="control" type="submit" data-netlify-recaptcha="true">
      <button class="button is-primary">
        Send message
      </button>
    </div>
  </form>
</template>

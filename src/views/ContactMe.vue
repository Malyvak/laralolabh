<script lang="ts" setup>
import logo from '@/assets/images/header-logo.png';
import quoteCircle from '@/assets/images/QuoteCircle.png'

</script>

<template>
    <section id="contact-me" class="contact-me">
        <div class="contact-me-wrapper">
            <div class="contact-me-container">
                <div class="col-1">
                    <div class="info">
                        <img class="logo" :src="logo"/>
                        <div class="email">laralolabh@gmail.com</div>
                    </div>
                </div>
                <div class="col-2">
                    <img class="quote-circle" :src="quoteCircle"/>
                </div>
            </div>
            <form class="contact-form" target="_blank" action="https://formsubmit.co/laralolabh@gmail.com" method="POST">
                <h4 class="contact-header">CONTACT ME</h4>
                <div class=contact-content>

                    <div class="input-container">
                        <div class="form-group">
                            <label class="input-label" for="name">NAME</label>
                            <input type="text" id="name" name="Name" required>
                        </div>
                        <div class="form-group">
                            <label class="input-label" for="phone">PHONE</label>
                            <input type="text" id="phone" name="Phone" required>
                        </div>
                    </div>

                    <div class="form-group">
                        <label class="input-label" for="email">EMAIL</label>
                        <input type="email" id="email" name="Email" required>
                    </div>

                    <div class="form-group">
                        <label class="input-label" for="subject">SUBJECT</label>
                        <input type="text" id="subject" name="Subject" required>
                    </div>

                    <div class="form-group textarea-group">
                        <label class="textarea-label" for="message">MESSAGE</label>
                        <textarea rows="10" name="Message" id="message" required></textarea>
                    </div>

                    <button class="submit-button" type="submit">SEND</button>
                </div>
            </form>
            <div class="phone-info">
                <img class="logo" :src="logo"/>
                <div class="email">laralolabh@gmail.com</div>
            </div>
        </div>    
    </section>
</template>
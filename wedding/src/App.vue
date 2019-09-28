<template>
  <div class="min-h-screen bg-grey-lighter p-8">
    <div class="max-w-xs mx-auto mb-8">
      <photo-card>
        <img slot="image" v-bind:src="imageLinks[0]" alt="">
        <template slot="heading">
          Card 1
        </template>
        <p>Card Content 1</p>
      </photo-card>
    </div>

    <div class="max-w-xs mx-auto mb-8">
      <photo-card>
        <img slot="image" v-bind:src="imageLinks[1]" alt="">
        <template slot="heading">
          Card 2
        </template>
        <p>Card Content 2</p>
      </photo-card>
    </div>
    <div class="max-w-xs mx-auto mb-8">
      <photo-card>
        <img slot="image" v-bind:src="imageLinks[2]" alt="">
        <template slot="heading">
          Card 2
        </template>
        <p>Card Content 2</p>
      </photo-card>
    </div>
    <div class="max-w-xs mx-auto mb-8">
      <photo-card>
        <img slot="image" v-bind:src="imageLinks[3]" alt="">
        <template slot="heading">
          Card 2
        </template>
        <p>Card Content 2</p>
      </photo-card>
    </div>
    <div class="max-w-xs mx-auto mb-8">
      <photo-card>
        <img slot="image" v-bind:src="imageLinks[4]" alt="">
        <template slot="heading">
          Card 2
        </template>
        <p>Card Content 2</p>
      </photo-card>
    </div>
  </div>
</template>

<script>
import PhotoCard from './components/PhotoCard.vue';

export default {
components: {
    PhotoCard
  },
  data() {
    return {
      imageLinks: [
        'https://cjred.net/wedding/wedding01.jpg',
        'https://cjred.net/wedding/wedding03.jpg',
        'https://cjred.net/wedding/wedding04.jpg',
        'https://cjred.net/wedding/wedding02.jpg',
        'https://cjred.net/wedding/wedding05.jpg'
      ]
    }
  },
}
</script>

<style src="./assets/css/app.css"/>
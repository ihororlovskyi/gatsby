<template>
  <div class="contacts">
    <h1 class='contacts__title'>Contacts</h1>
    <p><a href='mailto:ihororlovskyi@gmail.com?subject=Hello, Ihor'>ihororlovskyi@gmail.com</a></p>
    <p>
      <img class='contacts__icon-mobile' src="/assets/img/svg-icons/old/mobile.svg">
      +38(095)3452589
    </p>
    <div class='contacts__title'>Let's be in touch:</div>
    <nav>
      <a v-for="(item, key) in contacts" v-if="item.isShown == true" :href="item.url" target="_blank">
        <!-- <img class='contacts__icon' :src="'/assets/img/svg-icons/' + item.title + '.svg'"> -->
        <span>{{ item.title }}</span>
      </a>
    </nav>
  </div>
</template>

<script>
import axios from '~/plugins/axios'

export default {
  head: {
    title: 'Contacts',
    meta: [
      { name: 'description', content: 'Contacts page description' }
    ]
  },
  async asyncData() {
    const { data } = await axios.get('contacts.json')
    return {
      contacts: data
    }
  }
}
</script>

<style lang="scss">
$text-color: #ccc;
$accent-color: lighten($text-color, 10%);

.contacts {

  &__title {
    color: $accent-color;
    font-weight: 700;
    text-transform: uppercase;
  }

  &__icon-mobile {
    width: 1.2em;
    transform: translateY(36.5%);
    margin-right: .5em;
  }

  &__icon {
    width: 1.2em;
    transform: translateY(15%);
    margin-right: .5em;
  }

  nav {
    a {
      display: inline-block;
      padding: 1em;
    }
  }
}
</style>

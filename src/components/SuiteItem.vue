<template>
  <ul class="menu-list">
      <li>
          aaa
      </li>
  </ul>
</template>

<script>
import SuiteItem from './SuiteItem'

export default {
  name: 'SuiteItem',
  template: '#item-template',
  props: ['suiteObjects', 'id'],
  components: {
      'SuiteItem': SuiteItem
  }
}
</script>

<template>
    <ul class="menu-list">
      <li>
        <a>aa</a>
      </li>
    </ul>
</template>

<script>
import SuiteItem from './SuiteItem'
export default {
  name: 'SuiteParent',
  props: ['suiteObjects', 'id'],
  components: {
      'SuiteItem': SuiteItem
  }
}
</script>

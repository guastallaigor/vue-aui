<template>
  <div class="aui-group">
    <div class="aui-item">
      <h3>Basic usage</h3>
      <va-tabs>
        <va-tab name="Example">
          <va-timeline :items="items"/>
        </va-tab>
        <va-tab name="Code">
          <pre v-highlightjs><code class="xml" v-text='code'></code></pre>
        </va-tab>
      </va-tabs>
    </div>

    <div class="aui-item">
      <api-table name="va-avatar" :props="[
      {name: 'items', type: 'Array', default: '', description: 'Array of objects. Must have content and title attribute.'},
    ]">
      </api-table>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        items: [
          {title: 'Example title', content: 'Example content'},
          {title: 'Example title', content: 'Example content'},
          {title: 'Example title', content: 'Example content'},
          {title: 'Example title', content: 'Example content'},
          {title: 'Example title', content: 'Example content'},
          {title: 'Example title', content: 'Example content'}
        ],
        code: `<va-timeline :items="items"/>`,
      }
    }
  }
</script>

<template>
  <div class="aui-group">
    <div class="aui-item" style="width:calc(100vw - 920px)">
      <h3>Basic usage</h3>
      <va-tabs>
        <va-tab name="Example">
          <va-timeline :items="items"/>
        </va-tab>
        <va-tab name="Code">
          <pre v-highlightjs><code class="xml" v-text='code'></code></pre>
        </va-tab>
      </va-tabs>
      <h3>All props</h3>
      <va-tabs>
        <va-tab name="Example">
          <va-timeline :items="items" @click="clicked" align-content="center" align-title="center" color="rgb(128, 0, 128)"/>
        </va-tab>
        <va-tab name="Code">
          <pre v-highlightjs><code class="xml" v-text='code2'></code></pre>
        </va-tab>
      </va-tabs>
    </div>

    <div class="aui-item">
      <api-table name="va-timeline" :props="[
      {name: 'items', type: 'Array', default: '', description: 'Array of objects. Must have content and title attribute.'},
      {name: 'align-content', type: 'String', default: 'left', description: 'Align the content with text-align. Accepted values are: left, right and center.'},
      {name: 'align-title', type: 'String', default: 'flex-start', description: 'Align the title with justify-content. Accepted values are: center, flex-start and flex-end.'},
      {name: 'color', type: 'String', default: '#0052cc', description: 'Sets the color of each card (title background and card border).'}
    ]" :events="[
      {name:'click', description: 'Delegates to native DOM click event. Returns the object when clicked.'}
    ]"
    >
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
        ],
        code: `<va-timeline :items="items"/>`,
        code2: `<va-timeline :items="items" @click="clicked" align-content="center" align-title="center" color="#B3D4FF"/>`
      }
    },
    methods: {
      clicked(obj) {
        alert(JSON.stringify(obj, null, 4));
      }
    }
  }
</script>

<template lang="pug">
  doc-view(v-bind:doc="doc")
    component-example(header="Text Dividers" file="breadcrumbs/1")
      v-breadcrumbs(
        divider="/"
        v-bind:items="items"
      )
      v-breadcrumbs(
        divider="-"
        v-bind:items="items"
      )
    component-example(header="Icon Dividers" file="breadcrumbs/2")
      v-breadcrumbs(
        icons,
        divider="forward"
        v-bind:items="items"
      )
      v-breadcrumbs(
        icons,
        divider="chevron_right"
        v-bind:items="items"
      )
</template>

<script>
  export default {
    data () {
      return {
        doc: {
          title: 'Breadcrumbs',
          desc: `
            <p>
              The <code>v-breadcrumbs</code> component is a navigational helper for pages. It can accept a <strong>Material Icons</strong> icon or characters as a divider. An array of objects containing the fields <em>href</em>, <em>text</em> and optional <em>disabled</em> can be passed to the <strong>items</strong> property of the component.  Additionally, a regular slot exists for more control of the breadcrumbs, either utilizing <code>v-breadcrumb</code> or other custom markup.
            </p>
          `,
          props: {
            'v-breadcrumbs': {
              params: [
                [
                  'divider',
                  'String',
                  '/',
                  'Specifies the dividing character'
                ],
                [
                  'icon',
                  'Boolean',
                  'False',
                  'Specifies that the divider is an icon'
                ],
                [
                  'items',
                  'Array',
                  '[]',
                  'Accepts v-breadcrumbs object'
                ]
              ]
            },
            'v-breadcrumbs-item': {
              params: [
                [
                  'item',
                  'Object',
                  `{ href: '#!', text: '', disabled: false }`,
                  'The individual breadcrumbs'
                ]
              ]
            }
          }
        },
        items: [
          {
            href: '#!',
            text: 'Dashboard',
            disabled: false
          },
          {
            href: '#!',
            text: 'Link 1',
            disabled: false
          },
          {
            href: '#!',
            text: 'Link 2',
            disabled: true
          }
        ]
      }
    },

    mounted () {
      this.$emit('view', this.meta())
    },

    preFetch () {
      return this.methods.meta()
    },

    methods: {
      meta () {
        return {
          title: 'Breadcrumbs Component | Vuetify.js',
          h1: 'Breadcrumbs',
          description: 'The v-breadcrumbs component is a navigational helper for pages. It can accept a Material Icons icon or characters as a divider',
          keywords: 'vuetify, breadcrumbs, components'
        }
      }
    }
  }
</script>
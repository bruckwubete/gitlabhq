<script>
  import tooltip from '../../../vue_shared/directives/tooltip';
  import icon from '../../../vue_shared/components/icon.vue';

  /**
   * Renders either a cancel, retry or play icon pointing to the given path.
   * TODO: Remove UJS from here and use an async request instead.
   */
  export default {
    props: {
      tooltipText: {
        type: String,
        required: true,
      },

      link: {
        type: String,
        required: true,
      },

      actionMethod: {
        type: String,
        required: true,
      },

      actionIcon: {
        type: String,
        required: true,
      },
    },

    components: {
      icon,
    },

    directives: {
      tooltip,
    },

    computed: {
      cssClass() {
        const actionIconDash = gl.text.dasherize(this.actionIcon);
        return `${actionIconDash} js-icon-${actionIconDash}`;
      },
    },
  };
</script>
<template>
  <a
    v-tooltip
    :data-method="actionMethod"
    :title="tooltipText"
    :href="link"
    class="ci-action-icon-container ci-action-icon-wrapper"
    :class="cssClass"
    data-container="body">
    <icon :name="actionIcon"/>
  </a>
</template>

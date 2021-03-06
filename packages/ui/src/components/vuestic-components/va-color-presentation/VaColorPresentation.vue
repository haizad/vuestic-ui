<template>
  <div class="va-color-presentation">
    <va-popover
      color="info"
      :placement="popoverOptions.placement"
      :message="popoverOptions.content"
    >
      <div
        class="va-color-presentation__color"
        :style="computedStyle"
        @click="colorCopy(), notify()"
      />
    </va-popover>

    <div
      class="va-color-presentation__description"
      v-if="name || description"
    >
      <div class="va-color-presentation__name">
        {{ name }}
      </div>
      <div class="va-color-presentation__text">
        {{ description }}
      </div>
    </div>
  </div>
</template>

<script>
import VaPopover from '../va-popover/VaPopover'

import ColorMixin from '../../../services/ColorMixin'
import { getGradientBackground } from '../../../services/color-functions'

// NOTE This component is a tad weird.
// It's not part of presentation nor is it UI component.
// Could be seen as `playground` of sorts.

export default {
  name: 'VaColorPresentation',
  components: { VaPopover },
  mixins: [ColorMixin],
  props: {
    color: {
      type: String,
      default: '',
    },
    variant: {
      type: Array,
      default: () => [],
    },
    width: {
      type: Number,
      default: null,
    },
    name: {
      type: String,
      default: '',
    },
    description: {
      type: String,
      default: '',
    },
  },
  data () {
    return {
      popoverOptions: {
        content: 'Click to copy the color to clipboard',
        placement: 'right',
      },
    }
  },
  computed: {
    computedStyle () {
      const calcBackground = () => {
        if (this.variant.includes('gradient')) {
          return getGradientBackground(this.colorComputed)
        }

        return this.colorComputed
      }

      const calcFilter = () => {
        if (this.variant.includes('hovered')) { return 'brightness(115%)' }
        if (this.variant.includes('pressed')) { return 'brightness(85%)' }
      }

      return {
        background: calcBackground(),
        filter: calcFilter(),
        width: this.width ? `${this.width}px` : '',
      }
    },
  },
  methods: {
    colorCopy () {
      if (this.variant.includes('gradient')) {
        this.$copyText(getGradientBackground(this.colorComputed))
        return
      }

      this.$copyText(this.colorComputed)
    },

    notify () {
      this.showToast("The color's copied to your clipboard", {
        position: 'bottom-right',
      })
    },
  },
}
</script>

<style lang="scss">
@import "../../vuestic-sass/resources/resources";

.va-color-presentation {
  display: flex;
  align-items: center;
  margin-bottom: 1.125rem;

  .v-popover {
    width: 40px;
    height: 40px;

    span {
      outline: none !important;
    }
  }

  &__color {
    height: 40px;
    width: 40px;
    margin-right: 1rem;
    cursor: pointer;
  }

  &__description {
    margin-left: 1rem;
  }

  &__name {
    color: $vue-darkest-blue;
  }

  &__text {
    color: $brand-secondary;
  }
}
</style>

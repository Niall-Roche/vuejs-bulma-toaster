<template>
  <div class="toaster">
    <transition :name="transitionName">
      <article :class="`message is-medium is-${ type ? type.toLowerCase() : 'info'} ${ position || 'top-right' }`" v-show="show">
        <div class="message-header">
          <p>{{ title || (type ? type.toUpperCase() : 'INFO') }}</p>
          <button @click="$emit('close')" class="delete is-medium" aria-label="delete"></button>
        </div>
        <div v-if="message" class="message-body">
          {{ message }}
        </div>
      </article>
    </transition>
  </div>
</template>

<script>
export default {
  name: 'toaster',
  props: {
    show: Boolean,
    type: {
      type: String,
      validator: type => {
        const typeSet = new Set(['success', 'warning', 'info', 'danger', 'primary'])
        return typeSet.has(type.toLowerCase())
      }
    },
    position: {
      type: String,
      validator: position => {
        const positionSet = new Set(['top-right', 'top-left', 'bottom-right', 'bottom-left'])
        return positionSet.has(position.toLowerCase())
      }
    },
    title: String,
    message: String
  },
  computed: {
    transitionName () {
      const position = this.position
      if (position === 'top-right' || position === 'bottom-right' || !position) {
        return 'appear-from-right'
      } else if (position === 'top-middle') {
        return 'appear-from-top'
      } else if (position === 'bottom-middle') {
        return 'appear-from-bottom'
      }
      return 'appear-from-left'
    }
  }
}
</script>

<style lang="scss" scoped>
.toaster {
  width: 100%;
  display: flex;
  justify-content: center;
}

.message {
  z-index: 100;
  border-radius: 0;
  box-shadow: 0 1px 2px 0 rgba(60, 64, 67, 0.3), 0 4px 8px 3px rgba(60, 64, 67, 0.15);
  position: fixed;
  max-width: 40vw;
  .message-header {
    border-radius: 0;
  }
}

button.delete {
  margin-left: 20px !important;
}

.top-right {
  top: 50px;
  right: 50px;
}

.top-middle {
  top: 50px;
}

.top-left {
  top: 50px;
  left: 50px;
}

.bottom-right {
  bottom: 50px;
  right: 50px;
}

.bottom-middle {
  bottom: 50px;
}

.bottom-left {
  bottom: 50px;
  left: 50px;
}

.appear-from-right-enter-active, .appear-from-right-leave-active {
  transition: right .5s;
}
.appear-from-right-enter, .appear-from-right-leave-to {
  right: -1000px;
}

.appear-from-left-enter-active, .appear-from-left-leave-active {
  transition: left .5s;
}
.appear-from-left-enter, .appear-from-left-leave-to {
  left: -1000px;
}

.appear-from-top-enter-active, .appear-from-top-leave-active {
  transition: top .5s;
}
.appear-from-top-enter, .appear-from-top-leave-to {
  top: -1000px;
}

.appear-from-bottom-enter-active, .appear-from-bottom-leave-active {
  transition: bottom .5s;
}
.appear-from-bottom-enter, .appear-from-bottom-leave-to {
  bottom: -1000px;
}
</style>

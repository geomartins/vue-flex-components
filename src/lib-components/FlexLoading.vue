<template>
  <div>
    <transition name="fade">
      <div :style="flexVars" class="flexLoading" v-if="showing == true">
        <div class="flexLoading__content">
          <div class="flexLoading__content__top">
            <i class="icon" :class="icon" :style="iconVars"></i>
          </div>
          <div :style="bottomVars" class="flexLoading__content__bottom">
            {{ label }}
          </div>
        </div>
      </div>
    </transition>

    <slot></slot>
  </div>
</template>

<script>
import "@fortawesome/fontawesome-free/css/all.css";
import "@fortawesome/fontawesome-free/js/all.js";
export default {
  name: "FlexLoading",
  props: {
    showing: {
      type: Boolean,
      default: true,
    },
    label: {
      type: String,
      default: "",
    },
    labelSize: {
      type: String,
      default: "1rem",
    },
    labelWeight: {
      type: String,
      default: "lighter",
    },
    labelColor: {
      type: String,
      default: "black",
    },
    bgColor: {
      type: String,
      default: "grey",
    },
    icon: {
      type: String,
      default: "icon fas fa-spinner",
    },
    iconColor: {
      type: String,
      default: "black",
    },
    iconSize: {
      type: String,
      default: "2rem",
    },
    speed: {
      type: String,
      default: "4s",
    },
    transition: {
      type: String,
      default: "4s",
    },
  },
  data() {
    return {};
  },
  computed: {
    flexVars() {
      return {
        "--bgColor": this.bgColor,
        "--showing": this.showing == true ? "block" : "none",
        "--transition": this.transition,
      };
    },
    iconVars() {
      return {
        "--iconColor": this.iconColor,
        "--iconSize": this.iconSize,
        "--speed": this.speed,
      };
    },

    bottomVars() {
      return {
        "--labelColor": this.labelColor,
        "--labelSize": this.labelSize,
        "--labelWeight": this.labelWeight,
      };
    },
  },
  methods: {},
};
</script>

<style >
* {
  box-sizing: border-box;
}
.flexLoading {
  position: absolute;
  width: 100%;
  height: 100%;
  background: var(--bgColor);
  z-index: 1000;
  overflow: hidden;
  display: var(--showing);
  font-family: inherit;
  cursor: progress;
}

.flexLoading > .flexLoading__content {
  display: flex;
  width: 100%;
  height: 100%;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: absolute;
}

.flexLoading > .flexLoading__content > div {
  margin-bottom: 2rem;
  font-family: roboto;
}

.flexLoading
  > .flexLoading__content
  > .flexLoading__content__bottom {
  color: var(--labelColor);
  font-size: var(--labelSize);
  font-weight: var(--labelWeight);
}

.flexLoading__content__top > .icon {
  font-size: var(--iconSize);
  text-align: center;
  color: var(--iconColor);
  text-decoration: none;
  -webkit-animation: spin var(--speed) linear infinite;
  -moz-animation: spin var(--speed) linear infinite;
  animation: spin var(--speed) linear infinite;
}

/* .btn-circle span :hover {
 color :silver;
} */

/* rotate 360 key for refresh btn */
@-moz-keyframes spin {
  100% {
    -moz-transform: rotate(360deg);
  }
}
@-webkit-keyframes spin {
  100% {
    -webkit-transform: rotate(360deg);
  }
}
@keyframes spin {
  100% {
    -webkit-transform: rotate(360deg);
    transform: rotate(360deg);
  }
}

/** Transition */
.fade-enter-active,
.fade-leave-active {
  transition: opacity var(--transition);
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>

<script setup lang="ts">
import { ref } from 'vue'

import Intro from './components/Tutorial/Intro.vue';
import VBinds from './components/Tutorial/directives/v-bind.vue';
import VIf from './components/Tutorial/directives/v-if.vue';
import VShow from './components/Tutorial/directives/v-show.vue';
import VFor from './components/Tutorial/directives/v-for.vue';
import VOn from './components/Tutorial/v-on.vue';
import EventModifiers from './components/Tutorial/EventModifiers.vue';
import Forms from './components/Tutorial/Forms.vue';
import CSSBinding from './components/Tutorial/CSSBinding.vue';
import ComputedProperties from './components/Tutorial/ComputedProperties.vue';
import Watchers from './components/Tutorial/Watchers.vue';
import Emit from './components/Tutorial/emit/Emit.vue';
import Fallthrough from './components/Tutorial/fallthrough/Fallthrough.vue';
import ScopedStyling from './components/Tutorial/ScopedStyling.vue';
import SlotComp from './components/Tutorial/slots/SlotComp.vue';
import ScopedSlot from './components/Tutorial/slots/ScopedSlot.vue';
import DynamicComponents from './components/Tutorial/DynamicComponents/DynamicComponents.vue'

const background = true;

const vBinds = {
  class: 'text-success',
  style: 'font-size: 20px'
};

const classObject = {
  'ps-5': true,
  'text-danger': true,
  'bg-dark': true
};

const vIfStock = 2;
const vIfText = "this text includes worsd";

const vShow = true;

const vForArray = [
  { class: 'text-danger', text: 'Red' },
  { class: 'text-success', text: 'Green' },
  { class: 'text-primary', text: 'Blue' },
  { class: 'text-warning', text: 'Yellow' }
];

const vOnClick = ref(true)
const vOnIsInput = ref(false)
const vOnTypingTimer = ref(null)
const vOnOntype = ref('click')
const vOnXPos = ref(0)

const keyDown = ref('')
const keySent = ref(false)

const formItemName = null
const formItemNumber = null
const formItemImportant = false
const formList = []

const classList0 = 'fst-italic'
const classList1 = 'fw-bold'

const checkboxVal = false

const rangeVal = 70
const watchX = 0
const watchXDiff = 0
const watcherInput = ''
const watcherFeedback = 'Enter an email address.'
const watcherEmailValid = ''

const foods = [
  { "name": "Apples" },
  { "name": "Pizza" },
  { "name": "Rice" },
  { "name": "Fish" },
  { "name": "Cake" }
]

const fallthroughItems = ['Buy apples', 'Make pizza', 'Mow the lawn']
const fallthroughNewItem = ''

const componentToggleValue = true

</script>

<template>
  <Intro msg="Hello World" />
  <VBinds :background="background" :vBinds="vBinds" :classObject="classObject" />
  <VIf :vIfStock="vIfStock" :vIfText="vIfText" />
  <VShow :vShow="vShow" />
  <VFor :vForArray="vForArray" />
  <VOn :click="vOnClick" :isInput="vOnIsInput" :typingTimer="vOnTypingTimer" :ontype="vOnOntype" :xPos="vOnXPos" />
  <EventModifiers :keyDown="keyDown" :keySent="keySent" />
  <Forms :itemName="formItemName" :itemNumber="formItemNumber" :itemImportant="formItemImportant" :list="formList" />
  <CSSBinding :classList0="classList0" :classList1="classList1" />
  <ComputedProperties :checkbox-val="checkboxVal" />
  <Watchers :range-val="rangeVal" :watch-x="watchX" :watch-x-diff="watchXDiff" :watcher-input="watcherInput"
    :watcher-email-valid="watcherEmailValid" :watcher-feedback="watcherFeedback" />
  <Emit :foods="foods" />
  <Fallthrough :items="fallthroughItems" :new-item="fallthroughNewItem" />
  <ScopedStyling />
  <SlotComp />
  <ScopedSlot />
  <DynamicComponents :toggle-value="componentToggleValue" />
</template>

<template>
  <modal
    :show="show"
    @close="$emit('close')"
  >
    <div class="-mx-5">
      <h2 class="text-red-600 text-2xl font-medium mb-4 px-4">
        We couldn't save your form
      </h2>

      <div
        v-if="validationErrorResponse"
        class="p-4 border-b border-t"
      >
        <p
          v-if="validationErrorResponse.message"
          v-text="validationErrorResponse.message"
        />
        <ul class="list-disc list-inside">
          <li
            v-for="(err, key) in validationErrorResponse.errors"
            :key="key"
          >
            {{ Array.isArray(err) ? err[0] : err }}
          </li>
        </ul>
      </div>

      <div class="px-4 pt-4 text-right">
        <v-button
          color="gray"
          shade="light"
          @click="$emit('close')"
        >
          Close
        </v-button>
      </div>
    </div>
  </modal>
</template>

<script>
export default {
  name: 'FormErrorModal',
  props: {
    show: { type: Boolean, required: true },
    validationErrorResponse: { type: Object, required: false },
  },
  emits: ['close'],
}
</script>

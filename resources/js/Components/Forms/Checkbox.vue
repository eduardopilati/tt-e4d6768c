<script setup lang="ts">
const props = defineProps({
    modelValue: {
        type: Boolean,
        required: true,
    },
    label: {
        type: String,
        required: true,
    },
    id: {
        type: String,
        required: true,
    },
    name: {
        type: String,
        required: false,
    },
})

const emit = defineEmits(['update:modelValue'])
</script>

<template>
    <div class="form-check">
        <input
            :id="name ?? id"
            class="form-check-input"
            type="checkbox"
            :checked="modelValue"
            :name="name"
            @update:modelValue="emit('update:modelValue', $event.target.checked)">
        <label class="form-check-label" :for="name ?? id">
            {{ label }}
        </label>
    </div>
</template>

<template>
    <input type="radio"
           data-toggle="button"
           :id="id"
           :name="name"
           :value="value"
           :checked="value == this.$parent[this.name]"
           @click="updateRadioButtonValue(value)"
    >
    <label :for="id" class="button expanded">
        <slot></slot>
    </label>
</template>
<script>
    export default {
        props: ['id','name','value'],
        methods: {
            updateRadioButtonValue: function (value) {
                this.$parent.$set(this.name,value);
            }
        }
    };
</script>
<style lang="sass">
    $selected-color: green;

    input[data-toggle] {
        display: none;
    }

    input[data-toggle]:checked + label,
    input[data-toggle]:checked + label:active {
        background-color: $selected-color;
        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.15) inset,
        0 1px 2px rgba(0, 0, 0, 0.05);
    }

    .button-group.toggle {
        li:not(first-child) {
            margin: 0 -0.9rem;
        }
    }
</style>

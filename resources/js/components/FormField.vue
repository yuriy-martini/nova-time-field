<template>
    <default-field :field="field">
        <template slot="field">
            <div class="flex items-center">
                <time-picker
                    class="w-full form-control form-input form-input-bordered"
                    :field="field"
                    :placeholder="placeholder"
                    :value="value"
                    :twelveHourTime="twelveHourTime"
                    @change="handleChange"
                />
            </div>

            <p v-if="hasError" class="my-2 text-danger">
                {{ firstError }}
            </p>
        </template>
    </default-field>
</template>

<script>
import TimePicker from './../TimePicker'
import { Errors, FormField, HandlesValidationErrors } from 'laravel-nova'

export default {
    mixins: [HandlesValidationErrors, FormField],

    components: { TimePicker },

    computed: {
        placeholder() {
            return moment(new Date()).format('HH:ss')
        },

        twelveHourTime() {
            return this.field.twelveHourTime || false;
        }
    },
}
</script>

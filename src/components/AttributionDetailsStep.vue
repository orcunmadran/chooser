<template>
    <div class="step-content">
        <div
            v-if="status==='current'"
            class="step-actions"
        >
            <p class="attribution-details-instructions">
                {{ $t('stepper.AD.instructions') }}
            </p>
            <form class="attribution-details-form">
                <b-field :label="this.$t('stepper.AD.form.creator-name.label')">
                    <b-input
                        v-model="creatorName"
                        :placeholder="this.$t('stepper.AD.form.creator-name.placeholder')"
                    />
                </b-field>
                <b-field :label="this.$t('stepper.AD.form.creator-profile.label')">
                    <b-input
                        v-model="creatorProfileUrl"
                        :placeholder="this.$t('stepper.AD.form.creator-profile.placeholder')"
                    />
                </b-field>
                <b-field :label="this.$t('stepper.AD.form.work-title.label')">
                    <b-input
                        v-model="workTitle"
                        :placeholder="this.$t('stepper.AD.form.work-title.placeholder')"
                    />
                </b-field>
                <b-field :label="this.$t('stepper.AD.form.work-url.label')">
                    <b-input
                        v-model="workUrl"
                        :placeholder="this.$t('stepper.AD.form.work-url.placeholder')"
                    />
                </b-field>
            </form>
        </div>
    </div>
</template>
<script>
import { mapMutations, mapState } from 'vuex'

export default {
    name: 'AttributionDetails',
    props: {
        status: {
            type: String,
            validator(value) {
                return ['current', 'previous', 'inactive'].includes(value)
            }
        }
    },
    computed: {
        ...mapState(['attributionDetails']),
        creatorName: {
            get() { return this.attributionDetails.creatorName },
            set(newVal) {
                this.setCreatorName(newVal)
            }
        },
        creatorProfileUrl: {
            get() { return this.attributionDetails.creatorProfileUrl },
            set(newVal) {
                this.setCreatorProfileUrl(newVal)
            }
        },
        workTitle: {
            get() { return this.attributionDetails.workTitle },
            set(newVal) {
                this.setWorkTitle(newVal)
            }
        },
        workUrl: {
            get() { return this.attributionDetails.workUrl },
            set(newVal) {
                this.setWorkUrl(newVal)
            }
        }
    },
    methods: {
        ...mapMutations(['setCreatorName', 'setCreatorProfileUrl', 'setWorkTitle', 'setWorkUrl'])
    }

}
</script>
<style>
.attribution-details-form {
    margin-top: 1rem;
}
.attribution-details-form .label {
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 24px;
    color: #333333;
}
.attribution-details-form .input {
    font-weight: 600;
    font-size: 16px;
    color: #333333;
}
</style>

<template>
    <div class="inbox-body">
        <button class="btn btn-primary" @click="navigateBack">
            <i class="fa fa-arrow-left" aria-hidden="true"></i>&nbsp; Back
        </button>
        
    </div>
</template>

<script>
    import { eventBus } from './main';
    
    export default {
        props: {
            data: {
                type: Object,
                required: true
            }
        },
        methods: {
            navigateBack(){
                let previousView = this.$parent.previousView;
                
                eventBus.$emit('changeView', {
                    tag: previousView.tag,
                    title: previousView.title,
                    data: previousView.data
                });
            }
        }
    };
</script>
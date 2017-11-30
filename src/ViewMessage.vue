<template>
    <div class="inbox-body">
        <button class="btn btn-primary" @click="navigateBack">
            <i class="fa fa-arrow-left" aria-hidden="true"></i>&nbsp; Back
        </button>
        <button class="btn btn-danger" @click="data.message.isDeleted = true" :disabled="data.message.isDeleted">
            <i class="fa fa-trash-o"></i>&nbsp; {{ data.message.isDeleted ? 'Deleted' : 'Delete' }}
        </button>
        
        <template v-if="typeof data.message.isRead !== 'undefined'">
            <button class="btn btn-primary">
                
            </button>
        </template>
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
        },
        activated(){
            if(typeof this.data.message.isRead !== 'undefined'){
                this.data.message.isRead = true;
            }    
        },
        filters: {
            formatBytes(bytes){
                if(bytes == 0){
                    return '0 Bytes';
                }
                
                let decimals = 2;
                let k = 1000;
                let dm =decimals + 1 || 3;
                let sizes = ['Bytes', 'KB', 'MB', 'GB', 'TB', 'PB', 'EB', 'ZB', 'YB'];
                let i = Math.floor(Math.log(bytes) / Math.log(k));
                
                return parseFloat((bytes / Math.pow(k, i)).toFixed(dm)) + ' ' + sizes[i];
            }
        }
    };
</script>
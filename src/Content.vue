<template>
    <aside class="lg-side">
        
    </aside>
</template>
<script>
    import { eventBus } from './main';
    import Inbox from './Inbox.vue';
    import Sent from './Sent.vue';
    import Important from './Important.vue';
    import Trash from './Trash.vue';
    import ViewMessage from './ViewMessage.vue';
    
    export default {
        props: {
            messages: {
                type: Array,
                required: true
            }
        },
        data(){
            return {
                history: [
                    {
                        tag: 'app-inbox',
                        title: 'Inbox',
                        data: {
                            messages: null
                        }
                    }
                ]
            };
        },
        created(){
            eventBus.$on('changeView', (data) => {
                let temp = [{
                    tag: data.tag,
                    title: data.title,
                    data: data.data || {}
                }];
                
                this.history = temp.concat(this.history.splice(0));
            });
        }
    };
</script>
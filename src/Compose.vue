<template>
    <div>
        Compose
    </div>
</template>
<script>
    import moment from 'moment';
    import { eventBus } from './main';
    
    export default {
        data(){
            return {
                message: {
                    subject: '',
                    content: ''
                }
            };
        },
        methods: {
            sendMessage(){
                eventBus.$emit('sentMessage', {
                   message: {
                       subject: this.message.subject,
                       content: this.message.content,
                       isDeleted: false,
                       type: 'outgoing',
                       date: moment(),
                       from: {
                           name: 'Joe Bloggs',
                           email: 'abc@example.com'
                       },
                       attachments: []
                   } 
                });
            }
        }
    };
</script>
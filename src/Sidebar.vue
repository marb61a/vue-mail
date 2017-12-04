<template>
    <aside class="sm-side">
        <div class="user-head">
            <img src="src/assets/images/profile.jpg">
            <div class="user-name">
                <h5>Joe Bloggs</h5>
                <span class="email-address">joebloggs@example.com</span>
            </div>
        </div>
        <div class="compose-wrapper">
            <app-compose></app-compose>
        </div>
        <ul class="inbox-nav">
            
        </ul>
    </aside>
</template>
<script>
    import { eventBus } from './main';
    import Compose from './Compose.vue';
    
    export default {
        props:{
            messages: {
                type: Array,
                required: true
            }
        },
        data(){
            return {
                activeView: 'app-inbox'
            };
        },
        created(){
            eventBus.$on('changeView', (data) => {
                this.activeView = data.tag;
            });
        },
        methods: {
            navigate(newView, title){
                eventBus.$emit('changeView', {
                    tag: newView,
                    title: title
                });
            }   
        }
    };
</script>


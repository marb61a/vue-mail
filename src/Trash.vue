<template>
    <div class="inbox-body">
        <app-messages :messages="trashedMessages"></app-messages>
    </div>
</template>
<script>
    import Messages from './Messages.vue';
    
    export default {
        props: {
            data: {
                
            }
        }
    };
</script>
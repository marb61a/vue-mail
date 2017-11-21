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
    </aside>
</template>
<script>
    import { eventBus } from './main';
    import Compose from './Compose.vue';
    
    export default {
    
    }
</script>
<tmeplate>
  <div class="container">
    <div class="mail-box">
      <app-sidebar :messages="messages"></app-sidebar>
      <app-content :messages="messages"></app-content>  
    </div>
  </div>
</tmeplate>
<script>
  import Sidebar from './Sidebar.vue';
  import Content from './Content.vue';
  import messages from './data/messages';
  import randomMessages from './data/random-messages';
  import { eventBus } from './main';

  export default {
    data(){
      return {
        messages: messages
      };
    }  
  };
</script>
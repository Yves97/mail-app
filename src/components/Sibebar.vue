<template>
    <aside class="sm-side">
        <div class="user-head">
            <img src="../../public/images/profile.jpg">
            <div class="user-name">
                <h5>Bo Anderson</h5>
                <span class="email-address">yveskouadio111@yahoo.fr</span>
            </div>
        </div>
        <div class="compose-wrapper">
            <app-compose></app-compose>
        </div>
        <ul class="inbox-nav">
            <li :class="{active: activeView == 'app-inbox'}">
                <a href="#" @click.prevent="navigate('app-inbox','Inbox')">
                    <i class="fa fa-inbox" aria-hidden="true"></i>Inbox <span class="label label-danger pull-right">{{ unreadMessages.length }}</span>
                </a>
            </li>
            <li :class="{active: activeView == 'app-sent'}">
                <a href="#" @click.prevent="navigate('app-sent','Sent')">
                    <i class="fa fa-envelope-o" aria-hidden="true"></i>Sent <span class="label label-default pull-right">{{ sentMessages.length }}</span>
                </a>
            </li>
            <li :class="{active: activeView == 'app-important'}">
                <a href="#" @click.prevent="navigate('app-important','Important')">
                    <i class="fa fa-bookmark-o" aria-hidden="true"></i>Important<span class="label label-warning pull-right"> {{ importantMessages.length}}</span>
                </a>
            </li>
            <li :class="{active: activeView == 'app-trash'}">
                <a href="#" @click.prevent="navigate('app-trash','Trash')">
                    <i class="fa fa-trash-o" aria-hidden="true"></i>Trash <span class="label label-default pull-right">{{ trashedMessages.length }}</span>
                </a>
            </li>
        </ul>
    </aside>
</template>

<script>
    import Compose from './Compose.vue'
    import {eventBus} from '../main'
    export default {
        //passing data from the parent App.vue 
        props:{
            messages:{
                type: Array,
                required: true
            }
        },
        created(){
            eventBus.$on('changeView',(data)=>{
                this.activeView = data.tag
            })
        },
        data(){
            return{
                activeView : 'app-inbox'
            }
        },
        //changement dynamique des components via le eventBus(creation d'evenement)
        methods: {
            navigate(newVue,title){
                eventBus.$emit('changeView',{
                    tag: newVue,
                    title: title
                })
            }
        },
        computed:{
            //differents messages states computed
            unreadMessages(){
                return this.messages.filter(function(message){
                    return (message.type == 'incoming' && !message.isRead && !message.isDeleted)
                })
            },
            sentMessages(){
                return this.messages.filter(function(message){
                    return (message.type == 'outgoing' && !message.isDeleted)
                })
            },
            importantMessages(){
                return this.messages.filter(function(message){
                    return (message.type == 'incoming' && message.isImporant === true && !message.isDeleted)
                })
            },
            trashedMessages(){
                return this.messages.filter(function(message){
                    return message.isDeleted === true
                })
            }
        },
        components:{
            appCompose: Compose
        }
    }
</script>
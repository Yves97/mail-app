<template>
    <div>
        <a href="#composeModal" data-toggle="modal" class="btn-compose">{{messageAction}}</a>

        <div aria-hidden="true" role="dialog" tabindex="-1" id="composeModal" class="modal fade" style="display: none;">
            <div class="modal-dialog">
                <div class="modal-content">
                    <div class="modal-header">
                        <button aria-hidden="true" data-dismiss="modal" class="close" type="button">×</button>
                    </div>

                    <div class="modal-body">
                        <form role="form" class="form-horizontal" @submit.prevent="sendMessage">
                            <div class="form-group">
                                <label class="col-lg-2 control-label" for="subject">Subject</label>
                                <div class="col-lg-10">
                                    <input type="text" id="subject" class="form-message" v-model="message.subject">
                                </div>
                            </div>

                            <div class="form-group">
                                <label class="col-lg-2 control-label" for="message">Message</label>
                                <div class="col-lg-10">
                                    <textarea  rows="10" cols="30" class="form-message" id="message" v-model="message.content"></textarea>
                                </div>
                            </div>

                            <div class="form-group">
                                <div class="col-lg-offset-2 col-lg-10">
                                    <button class="btn btn-send" type="submit">Send</button>
                                </div>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import {eventBus} from '../main'
    import moment from 'moment'
    export default {
        data(){
            return{
                message:{
                    subject:'',
                    content: ''
                },
                messageAction: 'Ecrire'
            }
        },
        methods:{
            sendMessage(){
                eventBus.$emit('sentMessage',{
                    message:{
                        subject:this.message.subject,
                        content: this.message.content,
                        isDeleted: false,
                        type:'outgoing',
                        date:moment(),
                        from:{
                            name: 'Yves Kouadio',
                            email:'yveskouadio111@yahoo.fr'
                        },
                        attachments:[]
                    }
                })
            }
        }
    }
</script>
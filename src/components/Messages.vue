<template>
    <table v-if="messages.length > 0 " class="table table-inbox table-hover">
        <tbody>
            <tr v-for="message in messages"  :key="message.id" :class="{ unread: typeof messages.isRead !== 'undefined' && !messages.isRead }">
                <td>
                    <input type="checkbox">
                </td>
                <td>
                    <a href="#" v-if="typeof message.isImportant !== 'undefined'" @click.prevent.stop="message.isImportant = !message.isImportant">
                        <i :class="['fa','fa-star',{important:message.isImportant}]"></i>
                    </a>
                </td>
                <td>{{ message.from.name }}</td>
                <td>{{ message.subject }}</td>
                <td>
                    <i v-if="message.attachments.length > 0" class="fa fa-paperclip"></i>
                </td>
                <td class="text-right">{{ message.date.fromNow() }}</td>
            </tr>
        </tbody>
    </table>
    <p v-else>Not Message yet</p>
</template>

<script>
export default {
    props:{
        messages:{
            type:Array,
            required:true
        }
    }
}
</script>
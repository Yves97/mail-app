<template>
    <aside class="sm-side">
        <div class="user-head">
            <img src="../assets/images/profile.jpg">
            <div class="user-name">
                <h5>Bo Anderson</h5>
                <span class="email-address">yveskouadio111@yahoo.fr</span>
            </div>
        </div>
        <ul class="inbox-nav">
            <li class="active">
                <a href="#">
                    <i class="fa fa-inbox" aria-hidden="true"></i>Inbox <span class="label label-danger pull-right">?</span>
                </a>
            </li>
            <li>
                <a href="#">
                    <i class="fa fa-envelope-o" aria-hidden="true"></i>Sent <span class="label label-default pull-right">?</span>
                </a>
            </li>
            <li>
                <a href="#">
                    <i class="fa fa-bookmark-o" aria-hidden="true"></i>Important<span class="label label-warning pull-right">?</span>
                </a>
            </li>
            <li>
                <a href="#">
                    <i class="fa fa-trash-o" aria-hidden="true"></i>Trash <span class="label label-default pull-right">?</span>
                </a>
            </li>
        </ul>
    </aside>
</template>

<script>
export default {
    
}
</script>
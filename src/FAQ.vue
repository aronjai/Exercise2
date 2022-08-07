<template> 
    <div :class="open ? 'faq open': 'faq'" @click="$emit('toggleOpen', index)">
        <div class="sec">{{faq.title}}</div>
        <div class="content">{{faq.content}}</div>
    </div>
</template>

<script>
export default {
    name: 'FAQ',
    props: ['faq','index','open']
}


</script>
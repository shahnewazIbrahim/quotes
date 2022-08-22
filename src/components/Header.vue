<template>
    <h1>
        <b class="font-serif italic font text-3xl underline">
            {{ title }}
        </b>
        <sup class="font-serif italic font text-3xl top-0">
            <b>&ldquo;&rdquo;</b>
        </sup>
    </h1>
</template>

<script>
export default {
    props : {
        title: String
    }
}
</script>
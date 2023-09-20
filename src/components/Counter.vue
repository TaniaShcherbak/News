<template>
    <div>
        {{ counter }}
    </div>
</template>
<script>
export default {
    name: "newCounter",
    props: {
        counter: {
            type: Number,
        }
    },
}
</script>
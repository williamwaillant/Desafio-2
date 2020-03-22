<template>
    <div class="row bg-dark shadow" style="min-width: 100%;">
        <div class="col-2 py-2 d-md-none">
            <span class="text-white" @click="$emit('displayMobileMenu')"><i class="fas fa-bars fa-2x"></i></span>
        </div>
        <div class="col-10 col-md-12 my-auto py-md-2 text-right text-md-left">
            <a class="h4 text-white" href="#">{{ companyName }}</a>
        </div>
    </div>
</template>

<script>
export default {
    name: 'header',
    props: {
        companyName: {
            type: String,
            required: true,
        }
    }
}
</script>

<style scoped>
a:hover {
    text-decoration: none;
}
</style>

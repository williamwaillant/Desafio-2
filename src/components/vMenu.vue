<template>
    <div class="bg-light d-none d-md-block position-fixed" style="z-index: 1;">
        <ul class="nav flex-column sidebar">
            <li class="nav-item" v-for="(link, index) in links" :key="index">
                <a class="nav-link" :class="{ 'active' : index === 0 }" href="#">
                    <i :class="link.icon"></i>
                    {{ link.name }}
                </a>
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: 'Menu',
        computed: {
            links() {
                return [
                    {
                        name: 'Dashborad',
                        icon: 'fab fa-buffer',
                    },
                    {
                        name: 'Tela 2',
                        icon: 'fas fa-chart-area',
                    },
                    {
                        name: 'Tela 3',
                        icon: 'fas fa-home',
                    },
                    {
                        name: 'Tela 4',
                        icon: 'fas fa-users',
                    },
                ]
            }
        }
    }
</script>

<style scoped>
.sidebar .nav-link.active {
    color: #007bff;
}

.sidebar .nav-link {
    font-weight: 500;
    color: #666;
}

.sidebar .nav-link:hover {
    color: #111;
}
</style>

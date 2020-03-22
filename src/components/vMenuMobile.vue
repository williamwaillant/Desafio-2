<template>
    <div>
        <ul class="nav flex-column sidebar w-100 shadow">
            <li class="nav-item bg-light" v-for="(link, index) in links" :key="index">
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
        props: {
            displayMobileMenu: {
                type: Boolean,
                default: false
            }
        },
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

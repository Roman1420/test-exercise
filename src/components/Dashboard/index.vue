<template>
    <div class="dashboard">
        <d-header/>
        <d-sub-header/>
        <d-body/>
    </div>
</template>

<script>
import DHeader from './components/DHeader.vue'
import DSubHeader from './components/DSubHeader.vue'
import DBody from './components/DBody.vue'
export default {
    name: 'Dashboard',
    components: {
        DHeader,
        DSubHeader,
        DBody,
    }
}
</script>

<style lang="scss">
.dashboard {
    display: flex;
    flex-direction: column;
    overflow: hidden;
    background: #fff;
    width: 100%;
    max-width: 1440px;
    box-shadow: 0px 33px 43px rgba(0, 0, 0, 0.1), 0px 9.94853px 12.9632px rgba(0, 0, 0, 0.0651589), 0px 4.13211px 5.38427px rgba(0, 0, 0, 0.05), 0px 1.4945px 1.94738px rgba(0, 0, 0, 0.0348411);
    border-radius: 20px;
}
</style>

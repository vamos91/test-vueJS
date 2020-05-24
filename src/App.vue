<template>
    <div id="app">
        <Header></Header>
        <router-view></router-view>
    </div>
</template>

<script>
import Header from './components/layout/Header'
export default {
    name: 'App',
    components: {
        Header
    }
}
</script>
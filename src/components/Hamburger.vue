<template>
    <div class="hamburger-wrapper pointerable pointerable-darker">
        <img class="menu" src="@/assets/header/hamburger/menu.svg" />
        <img class="menu-text" src="@/assets/header/hamburger/menu-text.svg" />
    </div>
</template>

<script>
export default {}
</script>

<style scoped lang="scss">
.hamburger-wrapper {
    display: flex;
}
.menu {
    margin-right: 20px;
    max-width: 20px;
    height: auto;
}
.menu-text {
    max-width: 60px;
    height: auto;
    width: 100%;
}
</style>

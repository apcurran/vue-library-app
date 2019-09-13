<template>
    <header class="header">
        <h1 class="header-title">My<img class="header-icon" src="../images/open-book.svg"><span>Books</span></h1>
    </header>
</template>

<script>
export default {
    
}
</script>

<style scoped>

.header {
    background-color: #222;
    padding-top: 2em;
    padding-bottom: 2em;
    color: #fff;

    display: flex;
    justify-content: center;
}

.header-icon {
    width: 45px;
    margin-left: .5rem;
    margin-right: .5rem;
    vertical-align: bottom;
}

.header-title span {
    color: #c3def7;
}

</style>

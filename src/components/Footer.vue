<template>
    <footer class="footer">
        <ul class="footer-list">
            <li class="footer-item">Created by: <span>Alex Curran</span></li>
            <li class="footer-item"><a class="footer-item-link" href="https://github.com/apcurran" target="_blank"><img src="../images/social-github-white.svg" alt="GitHub"></a></li>
        </ul>
    </footer>
</template>

<script>
export default {
    
}
</script>

<style scoped>

.footer {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    padding-top: 1em;
    padding-bottom: 1em;

    background-color: #222;
    color: #eee;
    font-size: .85rem;
}

.footer-list {
    list-style: none;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.footer-item {
    margin: .35em 0;
}

.footer-item-link {
    color: #fff;
    text-decoration: none;
    transition: opacity 150ms ease;
}

.footer-item-link:hover {
    opacity: .65;
}

.footer-item span {
    color: #c3def7;
    font-weight: bolder;
}

.footer-item-link img {
    width: 40px;
    fill: #fff;
}

</style>

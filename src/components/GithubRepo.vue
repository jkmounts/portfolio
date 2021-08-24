<template>
    <div class="repo">
        <a href="repo.html_url">{{ repo.name }}</a>
        <p>{{ repo.description }}</p>
    </div>
</template>

<script>
    export default {
        name: 'GithubRepo',
        props: {
            repo: {
                type: Object,
            },
        },
    }
</script>

<style scoped>

.repo {
    width: 75px;
}

a {
    color:black;
    font-size: 1rem;
}

p {
    font-size: 0.75rem;
    margin: 0 0 0.5rem 0;
}

</style>
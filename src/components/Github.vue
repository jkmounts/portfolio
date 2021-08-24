<template>
    <div class="github">
        <div class="header">
            <img src = "../assets/github/GitHub-Mark.png">
            <h2>GitHub</h2>
            <img :src="profile.avatar_url">
        </div>
        <div>
            <a :href="profile.html_url">{{ profile.html_url }}</a>
        </div>
        <div class="repos_container">
            <h3 @click="toggleReposOpen()">Repos: {{ profile.public_repos }}</h3>
            <div class="repos" v-if="reposOpen">
                <github-repo v-for="(repo, index) in repos" :repo="repo" :key="index" />
            </div>
        </div>
    </div>
</template>

<script>
import GithubRepo from './GithubRepo'
    export default {
        name: "Github",
        components: {
            GithubRepo,
        },
        data() {
            return {
                profile: {},
                repos: [],
                reposOpen: false,
            }
        },
        async created () {
            this.profile = await this.getGithubProfile();
            this.repos = await this.getRepos();
        },
        methods: {
            async getGithubProfile() {
                let response = await fetch("https://api.github.com/users/jkmounts");
                const profile = response.json();
                return profile;
            },
            async getRepos() {
                let response = await fetch("https://api.github.com/users/jkmounts/repos");
                const repos = response.json();
                return repos;
            },
            toggleReposOpen() {
                this.reposOpen = !this.reposOpen;
            }
        },    
    }
</script>

<style scoped>

.github {
    border: 2px solid black;
    display: inline-flex;
    flex-flow: column;
}

.header {
    background-color: blueviolet;
    display: flex;
    flex-flow: row nowrap;
    justify-content: center;
    align-items: center;
}

h3 {
    margin: 0;
    padding: 0;
}

.header img {
    width: 3rem;
    border-radius: 100%;
    padding: 1rem
}

a {
    color: orange;
}

.repos {
    display: flex;
    flex-flow: row wrap;
}

</style>
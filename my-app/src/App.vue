<template>
    <form class="form" @submit.prevent>
        <input v-bind:value="title" @input="title = $event.target.value" class="post__input" type="text" placeholder="Название">
        <input v-bind:value="description" @input="description = $event.target.value" class="post__input" type="text"
            placeholder="Описание">
        <input v-bind:value="imgLink" @input="imgLink = $event.target.value" class="post__input" type="text"
            placeholder="URL-изображение">
        <button class="btn" @click="createPost">Добавить объект</button>
    </form>
    <div class="posts">
        <article class="post" v-for="post in posts">
            <img :src="post.imgLink" :alt="post.title" class="post__img">
            <h3 class="post__title">
                {{ post.title }}
            </h3>
            <p class="post__desc">
                {{ post.description }}
            </p>
        </article>
    </div>
</template>

<script>
export default {
    data() {
        return {
            posts: [
                { id: 1, imgLink: "https://cover.imglib.info/uploads/anime/6488/cover/8336bdb4-9468-4ec2-8f16-17ba114b9294.jpg", title: "Санка Рэа", description: "Чихиро Фуруя не заинтересован в чём-либо живом — он помешан на мёртвом, а точнее выразиться, на зомби. Даже после того, как умер его кот, он пытался вернуть его к жизни." },
                { id: 2, imgLink: "https://cover.imglib.info/uploads/anime/24203/cover/c0b71b77-3b47-4afc-b2f5-01cc6c7d2607.jpg", title: "Маленький гражданин", description: "Давайте поможем друг другу и стремимся стать идеальными обычными гражданами" },
                { id: 3, imgLink: "https://cover.imglib.info/uploads/anime/22828/cover/7b3e9c28-dce7-4140-9714-e42a72b10b9b.jpg", title: "Лазарь", description: "Человечество освободилось от болезней и боли благодаря чудодейственному средству под названием «Хапуна», которое разработал" },
            ],
            title: '',
            description: '',
            imgLink: '',
        }
    },
    methods: {
        createPost() {
            const newPost = {
                id: Date.now(),
                title: this.title,
                description: this.description,
                imgLink: this.imgLink,
            };

            this.posts.push(newPost);
            this.title = "";
            this.description = "";
            this.imgLink = "";
        }
    }
}
</script>

<style scoped>
.form {
    display: flex;
    flex-wrap: wrap;
    max-width: 350px;
    gap: 24px;
    padding: 12px;
    border: 1px solid black;
}

.form__input {
    font-size: 16px;
    padding: 8px 12px;
}

.posts {
    display: flex;
    gap: 24px;
    flex-wrap: wrap;
}

.post {
    display: flex;
    flex-direction: column;
    row-gap: 12px;
    max-width: 300px;

    border: 1px solid black;
}

.post__title {
    font-size: 24px;
    font-weight: 700;
}

.post__desc {
    font-size: 16px;
    font-weight: 500;
}
</style>
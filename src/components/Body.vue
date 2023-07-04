<template>
<v-container>
    <v-expansion-panels>
        <v-expansion-panel v-for="(post, idx) in posts">
            <v-expansion-panel-title>
                <v-row>
                    <v-col sm="9">{{ post.title }}</v-col>
                    <v-col sm="3" class="d-flex justify-end">
                        <small>posted by: {{handleName}}</small>
                    </v-col>
                </v-row>
            </v-expansion-panel-title>
            <v-expansion-panel-text>
                <div class="mb-5">
                    <v-img v-if="post.imgBool" width="300" :src="post.img"></v-img>
                    {{ post.text }}
                </div>
                <v-btn size="small" @click="viewComment(idx)">{{ !post.viewComment ? "Show Comments" : "Hide Comments" }}</v-btn>
                <v-card class="mt-5" :key="post.id" v-if="post.viewComment" :height="post.comments.length > 5 ? 300 : ''">
                    <v-virtual-scroll v-if="post.comments.length > 0"  :items="post.comments">
                        <template v-slot:default="item">
                            <v-card-text>
                                <v-row>
                                    <v-col sm="10">{{ item.item.comment }}</v-col>
                                    <v-col sm="2" class="d-flex justify-end">
                                        <div>
                                            <small>3-10-2023</small>
                                            <v-divider></v-divider>
                                            <p>{{ item.item.user.handle }}</p>
                                        </div>
                                    </v-col>
                                </v-row>
                            </v-card-text>
                            <v-divider></v-divider>
                        </template>
                    </v-virtual-scroll>
                    <v-card-text v-else>No comments</v-card-text>
                </v-card>
            </v-expansion-panel-text>
            
        </v-expansion-panel>
    </v-expansion-panels>
</v-container>
</template>

<script lang="ts">

    export default {
        data() {
            return {
                handleName : "negatron",
                posts: [
                    {"id": 0, "text": "do not fuck with me u got it? fucking ego kid", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "Noob gets destroyed in herald", viewComment: false, comments: [{"id":1, comment: "asdasdads", user: {"id": 100, handle: "negatron" }}]},
                    {"id": 1, "text": "Praise the lord with you my brothers and sisters, today we are blessed with the present of being alive", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "Prayer", viewComment: false,comments: [{"id":1, comment: "asdasdads", user: {"id": 100, handle: "negatron" }}]},
                    {"id": 2, "text": "yeah", img: "", imgBool: false, title: "xadssad", viewComment: false, comments: [{"id":1, comment: "asdasdads", user: {"id": 100, handle: "negatron" }}]},
                    {"id": 3, "text": "qwqe", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "yeah", viewComment: false, comments: [{"id":1, comment: "asdasdads", user: {"id": 100, handle: "negatron" }}]},
                    {"id": 4, "text": "yeah", img: "", imgBool: false, title: "xadssad", viewComment: false,comments: [{"id":1, comment: "asdasdads", user: {"id": 100, handle: "negatron" }}]},
                    {"id": 5, "text": "qwrqwt", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "bro", viewComment: false, comments: [{"id":1, comment: "asdasdads", user: {"id": 100, handle: "negatron" }}]},
                    {"id": 6, "text": "yeah", img: "", imgBool: false, title: "brother", viewComment: false,comments: [{"id":1, comment: "asdasdads", user: {"id": 100, handle: "negatron" }}]},
                    {"id": 7, "text": "yeah", img: "", imgBool: false, title: "in christ", viewComment: false,comments: []},
                    {"id": 8, "text": "tqwt", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "xddd", viewComment: false, comments: [{"id":1, comment: "asdasdads", user: {"id": 100, handle: "negatron" }}]},
                    {"id": 9, "text": "qwqwtqwy", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "dasd", viewComment: false, comments: [{"id":1, comment: "asdasdads", user: {"id": 100, handle: "negatron" }}]},
                    {"id": 10, "text": "qwqwtqwy", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "dasd", viewComment: false, comments: [{"id":1, comment: "asdasdads", user: {"id": 100, handle: "negatron" }}]},
                    {"id": 11, "text": "qwqwtqwy", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "dasd", viewComment: false, comments: [{"id":1, comment: "asdasdads", user: {"id": 100, handle: "negatron" }}]},
                    {"id": 12, "text": "qwqwtqwy", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "dasd", viewComment: false, comments: [{"id":1, comment: "asdasdads", user: {"id": 100, handle: "negatron" }}]},
                    {"id": 13, "text": "qwqwtqwy", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "dasd", viewComment: false, comments: [{"id":1, comment: "asdasdads", user: {"id": 100, handle: "negatron" }}]},
                    {"id": 14, "text": "qwqwtqwy", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "dasd", viewComment: false, comments: [{"id":1, comment: "asdasdads", user: {"id": 100, handle: "negatron" }}]},
                    {"id": 15, "text": "qwqwtqwy", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "dasd", viewComment: false, comments: [{"id":1, comment: "asdasdads", user: {"id": 100, handle: "negatron" }}]},
                    {"id": 16, "text": "qwqwtqwy", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "dasd", viewComment: false, comments: [{"id":1, comment: "asdasdads", user: {"id": 100, handle: "negatron" }}]},
                    {"id": 17, "text": "qwqwtqwy", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "dasd", viewComment: false, comments: [{"id":1, comment: "asdasdads", user: {"id": 100, handle: "negatron" }}]},
                    {"id": 18, "text": "qwqwtqwy", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "dasd", viewComment: false, comments: [{"id":1, comment: "asdasdads", user: {"id": 100, handle: "negatron" }}]},
                    {"id": 19, "text": "qwqwtqwy", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "dasd", viewComment: false, comments: [{"id":1, comment: "asdasdads", user: {"id": 100, handle: "negatron" }}]},
                ] 
            }
        },
        methods: {
            viewComment(idx:number) {
                this.posts[idx].viewComment = !this.posts[idx].viewComment

                console.log(this.posts[idx])
            }
        }
    }

    // let posts:{id: number, text: string, img: string, imgBool: boolean, title: string, viewComment: boolean, comments:{id:number, comment: string, user: {id: number, handle:string}}[]}[];

</script>

<style>
.v-card {
  display: flex !important;
  flex-direction: column;
}

.v-card__text {
  flex-grow: 1;
  overflow: auto;
}
</style>
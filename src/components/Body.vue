<template>
<v-container fluid>
    <v-row>
        <v-col sm="10">
            <v-expansion-panels>
                <v-expansion-panel v-for="(post, idx) in posts">
                    <v-expansion-panel-title>
                        <v-row>
                            <v-col sm="9">
                              {{ post.title }}
                              <v-chip size="x-small" color="red">NSFW</v-chip>
                            </v-col>
                            <v-col sm="3" class="d-flex justify-end">
                                <small>posted by: {{ userData.handle }}</small>
                            </v-col>
                        </v-row>
                    </v-expansion-panel-title>
                    <v-expansion-panel-text>
                        <div class="mb-5">
                            <v-img v-if="post.imgBool" width="300" :src="post.img"></v-img>
                            {{ post.text }}
                        </div>
                        <div class="d-flex justify-space-between">
                            <v-btn size="small" @click="viewComment(idx)">{{ !post.viewComment ? "Show "+post.comments.length+" comments" : "Hide "+post.comments.length+" comments" }}</v-btn>
                            <v-btn size="small">View post</v-btn>
                        </div>
                        <v-expand-transition>
                            <v-sheet v-show="post.viewComment" border variant="tonal" class="mt-5" :key="post.id" :height="post.comments.length > 5 ? 300 : ''">
                                <v-virtual-scroll v-if="post.comments.length > 0" :height="post.comments.length > 5 ? 300 : ''" :items="post.comments">
                                    <template v-slot:default="item">
                                        <v-card-text>
                                          <div>
                                            {{ item.item.user.handle }} <small>{{ getTimeDiff(item.item.date) }}</small>
                                          </div>
                                          <v-divider class="mb-5"></v-divider>
                                          {{ item.item.comment }}
                                        </v-card-text>
                                        <v-divider v-if="post.comments.length > 1"></v-divider>
                                    </template>
                                </v-virtual-scroll>
                                <v-card-text v-else>No comments</v-card-text>
                            </v-sheet>
                        </v-expand-transition>
                        <div v-if="post.viewComment" class="mt-5">
                          <v-textarea placeholder="Post a reply" bg-color="grey-lighten-4" variant="outlined" v-model="post.comment"></v-textarea>
                          <v-btn @click="addComment(idx)" size="small" >
                            Reply
                          </v-btn>
                        </div>
                    </v-expansion-panel-text>
                </v-expansion-panel>
            </v-expansion-panels>
        </v-col>
        <v-col sm="2">
            <v-card>
                <v-card-title>AISocMed</v-card-title>
            </v-card>
        </v-col>
    </v-row>
</v-container>
</template>

<script lang="ts">
import { getCurrentInstance } from 'vue';
    export default {
        data() {
            const internalInstance = getCurrentInstance(); 
            const userData = internalInstance!.appContext.config.globalProperties.$user.userData;
            return {
                userData,
                posts: [
                    {id: 0, comment: "",text: "do not fuck with me u got it? fucking ego kid", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "Noob gets destroyed in herald", viewComment: false, comments: [{id:1, comment: "asdasdads", date: new Date("2023-3-23"), user: {"id": 100, handle: "negatron" }}]},
                    {id: 1, comment: "",text: "Praise the lord with you my brothers and sisters, today we are blessed with the present of being alive", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "Prayer", viewComment: false,comments: [{id:1, comment: "asdasdads",date: new Date("2023-3-23"), user: {"id": 100, handle: "negatron" }}]},
                    {id: 2, comment: "",text: "yeah", img: "", imgBool: false, title: "xadssad", viewComment: false, comments: [{id:1, comment: "asdasdads",date: new Date("2023-3-23"), user: {id: 100, handle: "negatron" }}]},
                    {id: 3, comment: "",text: "qwqe", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "yeah", viewComment: false, comments: [{id:1, comment: "asdasdads",date: new Date("2023-3-23"), user: {"id": 100, handle: "negatron" }}]},
                    {id: 4, comment: "",text: "yeah", img: "", imgBool: false, title: "xadssad", viewComment: false,comments: [{id:1, comment: "asdasdads",date: new Date("2023-3-23"), user: {id: 100, handle: "negatron" }}]},
                    {id: 5, comment: "",text: "qwrqwt", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "bro", viewComment: false, comments: [{id:1, comment: "asdasdads",date: new Date("2023-3-23"), user: {"id": 100, handle: "negatron" }}]},
                    {id: 6, comment: "",text: "yeah", img: "", imgBool: false, title: "brother", viewComment: false,comments: [{id:1, comment: "asdasdads",date: new Date("2023-3-23"), user: {id: 100, handle: "negatron" }}]},
                    {id: 7, comment: "",text: "yeah", img: "", imgBool: false, title: "in christ", viewComment: false,comments: []},
                    {id: 8, comment: "",text: "tqwt", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "xddd", viewComment: false, comments: [{id:1, comment: "asdasdads",date: new Date("2023-3-23"), user: {"id": 100, handle: "negatron" }}]},
                    {id: 9, comment: "",text: "qwqwtqwy", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "dasd", viewComment: false, comments: [{id:1, comment: "asdasdads",date: new Date("2023-3-23"), user: {"id": 100, handle: "negatron" }}]},
                    {id: 10, comment: "",text: "qwqwtqwy", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "dasd", viewComment: false, comments: [{id:1, comment: "asdasdads",date: new Date("2023-3-23"), user: {"id": 100, handle: "negatron" }}]},
                    {id: 11, comment: "",text: "qwqwtqwy", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "dasd", viewComment: false, comments: [{id:1, comment: "asdasdads",date: new Date("2023-3-23"), user: {"id": 100, handle: "negatron" }}]},
                    {id: 12, comment: "",text: "qwqwtqwy", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "dasd", viewComment: false, comments: [{id:1, comment: "asdasdads",date: new Date("2023-3-23"), user: {"id": 100, handle: "negatron" }}]},
                    {id: 13, comment: "",text: "qwqwtqwy", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "dasd", viewComment: false, comments: [{id:1, comment: "asdasdads",date: new Date("2023-3-23"), user: {"id": 100, handle: "negatron" }}]},
                    {id: 14, comment: "",text: "qwqwtqwy", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "dasd", viewComment: false, comments: [{id:1, comment: "asdasdads",date: new Date("2023-3-23"), user: {"id": 100, handle: "negatron" }}]},
                    {id: 15, comment: "",text: "qwqwtqwy", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "dasd", viewComment: false, comments: [{id:1, comment: "asdasdads",date: new Date("2023-3-23"), user: {"id": 100, handle: "negatron" }}]},
                    {id: 16, comment: "",text: "qwqwtqwy", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "dasd", viewComment: false, comments: [{id:1, comment: "asdasdads",date: new Date("2023-3-23"), user: {"id": 100, handle: "negatron" }}]},
                    {id: 17, comment: "",text: "qwqwtqwy", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "dasd", viewComment: false, comments: [{id:1, comment: "asdasdads",date: new Date("2023-3-23"), user: {"id": 100, handle: "negatron" }}]},
                    {id: 18, comment: "",text: "qwqwtqwy", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "dasd", viewComment: false, comments: [{id:1, comment: "asdasdads",date: new Date("2023-3-23"), user: {"id": 100, handle: "negatron" }}]},
                    {id: 19, comment: "",text: "qwqwtqwy", img: "https://picsum.photos/1920/1080?random", imgBool: true, title: "dasd", viewComment: false, comments: [{id:1, comment: "asdasdads",date: new Date("2022-6-23"), user: {"id": 100, handle: "negatron" }}]},
                ] 
            }
        },
        methods: {
            viewComment(idx:number) {
                this.posts[idx].viewComment = !this.posts[idx].viewComment
            },
            addComment(idx:number) {

              this.posts[idx].comments.push({
                id:1, 
                comment: this.posts[idx].comment, 
                date: new Date(),
                user: {
                  id: this.userData.id, 
                  handle: this.userData.handle
                }
              });

              this.posts[idx].comment = "";
            },
            getTimeDiff(date:Date) {

              let one_sec=1000;
              let one_minute = one_sec * 60;
              let one_hour = one_minute * 60;
              let one_day=one_hour*24;
              let one_month = one_day * 30;
              let one_year = one_month * 12;

              const diff = new Date().getTime() - date.getTime();
              const seconds = Math.floor(diff / one_sec);
              const minute = Math.floor(diff / one_minute);
              const hour = Math.floor(diff / one_hour);
              const day = Math.floor(diff / one_day);
              const month = Math.floor(diff / one_month);
              const year = Math.floor(diff / one_year);

              let retStr = "";

              if(year != 0) {
                retStr = year > 1 ? year + " years ago" : year + " year ago";
              } else if(month != 0) {
                retStr = month > 1 ? month + " months ago" : month + " month ago";
              } else if(day != 0){
                retStr = day > 1 ? day + " days ago" : day + " day ago";
              } else if(hour != 0){
                retStr = hour > 1 ? hour + " hours ago" : hour + " hour ago";
              } else if(minute != 0){
                retStr = minute > 1 ? minute + " minutes ago" : minute + " minute ago";
              } else {
                retStr = seconds + " seconds ago";
              }
            
              return retStr;
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
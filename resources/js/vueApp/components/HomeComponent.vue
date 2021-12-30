<template>
    <div class="container has-text-centered" v-cloak id="app">
        <h1 class="title">
            Stringee API Call Video
        </h1>

        <div>
            <button class="button is-primary" v-if="!room" @click="createRoom">
                Tạo Meeting
            </button>

            <button class="button is-info" v-if="!room" @click="joinWithId">
                Join Meeting
            </button>

            <button class="button is-info" v-if="room" @click="publish(true)">
                Share Desktop
            </button>
        </div>

        <div v-if="roomId" class="info">
            <p>
                Link to join this room:
                <a v-bind:href="roomUrl" target="_blank">{{roomUrl}}</a>.
            </p>
            <p>Room Id: <code>{{roomId}}</code></p>
        </div>

        <div id="videos"></div>
    </div>
</template>

<script>
import CallVideoMixin
    from './CallVideoMixin';

export default {
    mixins: [CallVideoMixin],
    data() {
        return {
            userToken: "",
            roomId: "",
            roomToken: "",
            room: undefined,
            callClient: undefined
        }
    }
}
</script>

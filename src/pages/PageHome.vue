<template>
  <q-page>
    <div class="q-py-lg q-px-md row items-end q-col-gutter-md">
      <div class="col">
        <q-input
          bottom-slots
          class="new-mweet"
          v-model="neMweetContent"
          placeholder="Whats happening?"
          counter
          autogrow
          maxlength="280"
        >
          <template v-slot:before>
            <q-avatar size="xl">
              <img
                src="https://pbs.twimg.com/profile_images/1349722974677467139/Sm4DrmsI_400x400.jpg"
              />
            </q-avatar>
          </template>
        </q-input>
      </div>
      <div class="col col-shrink">
        <q-btn
          :disable="!neMweetContent"
          class="q-mb-lg"
          unelevated
          no-caps
          rounded
          color="primary"
          label="Mweet"
        />
      </div>
    </div>
    <q-separator class="divider" size="10px" color="grey-2" />
    <q-list separator>
      <q-item v-for="mweet in mweets" :key="mweet.date" class="q-py-md">
        <q-item-section avatar top>
          <q-avatar size="xl">
            <img
              src="https://pbs.twimg.com/profile_images/1349722974677467139/Sm4DrmsI_400x400.jpg"
            />
          </q-avatar>
        </q-item-section>

        <q-item-section>
          <q-item-label class="text-subtitle1"
            ><strong> Azraf Al Monzim </strong>
            <span class="text-grey-7"> @monzim </span>
          </q-item-label>
          <q-item-label class="mweet-content text-body1">{{
            mweet.content
          }}</q-item-label>
          <div class="mweet-icons row justify-between q-mt-sm">
            <q-btn
              flat
              round
              color="grey"
              icon="far fa-comment"
              size="sm"
            /><q-btn
              flat
              round
              color="grey"
              icon="fas fa-retweet"
              size="sm"
            /><q-btn flat round color="grey" icon="far fa-heart" size="sm" />
            <q-btn flat round color="grey" icon="fas fa-trash" size="sm" />
          </div>
        </q-item-section>

        <q-item-section side top>{{
          mweet.date | relativeDate
        }}</q-item-section>
      </q-item>
    </q-list>
  </q-page>
</template>
  
<script>
import { formatDistance } from "date-fns";

export default {
  name: "PageHome",
  data() {
    return {
      neMweetContent: "",
      mweets: [
        {
          content:
            "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ipsa quasi quia earum. Laboriosam sit modi impedit voluptatem molestiae tenetur illo? Laudantium ut ullam harum, sed doloribus velit ea sequi nemo?",
          date: 1615576884993,
        },
        {
          content:
            "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ipsa quasi quia earum. Laboriosam sit modi impedit voluptatem molestiae tenetur illo? Laudantium ut ullam harum, sed doloribus velit ea sequi nemo?",
          date: 1615576985007,
        },
      ],
    };
  },
  filters: {
    relativeDate(value) {
      return formatDistance(value, new Date());
    },
  },
};
</script>


<style lang="sass">
.new-mweet
textarea
  font-size: 19px
  line-height: 1.4 !important
.divider
  border-top: 1px solid
  border-bottom: 1px solid
  border-color: $grey-4
.mweet-content
  white-space: pre-line
.mweet-icons
  margin-left: -5px
</style>
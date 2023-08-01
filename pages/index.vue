<template>
  <v-row justify="center">
    <v-col cols="12" md="9">
      <v-sheet class="ma-2" height="600px">
        <v-btn class="ma-2"
          ><v-icon>mdi-export-variant</v-icon>作成した時間割を保存する</v-btn
        ><v-calendar ref="calendar" v-model="value"></v-calendar
      ></v-sheet>
      <v-card class="ma-2 pa-2">
        教科：<v-autocomplete max-width="50%"></v-autocomplete>
        <v-spacer></v-spacer>
        時間：<v-autocomplete max-width="50%"></v-autocomplete>
      </v-card>
      <v-card class="ma-2 pa-2" v-for="course in courses">
        <v-card-title
          >{{ course.title }}
          <v-spacer></v-spacer>
          <span class="grey--text">{{ course.number }}</span>
        </v-card-title>
        <v-card-subtitle>{{ course.instructor }}</v-card-subtitle>
        <v-card-actions
          ><v-chip>{{ course.subject }}</v-chip
          ><v-spacer></v-spacer>
          <v-btn><v-icon>mdi-heart</v-icon>お気に入り</v-btn
          ><v-btn><v-icon>mdi-plus</v-icon>時間割に追加</v-btn></v-card-actions
        >
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: "IndexPage",
  data() {
    return {
      today: new Date().today,

      courses: [
        {
          number: "101",
          title: "共通テスト現代文演習A",
          instructor: "Instructor-1",
          subject: "現代文B",
          schedule: [],
        },
        {
          number: "102",
          title: "共通テスト現代文演習B",
          instructor: "Instructor-2",
          subject: "現代文B",
          schedule: [],
        },
        {
          number: "103",
          title: "古文（単語・文法）演習",
          instructor: "Instructor-3",
          subject: "古典B",
          schedule: [],
        },
      ],
    };
  },
  mounted() {
    this.$refs.calendar.checkChange();
  },
  methods: {
    viewDay({ date }) {
      this.focus = date;
      this.type = "day";
    },
    getEventColor(event) {
      return event.color;
    },
    setToday() {
      this.focus = "";
    },
    prev() {
      this.$refs.calendar.prev();
    },
    next() {
      this.$refs.calendar.next();
    },
    showEvent({ nativeEvent, event }) {
      const open = () => {
        this.selectedEvent = event;
        this.selectedElement = nativeEvent.target;
        requestAnimationFrame(() =>
          requestAnimationFrame(() => (this.selectedOpen = true))
        );
      };

      if (this.selectedOpen) {
        this.selectedOpen = false;
        requestAnimationFrame(() => requestAnimationFrame(() => open()));
      } else {
        open();
      }

      nativeEvent.stopPropagation();
    },
    updateRange({ start, end }) {
      const events = [];

      const min = new Date(`${start.date}T00:00:00`);
      const max = new Date(`${end.date}T23:59:59`);
      const days = (max.getTime() - min.getTime()) / 86400000;
      const eventCount = this.rnd(days, days + 20);

      for (let i = 0; i < eventCount; i++) {
        const allDay = this.rnd(0, 3) === 0;
        const firstTimestamp = this.rnd(min.getTime(), max.getTime());
        const first = new Date(firstTimestamp - (firstTimestamp % 900000));
        const secondTimestamp = this.rnd(2, allDay ? 288 : 8) * 900000;
        const second = new Date(first.getTime() + secondTimestamp);

        events.push({
          name: this.names[this.rnd(0, this.names.length - 1)],
          start: first,
          end: second,
          color: this.colors[this.rnd(0, this.colors.length - 1)],
          timed: !allDay,
        });
      }

      this.events = events;
    },
    rnd(a, b) {
      return Math.floor((b - a + 1) * Math.random()) + a;
    },
  },
};
</script>

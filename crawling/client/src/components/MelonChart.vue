<template>
  <div>
    <v-data-table
      :headers="headers"
      :items="desserts"
      :search="search"
      :pagination.sync="pagination"
      hide-actions
      class="elevation-1"
    >
      <template slot="headerCell" slot-scope="props">
        <v-tooltip bottom>
          <span slot="activator">
            {{ props.header.text }}
          </span>
          <span>
            {{ props.header.text }}
          </span>
        </v-tooltip>
      </template>
      <template slot="items" slot-scope="props">
        <td class="text-xs-center">{{ props.item.rank }}</td>
        <td class="text-xs-center">{{ props.item.title }}</td>
        <td class="text-xs-center">{{ props.item.singer }}</td>
      </template>
    </v-data-table>
    <div class="text-xs-center pt-2">
      <v-pagination v-model="pagination.page" :length="pages"></v-pagination>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'MelonChart',
    data () {
      return {
        search: '',
        pagination: {},
        selected: [],
        headers: [
          { text: 'Rank (Top 100)', align: 'center', value: 'rank' },
          { text: 'Title', align: 'center', value: 'title' },
          { text: 'Singer', align: 'center', value: 'singer' }
        ],
        desserts: [
          {
            value: false,
            rank: 1,
            title: 'Power Up',
            singer: 'Red Velvet (레드벨벳)',
          },
          {
            value: false,
            rank: 2,
            title: 'Way Back Home',
            singer: '숀 (SHAUN)'
          },
          {
            value: false,
            rank: 3,
            title: 'SoulMate (Feat. 아이유)',
            singer: '지코 (ZICO)'
          },
          {
            value: false,
            rank: 4,
            title: 'Dance The Night Away',
            singer: 'TWICE (트와이스)'
          },
          {
            value: false,
            rank: 5,
            title: '뚜두뚜두 (DDU-DU DDU-DU)',
            singer: 'BLACKPINK'
          },
          {
            value: false,
            rank: 6,
            title: '너나 해 (Egotistic)',
            singer: '마마무(Mamamoo)'
          },
          {
            value: false,
            rank: 7,
            title: '1도 없어',
            singer: 'Apink (에이핑크)'
          },
          {
            value: false,
            rank: 8,
            title: '여행',
            singer: '볼빨간사춘기'
          },
          {
            value: false,
            rank: 9,
            title: 'Forever Young',
            singer: 'BLACKPINK'
          },
          {
            value: false,
            rank: 10,
            title: '모든 날, 모든 순간 (Every day, Every Moment)',
            singer: '폴킴'
          }
        ]
      }
    },
    computed: {
      pages () {
        if (this.pagination.rowsPerPage == null ||
          this.pagination.totalItems == null
        ) return 0

        return Math.ceil(this.pagination.totalItems / this.pagination.rowsPerPage)
      }
    }
  }
</script>
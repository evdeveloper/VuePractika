<template>
  <div class="conatiner">
    <div class="user-card">
      <h1>Научу зарабатывать от 50 000р. в час</h1>
      <div class="main-info">
        <img src="../assets/коуч.jpg" width="500px">
        <div class="info">
          <h2>{{ upperAuthorName }}</h2>
          <strong>Бизнес-коуч</strong>
          <ul class="list">
            <li>Учу делать РЕАЛЬНЫЕ бабки, на себя просто не хватило времени</li>
            <li>НЕ знаю, что такое "Успешный Успех", но знаю, что нужно ТЕБЕ!</li>
            <li>Пообещал, что побреюсь, когда кого-нибудь ОБМАНУ.</li>
          </ul>
        </div>
      </div>
      <p>Участников: {{ users.length }}</p>
      <ul>
        <li
        v-for="(item, index) in users"
        :key="index"
        >
        {{ `${index + 1}. ${getFullName(item)}` }}
        </li>
      </ul>

      <ul>
        <li
        v-for="(value, key, index) in users[0]"
        :key="index"
        >
        {{ key }}
        </li>
      </ul>

      <button
        type="button"
        @click="currentPage--"
      >
        Пред.
      </button>
      <button
        type="button"
        v-for="page in pages"
        :key="page"
        @click="currentPage = page"
      >
      {{ page }}
      </button>
      <button
        type="button"
        @click="currentPage++"
      >
        След.
      </button>

      
      <p>Страница: {{ currentPage }} из {{ pages }} </p>
    </div>
    <p>Поиск:</p>
    <input 
    type="text"
    @input="searchText = $event.target.value"

    >
    <span>Всего имен: {{ names.length }}</span>
    <span>Совпадений: {{ searchInput().length }}</span>
    <ul class="list">
      <li
      v-for="(name, index) in searchInput()"
      :key="index"
      >
      {{ name }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'UserCard',
  data() {
    return {
      searchText: '',
      names: ['Данил', 'Василий', 'Дмитрий', 'Григорий', 'Максим'],
      lastName: 'Петров',
      firstName: 'Максим',
      secondName: 'Генадьевич',
      users: [
        {
          firstName: 'Игнатий',
          secondName: 'Иларионович',
          lastName: 'Богатов'
        },
        {
          firstName: 'Игнатий',
          secondName: 'Иларионович',
          lastName: 'Богатов'
        },
        {
          firstName: 'Игнатий',
          secondName: 'Иларионович',
          lastName: 'Богатов'
        }
      ],
      pages: 3,
      currentPage: 1

    }
  },
  computed: {
    upperAuthorName() {
      // `this` указывает на экземпляр vm
      return `${this.lastName} ${this.firstName} ${this.secondName}`.toUpperCase()
    }
  },
  methods: {
    getFullName(user) {
      return `${user.lastName} ${user.firstName} ${user.secondName}`.toUpperCase()
    },
    loadUser(page) {
      console.log(`Загрузка пользователей, страница: ${page}`)
    },
    searchInput() {
      return this.names.filter(name => name.toLowerCase().includes(this.searchText.toLowerCase()))
    }
  },
  watch: {
    currentPage(newPage) {
      this.loadUser(newPage);
    }
  }
}

</script>

<style scoped>
  .user-card {
    margin-top: 40px;
  }
  ul {
    list-style: none;
    padding: 0;
  }
  li {
    margin-bottom: 5px;
  }
  .main-info {
    display: flex;
  }

  .info {
    margin-left: 50px;
  }
  h2 {
    margin-bottom: 14px;
  }

</style>


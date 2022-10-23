<template>
  <v-app>
    <v-main>
      <v-container>
        <h1 class="text-center mb-1">Портфолио</h1>
        <v-divider></v-divider>
        <v-col cols="12" class="py-0 d-flex justify-center">
          <v-btn-toggle v-model="activeFilter" color="primary" group borderless>
            <v-btn class="mx-1 my-0" value="all">              
              <v-icon left>mdi-format-list-bulleted</v-icon>
              <span>All</span>
            </v-btn>
            <v-btn class="mx-1 my-0" value="react">
              <v-icon left>mdi-react</v-icon>
              <span>React</span>
            </v-btn>
            <v-btn class="mx-1 my-0" value="javascript">
              <v-icon left>mdi-language-javascript</v-icon>
              <span>JavaScript</span>
            </v-btn>
          </v-btn-toggle>
        </v-col>
        <v-divider></v-divider>
        <v-row class="mt-3">
          <ProjectCard
            v-for="project in filtered"
            :key="project.id"
            :item="project"
          />
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import { v4 } from 'uuid';
import ProjectCard from './components/ProjectCard.vue';

export default {
  name: 'App',
  components: {
    ProjectCard,
  },
  data: () => ({
    activeFilter: 'all',
    projects: [
      {
        id: v4(),
        title: 'Retro Game',
        desc: 'Двухмерная игра в стиле фэнтези, где игроку предстоит выставлять своих персонажей против персонажей нечисти. После каждого раунда, восстанавливается жизнь уцелевших персонажей игрока и повышается их уровень. Максимальный уровень - 4.',
        stack: 'javascript',
        imagesUrl: 'https://imageup.ru/img99/4050490/retro-game-min.jpg',
        githubUrl: 'https://github.com/lekseff/RetroGame',
        linkUrl: 'https://lekseff.github.io/RetroGame/',
      },
      {
        id: v4(),
        title: 'Trello',
        desc: 'Доска состоящая из колонок, в каждой колонке может быть несколько карточек.',
        stack: 'javascript',
        imagesUrl: 'https://imageup.ru/img282/4050491/trello-min.jpg',
        githubUrl: 'https://github.com/lekseff/Trello',
        linkUrl: 'https://lekseff.github.io/Trello/',
      },
      {
        id: v4(),
        title: 'Чат',
        desc: 'В данном проекте имеется серверная и клиентская часть. Соединение устанавливается через WebSocket. Серверная часть реализована с помощью Express.',
        stack: 'javascript',
        imagesUrl: 'https://imageup.ru/img174/4050492/chat-min.jpg',
        githubUrl: 'https://github.com/lekseff/Messenger__Frontend',
        linkUrl: '',
      },
      {
        id: v4(),
        title: 'Список товаров',
        desc: 'Редактор списка, который позволяет добавлять, редактировать и удалять записи.',
        stack: 'javascript',
        imagesUrl: 'https://imageup.ru/img203/4050493/list-editor-min.jpg',
        githubUrl: 'https://github.com/lekseff/AHJ_5-2',
        linkUrl: 'https://lekseff.github.io/AHJ_5-2/',
      },
      {
        id: v4(),
        title: 'Галерея изображений с проверкой URL',
        desc: 'Добавляет изображение по ссылке в галерею. ',
        stack: 'javascript',
        imagesUrl: 'https://imageup.ru/img148/4050495/image-gallery-min.jpg',
        githubUrl: 'https://github.com/lekseff/AHJ_3-3',
        linkUrl: 'https://lekseff.github.io/AHJ_3-3/',
      },
      {
        id: v4(),
        title: 'TOP Tasks List',
        desc: 'Список задач, который позволяет добавлять, редактировать, удалять и закреплять задачи. Также есть поиск по задачам.',
        stack: 'avascript',
        imagesUrl: 'https://imageup.ru/img222/4050496/top-task-list-min.jpg',
        githubUrl: 'https://github.com/lekseff/AHJ_3-2',
        linkUrl: 'https://lekseff.github.io/AHJ_3-2/',
      },
      {
        id: v4(),
        title: 'Игра с гоблинами',
        desc: 'Увлекательная игра в которой нужно попадать по появляющемуся гоблину. В ростом количества попаданий скорость игры возрастает.',
        stack: 'javascript',
        imagesUrl: 'https://imageup.ru/img152/4050497/goblin-game-min.jpg',
        githubUrl: 'https://github.com/lekseff/AHJ_3-1',
        linkUrl: 'https://lekseff.github.io/AHJ_3-1/',
      },
      {
        id: v4(),
        title: 'Credit Card Validator',
        desc: 'Валидатор позволяет по номеру карты определить одну из платежных систем: Visa, Mastercard, Мир, Maestro, Amexp, Discover, Dinners, Unionpay, Jcb',
        stack: 'javascript',
        imagesUrl: 'https://imageup.ru/img13/4050498/card-validator-min.jpg',
        githubUrl: 'https://github.com/lekseff/AHJ_4_1',
        linkUrl: 'https://lekseff.github.io/AHJ_4_1/',
      },
      {
        id: v4(),
        title: 'Modern Image Manager',
        desc: 'Позволяет добавлять файлы в галерею через DnD. Достаточно перетащить файл из проводника в поле или щелкнуть по нему для добавления через выбор файлов.',
        stack: 'javascript',
        imagesUrl: 'https://imageup.ru/img202/4050499/modern-gallery-min.jpg',
        githubUrl: 'https://github.com/lekseff/Modern-Image-Manager',
        linkUrl: 'https://lekseff.github.io/Modern-Image-Manager/',
      },
      {
        id: v4(),
        title: 'Timeline',
        desc: 'Проект "Timeline" - некая лента постов человека, где он может прикреплять текстовые посты, а также записывать аудио в привязке к своей геопозиции.',
        stack: 'javascript',
        imagesUrl: 'https://imageup.ru/img285/4050500/timeline-min.jpg',
        githubUrl: 'https://github.com/lekseff/Timeline',
        linkUrl: 'https://lekseff.github.io/Timeline/',
      },
      {
        id: v4(),
        title: 'Онлайн магазин',
        desc: 'Небольшой онлайн магазин.',
        stack: 'react',
        imagesUrl: 'https://imageup.ru/img19/4050480/bosanoga.jpg',
        githubUrl: 'https://github.com/lekseff/online-store',
        linkUrl: 'https://lekseff.github.io/online-store/',
      },
      {
        id: v4(),
        title: 'Учёт тренировок',
        desc: 'Небольшое приложение, которое хранит данные о тренировках (прогулках).',
        stack: 'react',
        imagesUrl: 'https://imageup.ru/img205/4050502/training-min.jpg',
        githubUrl: 'https://github.com/lekseff/Training_accounting',
        linkUrl: 'https://lekseff.github.io/Training_accounting/',
      },
      {
        id: v4(),
        title: 'Мировые часы',
        desc: 'Часы показывающие время в разных часовых поясах',
        stack: 'react',
        imagesUrl: 'https://imageup.ru/img51/4050504/clock-min.jpg',
        githubUrl: 'https://github.com/lekseff/World-Clock',
        linkUrl: 'https://lekseff.github.io/World-Clock/',
      },
      {
        id: v4(),
        title: 'Бот',
        desc: 'Бот предназначен как для хранения информации в виде текстовых сообщений, изображений, аудио и видео файлов. Также бот имеет интеграцию с несколькими сервисами API. Он может получать погоду используя Ваше местоположение, новости, курсы таких валют как доллар(USD), евро(EUR), Bitcoin(BTC). В данном проекте имеется серверная часть.',
        stack: 'javascript',
        imagesUrl: 'https://imageup.ru/img157/4050489/bot-min.jpg',
        githubUrl: 'https://github.com/lekseff/Bot_Frontend',
        linkUrl: '',
      }, 
      {
        id: v4(),
        title: 'Конвертер цветов из HEX в RGB',
        desc: 'Показывает представление цвета в формате RGB и меняет цвет фона. Нужно ввести 7 символов (включая решётку), чтобы получить результат.',
        stack: 'react',
        imagesUrl: 'https://imageup.ru/img74/4050501/converter-min.jpg',
        githubUrl: 'https://github.com/lekseff/Hex_to_RGB_converter',
        linkUrl: 'https://lekseff.github.io/Hex_to_RGB_converter/',
      },
    ],
    filters: [
      { title: 'Все', value: 'all' },
      { title: 'React', value: 'react' },
      { title: 'JavaScript', value: 'javascript' },
    ],
  }),
  computed: {
    filtered () {
      if (this.activeFilter === 'all') {
        return this.projects
      } else {
        return this.projects.filter(item => item.stack === this.activeFilter)
      }      
    }
  }
};
</script>

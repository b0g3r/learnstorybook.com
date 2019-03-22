---
title: "Начало работы"
tocTitle: "Начало работы"
description: "Устанавливаем Vue Storybook в окружение для разработки"
---

# Начало работы

Storybook работает вместе с твоим приложением в режиме разработки. Он помогает тебе строить UI компоненты, изолированные от бизнес-логики и контекста твоего приложения. Это редакция Learn Storybook для Vue; также существуют редакции для [React](/react/en/get-started) и [Angular](/angular/en/get-started).

![Storybook и твоё приложение](/storybook-relationship.jpg)

## Установка Vue Storybook

Нам нужно сделать несколько шагов, чтобы настроить процесс сборки в твоём окружении. Для начала мы хотим использовать [Vue CLI](https://cli.vuejs.org) для настройки нашей системы сборки и включить [Storybook](https://storybook.js.org/) и [Jest](https://facebook.github.io/jest/) тестирование в нашем созданном приложении. Давай запустим следующие команды:

```bash
# Создаёт наше приложение, используя предустановку с jest:
npx -p @vue/cli vue create --preset hichroma/vue-preset-learnstorybook taskbox
cd taskbox

# Добавляет Storybook:
npx -p @storybook/cli sb init
```

Мы можем быстро проверить, что разные окружения нашего приложения работают как надо:

```bash
# Запускает тесты (Jest) в терминале:
yarn test:unit

# Запускает навигатор по компонентам на 6006 порту:
yarn run storybook

# Запускает фронтенд-приложение на 8080 порту:
yarn serve
```

<div class="aside">
  NOTE: Если <code>yarn test:unit</code> выбрасывает ошибку, возможно у тебя не <a href="https://yarnpkg.com/lang/en/docs/install/">установлен yarn</a> или тебе нужно поставить <code>watchman</code>, как указано в <a href="https://github.com/facebook/create-react-app/issues/871#issuecomment-252297884">этом issue</a>.
</div>

Наши три сущности фронтенд-приложения: автоматизированные тесты (Jest), компонентная разработка (Storybook) и само приложение.

![3 сущности](/app-three-modalities-vue.png)

В зависимости от того, над какой частью приложения ты работаешь, тебе может потребоваться запустить одну или несколько этих сущностей одновременно. Поскольку сейчас мы сфокусированы на создании одного UI-компонента, мы продолжим c запущенным Storybook.

## Переиспользование CSS

Taskbox переиспользует элементы дизайна из [примера приложения](https://blog.hichroma.com/graphql-react-tutorial-part-1-6-d0691af25858) для туториала по GraphQL и React, так что нам не нужно будет писать CSS в этом туториале. Мы просто скомпилируем LESS в один CSS файл и подключим его к нашему приложению. Скопируй и вставь этот [скомпилированный CSS](https://github.com/hichroma/learnstorybook-code/blob/master/src/index.css) в `src/index.css` и затем импортируй его в приложение, изменив тег `<style>` в `src/App.vue`, чтобы он выглядел вот так:

```html
<style>
@import './index.css';
</style>
```

![Taskbox UI](/ss-browserchrome-taskbox-learnstorybook.png)

<div class="aside">
Если ты захочешь изменить стили, то ты сможешь найти исходный LESS-файл в GitHub репозитории.
</div>

## Добавление ресурсов

Нам также нужно добавить [шрифты и иконки](https://github.com/hichroma/learnstorybook-code/tree/master/public) в папку `public/`.

Также нам потребуется обновить наш скрипт для сборки storybook, чтобы он собирался в папку `public` (файл `package.json`):

```json
{
  "scripts": {
    "storybook": "start-storybook -p 6006 -s public"
  }
}
```

После добавления стилей и ресурсов приложение может отображаться немного странно. Это нормально, мы ещё не начали работать над приложением. Мы начинаем со строительства нашего первого компонента!

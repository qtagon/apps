<script lang="ts">
  import { ALIGNMENT, SIZE, Typhon } from '@qtagon/typhon-ui';
  import TyphonUI from './core/components/Typhon/index.svelte';

  let dynamic = new Typhon('apps').setColumn('apps').setColumn('actions');

  const apps_container = dynamic
    .onColumn('apps')
    .setRow('apps')
    .setContainer('apps')
    .setClassified('direction-row align-items-flex-start flex-wrap')
    .setStyle('padding: 2rem;');

  const actions_container = dynamic
    .onColumn('actions')
    .setRow('actions')
    .setContainer('actions')
    .setClassified('align-items-flex-start')
    .setStyle('padding: 2rem;');

  // GET AVAILABLE APPS
  const apps = [
    {
      title: 'todo.qtagon.com',
      image: {
        url:
          'https://static.dribbble.com/users/852957/screenshots/9684036/media/da0cd70829c566b17b99fe1f4193eedf.png',
      },
      owner: {
        username: 'hanakao',
      },
    },
    {
      title: 'news.qtagon.com',
      image: {
        url:
          'https://static.dribbble.com/users/1312595/screenshots/14042476/media/7df309763fe4ddbbc9a25a6b2fdc592b.png',
      },
      owner: {
        username: 'fistashka',
      },
    },
    {
      title: 'news.qtagon.com',
      image: {
        url:
          'https://static.dribbble.com/users/1312595/screenshots/14042476/media/7df309763fe4ddbbc9a25a6b2fdc592b.png',
      },
      owner: {
        username: 'fistashka',
      },
    },
    {
      title: 'news.qtagon.com',
      image: {
        url:
          'https://static.dribbble.com/users/1312595/screenshots/14042476/media/7df309763fe4ddbbc9a25a6b2fdc592b.png',
      },
      owner: {
        username: 'fistashka',
      },
    },
    {
      title: 'news.qtagon.com',
      image: {
        url:
          'https://static.dribbble.com/users/1312595/screenshots/14042476/media/7df309763fe4ddbbc9a25a6b2fdc592b.png',
      },
      owner: {
        username: 'fistashka',
      },
    },
    {
      title: 'news.qtagon.com',
      image: {
        url:
          'https://static.dribbble.com/users/1312595/screenshots/14042476/media/7df309763fe4ddbbc9a25a6b2fdc592b.png',
      },
      owner: {
        username: 'fistashka',
      },
    },
  ];

  // ADD APPS
  apps.forEach((app) => {
    const media = apps_container
      .setMedia(app.title, app.owner.username)
      .setClassified('pointer background-white padding-default-half round shadow');
    media
      .setImage(app.image.url, SIZE.SMALL)
      .setClassified('round')
      .setAlignment(ALIGNMENT.MIDDLE);

    dynamic = dynamic;
  });

  actions_container.setButton('').setIcon('plus');
</script>

<style type="text/scss">
</style>

<main>
  <TyphonUI {dynamic} />
</main>

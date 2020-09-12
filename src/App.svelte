<script lang="ts">
  import { ALIGNMENT, SIZE, Typhon } from '@qtagon/typhon-ui';
  import TyphonUI from './core/components/Typhon/index.svelte';

  let dynamic = new Typhon('apps')
    .setColumn('headline')
    .setColumn('apps')
    .setColumn('actions');

  const headline_container = dynamic
    .onColumn('headline')
    .setRow('headline')
    .setContainer('headline')
    .setClassified(
      'direction-row align-items-flex-start flex-wrap height-auto background-white align-center justify-center'
    )
    .setStyle('padding: 2rem;');

  const apps_container = dynamic
    .onColumn('apps')
    .setRow('apps')
    .setContainer('apps')
    .setClassified(
      'direction-row align-items-flex-start background-gray flex-wrap height-auto align-center justify-center'
    )
    .setStyle('padding: 2rem;');

  const actions_container = dynamic
    .onColumn('actions')
    .setRow('actions')
    .setContainer('actions')
    .setClassified(
      'align-items-flex-start direction-row align-center background-white justify-center'
    )
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

  headline_container
    .setMessage(
      'Create. Show. Link. Share.',
      'Share your creations anything , really !'
    )
    .setClassified('h1 content-center');

  actions_container.setButton('Create').setEvent('plus-app').setIcon('plus');

  const modal = dynamic
    .setModal('Link your creation !', "Just complete the form and that's it !")
    .setVisible(false);
  modal
    .setButton("I'm not yet ready")
    .setEvent('cancel')
    .setClassified('transparent bordered')
    .setIcon('close');
  modal.setButton("I'm ready !").setEvent('confirm').setIcon('check');

  /**
   * Functions
   */

  const setupModal = (visible = true) => {
    modal.setVisible(visible);
    dynamic = dynamic;
  };

  /**
   * Event
   */
  const setAppItem = (app) => {
    const media = apps_container
      .setMedia(app.title, app.owner.username)
      .setClassified(
        'pointer background-white padding-default-half round shadow'
      );
    media
      .setImage(app.image.url, SIZE.SMALL)
      .setClassified('round')
      .setAlignment(ALIGNMENT.MIDDLE);
    dynamic = dynamic;
  };

  // ADD APPS
  apps.forEach((app) => {
    setAppItem(app);
  });

  const onEvent = ({ detail }) => {
    if (!detail.name) return;
    switch (detail.name) {
      case 'plus-app':
        setupModal();
        return;
      case 'confirm':
        setAppItem({
          title: 'uber.qtagon.com',
          image: {
            url:
              'https://static.dribbble.com/users/40433/screenshots/14188803/media/dae690daff9335eaa507c50cebfd24fb.png',
          },
          owner: {
            username: 'ueno',
          },
        });
        setupModal(false);
        return;
      default:
        return;
    }
  };
</script>

<TyphonUI {dynamic} on:event={onEvent} />

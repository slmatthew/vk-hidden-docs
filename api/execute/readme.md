# execute
Различные методы, используемые в VK для Android.

* [execute.CommunityAudiosAndPlaylists](#executecommunityaudiosandplaylists)
* [execute.addAudioToPlaylist](#executeaddaudiotoplaylist)
* [execute.cancelDonutSubscription](#executecanceldonutsubscription)
<!-- * [execute.createCommentRestricted](#executecreatecommentrestricted)
* [execute.deleteAvatarNew](#executedeleteavatarnew)
* [execute.deleteStory](#executedeletestory)
* [execute.discoverCategories](#executediscovercategories)
* [execute.editComment](#executeeditcomment)
* [execute.fetchComments](#executefetchcomments)
* [execute.friendsAddWithRecommendations](#executefriendsaddwithrecommendations)
* [execute.getAccountSettings](#executegetaccountsettings)
* [execute.getAudioServicePackages](#executegetaudioservicepackages)
* [execute.getAvailableForGiftStickers](#executegetavailableforgiftstickers)
* [execute.getBirthdaysInfo](#executegetbirthdaysinfo)
* [execute.getClipsPage](#executegetclipspage)
* [execute.getCommentsNew](#executegetcommentsnew)
* [execute.getCommunityChats](#executegetcommunitychats)
* [execute.getCommunityDetails](#executegetcommunitydetails)
* [execute.getCommunityNotificationSettings](#executegetcommunitynotificationsettings)
* [execute.getCopyrightInfo](#executegetcopyrightinfo)
* [execute.getDiscover](#executegetdiscover)
* [execute.getDocTypes](#executegetdoctypes)
* [execute.getFave](#executegetfave)
* [execute.getFaveWithPages](#executegetfavewithpages)
* [execute.getFeedLikes](#executegetfeedlikes)
* [execute.getFriendRequestsMaterial](#executegetfriendrequestsmaterial)
* [execute.getFriendRequestsNotifications](#executegetfriendrequestsnotifications)
* [execute.getFriendsAndLists](#executegetfriendsandlists)
* [execute.getFriendsUsedMoneyTransfers](#executegetfriendsusedmoneytransfers)
* [execute.getFullAddress](#executegetfulladdress)
* [execute.getFullGroupNewNew](#executegetfullgroupnewnew)
* [execute.getFullProfileNewNew](#executegetfullprofilenewnew)
* [execute.getGameLeaderboard](#executegetgameleaderboard)
* [execute.getGamePage](#executegetgamepage)
* [execute.getGamesPage](#executegetgamespage)
* [execute.getGeoNews](#executegetgeonews)
* [execute.getGiftByStickerId](#executegetgiftbystickerid)
* [execute.getGifts](#executegetgifts)
* [execute.getGiftsCatalogMaterial](#executegetgiftscatalogmaterial)
* [execute.getGroupBannedUsers](#executegetgroupbannedusers)
* [execute.getMarketItemFullPage](#executegetmarketitemfullpage)
* [execute.getMarketPage](#executegetmarketpage)
* [execute.getMusicPage](#executegetmusicpage)
* [execute.getMutualFriendsExtended](#executegetmutualfriendsextended)
* [execute.getNewPhotoTagsWithProfiles](#executegetnewphototagswithprofiles)
* [execute.getNewsfeedCustom](#executegetnewsfeedcustom)
* [execute.getNewsfeedSmart](#executegetnewsfeedsmart)
* [execute.getNotifications](#executegetnotifications)
* [execute.getNotificationsIgnoredSources](#executegetnotificationsignoredsources)
* [execute.getNotificationsSettings](#executegetnotificationssettings)
* [execute.getPhotoAlbum](#executegetphotoalbum)
* [execute.getPlaceCheckinsNew](#executegetplacecheckinsnew)
* [execute.getPlaceInfoNew](#executegetplaceinfonew)
* [execute.getPlaylist](#executegetplaylist)
* [execute.getPodcastEpisodesWithInfo](#executegetpodcastepisodeswithinfo)
* [execute.getPodcastList](#executegetpodcastlist)
* [execute.getPodcastListPage](#executegetpodcastlistpage)
* [execute.getPodcastPage](#executegetpodcastpage)
* [execute.getPostPreviewWithInfo](#executegetpostpreviewwithinfo)
* [execute.getPostingSettings](#executegetpostingsettings)
* [execute.getRequestsAndRecommendations](#executegetrequestsandrecommendations)
* [execute.getServiceApp](#executegetserviceapp)
* [execute.getSourcesForClips](#executegetsourcesforclips)
* [execute.getSpecialEventsInfo](#executegetspecialeventsinfo)
* [execute.getStickersCatalogFirstPage](#executegetstickerscatalogfirstpage)
* [execute.getStoriesAndOwners](#executegetstoriesandowners)
* [execute.getTrustedPackage](#executegettrustedpackage)
* [execute.getUserInfo](#executegetuserinfo)
* [execute.getUserPhotosAndNewTags](#executegetuserphotosandnewtags)
* [execute.getUsersAndGroups](#executegetusersandgroups)
* [execute.getVideoAlbums](#executegetvideoalbums)
* [execute.getVideoById](#executegetvideobyid)
* [execute.getVideosWithProfiles](#executegetvideoswithprofiles)
* [execute.getWallSubscriptions](#executegetwallsubscriptions)
* [execute.groupsGet](#executegroupsget)
* [execute.imGetLongPollHistoryExtended](#executeimgetlongpollhistoryextended)
* [execute.imLpInit](#executeimlpinit)
* [execute.isVideoAdded](#executeisvideoadded)
* [execute.joinGroup](#executejoingroup)
* [execute.leaveGroup](#executeleavegroup)
* [execute.marketReplaceCartItem](#executemarketreplacecartitem)
* [execute.moneyGetTransferFull](#executemoneygettransferfull)
* [execute.newsfeedIgnoreItem](#executenewsfeedignoreitem)
* [execute.notificationsDeleteGroupSource](#executenotificationsdeletegroupsource)
* [execute.podcastsJoinGroup](#executepodcastsjoingroup)
* [execute.podcastsLeaveGroup](#executepodcastsleavegroup)
* [execute.pollsAddVote](#executepollsaddvote)
* [execute.pollsDeleteVote](#executepollsdeletevote)
* [execute.pollsEdit](#executepollsedit)
* [execute.pollsGetExtraWithCriteria](#executepollsgetextrawithcriteria)
* [execute.removeAudioFromPlaylist](#executeremoveaudiofromplaylist)
* [execute.resolveScreenName](#executeresolvescreenname)
* [execute.savePlaylist](#executesaveplaylist)
* [execute.searchAll](#executesearchall)
* [execute.searchApps](#executesearchapps)
* [execute.searchGetHintsWithAttachments](#executesearchgethintswithattachments)
* [execute.searchGroups](#executesearchgroups)
* [execute.searchNewsfeedSmart](#executesearchnewsfeedsmart)
* [execute.searchPeople](#executesearchpeople)
* [execute.searchVideosWithProfiles](#executesearchvideoswithprofiles)
* [execute.setPostTopic](#executesetposttopic)
* [execute.setSubscriptionStatus](#executesetsubscriptionstatus)
* [execute.setVideoAlbums](#executesetvideoalbums)
* [execute.storiesAddBan](#executestoriesaddban)
* [execute.storiesAskQuestion](#executestoriesaskquestion)
* [execute.storiesDeleteBan](#executestoriesdeleteban)
* [execute.storiesGetFeedSettings](#executestoriesgetfeedsettings)
* [execute.storiesGetRepliesFull](#executestoriesgetrepliesfull)
* [execute.videoGetTabs](#executevideogettabs)
* [execute.wallArchive](#executewallarchive)
* [execute.wallEdit](#executewalledit)
* [execute.wallGetWrapNew](#executewallgetwrapnew)
* [execute.wallPost](#executewallpost)
* [execute.wallReveal](#executewallreveal) -->



## execute.CommunityAudiosAndPlaylists

Возвращает до 3 треков и до 15 плейлистов в аккаунте пользователя или сообщества.

**Обратите внимание:** метод может вернуть ошибку для любого сообщества, поэтому при использовании нужно обязательно проверять ответ на наличие `execute_errors`.

### Параметры

| Параметр | Тип    | Описание                       |
|----------|--------|--------------------------------|
| gid      | number | id пользователя или сообщества |

### Тип возвращаемого значения

```ts
interface ExecuteCommunityAudiosAndPlaylists {
  audios: VKAudio[]
  playlists: VKPlaylist[]
}
```

### Как работает

Для получения поля `audios` вызывается `audio.get` с параметрами `count: 3` и `owner_id`.

Для получения поля `playlists` вызывается `audio.getPlaylists` с параметрами `count: 15` и `owner_id`.

### Пример ответа
<details>
  <summary>тык</summary>

  ```json
  {
    "audios": [
      {
        "artist": "Markul feat. Платина",
        "id": 456241386,
        "owner_id": 249247563,
        "title": "Конфеты",
        "duration": 161,
        "access_key": "544dab7a483ec5fdf7",
        "ads": {
          "content_id": "249247563_456241386",
          "duration": "161",
          "account_age_type": "3",
          "puid1": "554",
          "puid22": "14"
        },
        "is_explicit": true,
        "is_focus_track": false,
        "is_licensed": true,
        "track_code": "f413c26d1sPTa9MUAln3tfVYEDsZyL1YNtrPOysU",
        "url": "https://cs7-12v4.vkuseraudio.net/p4/b14c9d5b11/c06b0e031664b8/index.m3u8?extra=GFrr7j8laTGi1I8RLTYChzJsiRzMRJYRCUrCzUTZ_AVNOBGnkMOVm8INPLepxS3bY2mvKNkbwHePBQyyT3A2rJjwlh2jHxI-VUzU6znDObOLS_lJyRl67hfmvvgx8VzzYzt_g48hTcGLmcXtkT1srzArfQ&long_chunk=1",
        "date": 1594593737,
        "no_search": 1,
        "album": {
          "id": 7981110,
          "title": "Конфеты",
          "owner_id": -2000981110,
          "access_key": "bde1bfe90c048fb53f",
          "thumb": {
            "width": 300,
            "height": 300,
            "photo_34": "https://sun9-55.userapi.com/c858036/v858036877/21528b/gAG6F87iB9U.jpg",
            "photo_68": "https://sun9-8.userapi.com/c858036/v858036877/215289/z3lV3iwUOAM.jpg",
            "photo_135": "https://sun9-66.userapi.com/c858036/v858036877/215287/Ksotp0sy3L8.jpg",
            "photo_270": "https://sun9-4.userapi.com/c858036/v858036877/215284/KRi0vxPmVZ4.jpg",
            "photo_300": "https://sun9-57.userapi.com/c858036/v858036877/215282/1o6DfbICuUQ.jpg",
            "photo_600": "https://sun9-48.userapi.com/c858036/v858036877/215281/pAnBuLUn0KU.jpg",
            "photo_1200": "https://sun9-23.userapi.com/c858036/v858036877/215280/ESX9LAQQbv8.jpg"
          }
        },
        "main_artists": [
          {
            "name": "Markul",
            "domain": "8473949182781681811",
            "id": "8473949182781681811"
          }
        ],
        "featured_artists": [
          {
            "name": "Платина",
            "domain": "7935075146089096976",
            "id": "7935075146089096976"
          }
        ],
        "short_videos_allowed": false,
        "stories_allowed": false
      }
    ],
    "playlists": [
      {
        "id": 47,
        "owner_id": 249247563,
        "type": 0,
        "title": "Happy(для тусовок)",
        "description": "Есть musiceverysf телеграмм, где я каждые день выкладываю новые треки. Если интересно- залетай.",
        "count": 131,
        "followers": 26159,
        "plays": 368600,
        "create_time": 1588022194,
        "update_time": 1594641785,
        "genres": [],
        "is_following": false,
        "original": {
          "playlist_id": 45,
          "owner_id": 166352597,
          "access_key": "3da97cfef1ddf7384d"
        },
        "photo": {
          "width": 300,
          "height": 300,
          "photo_34": "https://sun9-52.userapi.com/c857224/v857224961/1bca59/DssgMcBJMc0.jpg",
          "photo_68": "https://sun9-27.userapi.com/c857224/v857224961/1bca57/bFHSwYnSis0.jpg",
          "photo_135": "https://sun9-33.userapi.com/c857224/v857224961/1bca55/pvi85HGkcwM.jpg",
          "photo_270": "https://sun9-22.userapi.com/c857224/v857224961/1bca52/rn72ju2nOy4.jpg",
          "photo_300": "https://sun9-56.userapi.com/c857224/v857224961/1bca50/KiP1dsp76rA.jpg",
          "photo_600": "https://sun9-56.userapi.com/c857224/v857224961/1bca4f/f-osqxKmOKo.jpg",
          "photo_1200": "https://sun9-40.userapi.com/c857224/v857224961/1bca4e/L4SoxnNBoDs.jpg"
        },
        "permissions": {
          "play": true,
          "share": true,
          "edit": false,
          "follow": true
        },
        "subtitle_badge": false,
        "play_button": false,
        "access_key": "ce6f341d1d273ae160",
        "album_type": "playlist"
      }
    ]
  }
  ```
</details>



## execute.addAudioToPlaylist

Добавляет аудиозаписи в плейлист и возвращает обновленный альбом.

### Параметры

| Параметр    | Тип    | Описание                                            |
|-------------|--------|-----------------------------------------------------|
| owner_id    | number | id пользователя или сообщества                      |
| playlist_id | number | id плейлиста                                        |
| audio_ids   | string | id аудиозаписей в формате ownerId_audioId_accessKey |

### Тип возвращаемого значения

```ts
interface ExecuteAddAudioToPlaylist {
  result: { audio_id: number }[]
  playlist: VKPlaylist
}
```

### Как работает

Для получения поля `result` вызывается метод `audio.addToPlaylist`, в который передаются те же параметры,
что и в этот метод.

Для получения поля `playlist` вызывается метод `audio.getPlaylistById` с параметрами `owner_id` и `playlist_id`.

### Пример ответа

<details>
  <summary>тык</summary>

  ```json
  {
    "result": [{ "audio_id": 456239732 }],
    "playlist": {
      "id": 5,
      "owner_id": 88262293,
      "type": 0,
      "title": "фываыва",
      "description": "",
      "count": 17,
      "followers": 0,
      "plays": 0,
      "create_time": 1551094084,
      "update_time": 1594746956,
      "genres": [],
      "is_following": false,
      "permissions": {
        "play": true,
        "share": true,
        "edit": true,
        "follow": true
      },
      "subtitle_badge": false,
      "play_button": false,
      "thumbs": [
        {
          "width": 300,
          "height": 300,
          "photo_34": "https://sun9-55.userapi.com/c858036/v858036877/21528b/gAG6F87iB9U.jpg",
          "photo_68": "https://sun9-8.userapi.com/c858036/v858036877/215289/z3lV3iwUOAM.jpg",
          "photo_135": "https://sun9-66.userapi.com/c858036/v858036877/215287/Ksotp0sy3L8.jpg",
          "photo_270": "https://sun9-4.userapi.com/c858036/v858036877/215284/KRi0vxPmVZ4.jpg",
          "photo_300": "https://sun9-57.userapi.com/c858036/v858036877/215282/1o6DfbICuUQ.jpg",
          "photo_600": "https://sun9-48.userapi.com/c858036/v858036877/215281/pAnBuLUn0KU.jpg",
          "photo_1200": "https://sun9-23.userapi.com/c858036/v858036877/215280/ESX9LAQQbv8.jpg"
        },
        {
          "width": 300,
          "height": 300,
          "photo_34": "https://sun9-55.userapi.com/c846217/v846217368/1c155b/TwDPBBlui4Y.jpg",
          "photo_68": "https://sun9-57.userapi.com/c846217/v846217368/1c1559/_vM0aBzNKvE.jpg",
          "photo_135": "https://sun9-50.userapi.com/c846217/v846217368/1c1557/ACYLOgJu90o.jpg",
          "photo_270": "https://sun9-46.userapi.com/c846217/v846217368/1c1554/SGvkSBuOTwk.jpg",
          "photo_300": "https://sun9-72.userapi.com/c846217/v846217368/1c1552/Rvbbz6sKMdw.jpg",
          "photo_600": "https://sun9-1.userapi.com/c846217/v846217368/1c1551/BzOIUxmIzXQ.jpg",
          "photo_1200": "https://sun9-10.userapi.com/c846217/v846217368/1c1550/amcpWlIUkro.jpg"
        },
        {
          "width": 300,
          "height": 300,
          "photo_34": "https://sun9-11.userapi.com/c815322/v815322005/1a/iGZcAWxO40Y.jpg",
          "photo_68": "https://sun9-21.userapi.com/c815322/v815322005/18/4DXtFlSvem8.jpg",
          "photo_135": "https://sun9-58.userapi.com/c815322/v815322005/16/6U22nflg9hk.jpg",
          "photo_270": "https://sun9-59.userapi.com/c815322/v815322005/13/RWTo6TaQ5wY.jpg",
          "photo_300": "https://sun9-32.userapi.com/c815322/v815322005/11/4vo8bxKqALw.jpg",
          "photo_600": "https://sun9-11.userapi.com/c815322/v815322005/10/1gqcpSPzpNY.jpg",
          "photo_1200": "https://sun9-20.userapi.com/c815322/v815322005/f/w7_7ulvJQQg.jpg"
        },
        {
          "width": 300,
          "height": 300,
          "photo_34": "https://sun9-4.userapi.com/c855336/v855336230/43014/9H2xNoeRqQk.jpg",
          "photo_68": "https://sun9-4.userapi.com/c855336/v855336230/43012/7m77lID303k.jpg",
          "photo_135": "https://sun9-1.userapi.com/c855336/v855336230/43010/BjIkGdtjhPc.jpg",
          "photo_270": "https://sun9-10.userapi.com/c855336/v855336230/4300d/otKUV-LrSM8.jpg",
          "photo_300": "https://sun9-65.userapi.com/c855336/v855336230/4300b/Mm6NAWO7m1Y.jpg",
          "photo_600": "https://sun9-69.userapi.com/c855336/v855336230/4300a/Mql2JSH_kSw.jpg",
          "photo_1200": "https://sun9-33.userapi.com/c855336/v855336230/43009/8Qvk2gQI4So.jpg"
        }
      ],
      "access_key": "***",
      "album_type": "playlist"
    }
  }
  ```
</details>



## execute.cancelDonutSubscription

Отменяет подписку на сообщество (с возможностью отменить отписку).

### Параметры

| Параметр | Тип    | Описание                       |
|----------|--------|--------------------------------|
| owner_id | number | id пользователя или сообщества |

### Тип возвращаемого значения

```ts
interface ExecuteCancelDonutSubscription {
  cancelled: true
  group?: VKGroup
}
```

В поле `group` находится дополнительное поле `donut`, которое можно самостоятельно получить, если вызвать
метод `groups.getById` с `fields: 'donut'`. Его тип:

```ts
interface VKGroupDonut {
  is_don: boolean
  // возвращается, если ты дон
  payment_link?: {
    target: 'internal'
    type: 'open_url'
    // ссылка на продление подписки (которая не имеет смысла)
    url: string
  }
  // возвращается, если ты дон
  status?: 'expiring'
  wall: {
    available: boolean
    is_enabled: boolean
    // возвращается, если ты _не_ дон
    widget?: VKWidget
  }
}
```

### Пример ответа

В примере ответа автор не является доном.

<details>
  <summary>тык</summary>

  ```json
  {
    "canceled": true,
    "group": {
      "id": 163369292,
      "name": "Flyink outdoor",
      "screen_name": "mem.flyink",
      "is_closed": 0,
      "type": "page",
      "is_admin": 0,
      "is_member": 1,
      "is_advertiser": 0,
      "donut": {
        "is_don": false,
        "wall": {
          "is_enabled": true,
          "available": false,
          "widget": {
            "text": "Здесь Вы сможете просматривать эксклюзивные материалы Вашего любимого автора, если оформите платную подписку на его творчество с помощью VK Donut.",
            "title": "VK Donut",
            "button": {
              "action": {
                "target": "internal",
                "type": "open_url",
                "url": "https://vk.com/@donut-faq-dlya-donov"
              },
              "title": "Подробнее"
            },
            "image": [
              {
                "height": 64,
                "url": "https://vk.com/images/donate/vk_donate_64.png",
                "width": 64
              },
              {
                "height": 96,
                "url": "https://vk.com/images/donate/vk_donate_64_1,5x.png",
                "width": 96
              },
              {
                "height": 128,
                "url": "https://vk.com/images/donate/vk_donate_64_2x.png",
                "width": 128
              },
              {
                "height": 192,
                "url": "https://vk.com/images/donate/vk_donate_64_3x.png",
                "width": 192
              },
              {
                "height": 256,
                "url": "https://vk.com/images/donate/vk_donate_64_4x.png",
                "width": 256
              }
            ]
          }
        },
        "description": {
          "about_button": {
            "action": {
              "target": "internal",
              "type": "open_url",
              "url": "https://vk.com/@donut-faq-dlya-donov"
            },
            "title": "Что такое VK Donut?"
          },
          "text": "цп",
          "title": "Поддержать автора",
          "button": {
            "action": {
              "target": "internal",
              "type": "open_url",
              "url": "https://vk.com/mem.flyink?w=donut_payment-163369292&source=description"
            },
            "title": "Поддержать автора"
          },
          "friends": [
            {
              "first_name": "Р­Р»СЊС‡РёРЅ",
              "id": 172894294,
              "last_name": "РћСЂСѓРґР¶РµРІ",
              "can_access_closed": true,
              "is_closed": false,
              "sex": 2,
              "photo_50": "https://sun7-6.userapi.com/impg/jTvmWwYpVfkXnv9Vki5kEzHw0z_OtWo3Vd0OYw/3No0ZlpCLVk.jpg?size=50x0&quality=90&crop=210,153,469,469&sign=13da3e69604a141eb5cb73599ecfb508&c_uniq_tag=KuRB0mOW8B-aq8sqzKIgNUsq4RVbJUpSRQeBuTrNTy4&ava=1",
              "photo_100": "https://sun7-6.userapi.com/impg/jTvmWwYpVfkXnv9Vki5kEzHw0z_OtWo3Vd0OYw/3No0ZlpCLVk.jpg?size=100x0&quality=90&crop=210,153,469,469&sign=81e4e0607a248d132c01273d6396c0e4&c_uniq_tag=cpE0YN8H0njXKvGSpWbo_Zd7WUtAFsjxnfU_ox8YwxE&ava=1",
              "photo_200": "https://sun7-6.userapi.com/impg/jTvmWwYpVfkXnv9Vki5kEzHw0z_OtWo3Vd0OYw/3No0ZlpCLVk.jpg?size=200x0&quality=90&crop=210,153,469,469&sign=94e0cff55b667647605abe38243d1130&c_uniq_tag=tR469ut-uYJcuny8ckkf_fCznHO_TX6CicsuiHt-rmw&ava=1",
              "friend_status": 3
            },
            {
              "first_name": "РњР°РєСЃРµРј",
              "id": 236820864,
              "last_name": "РњР°РЅР°РµРЅРєРѕРІ",
              "can_access_closed": true,
              "is_closed": false,
              "sex": 2,
              "photo_50": "https://sun9-30.userapi.com/impg/c857024/v857024963/15aeb4/y1ZsWz3rDSo.jpg?size=50x0&quality=90&crop=575,641,608,608&sign=1fef7d20445939e2b88022dffbf7b578&c_uniq_tag=Ouli111gqzYboYicUDpZq9y6JynMxw7juC1Jr5kIK_c&ava=1",
              "photo_100": "https://sun9-30.userapi.com/impg/c857024/v857024963/15aeb4/y1ZsWz3rDSo.jpg?size=100x0&quality=90&crop=575,641,608,608&sign=15b313537bbccf0a110bf3b96ee84edd&c_uniq_tag=yLdXjjmnCwXaKoW7zer_c69GDs_YPSdh-HRsYl1Z5Us&ava=1",
              "photo_200": "https://sun9-30.userapi.com/impg/c857024/v857024963/15aeb4/y1ZsWz3rDSo.jpg?size=200x0&quality=90&crop=575,641,608,608&sign=7ed6bcc634361408c36455f9fa3f574f&c_uniq_tag=YOJTVLus46ySB3gyY26dit0SQ2jyDD_k2ZuQZle23jE&ava=1",
              "friend_status": 3
            },
            {
              "first_name": "РљРёСЂРёР»Р»",
              "id": 343294797,
              "last_name": "Р“Р»СѓС€Р°РєРѕРІ",
              "can_access_closed": true,
              "is_closed": true,
              "sex": 2,
              "photo_50": "https://sun9-11.userapi.com/impg/c856524/v856524902/192e1a/s8Sip6jVv1w.jpg?size=50x0&quality=90&crop=63,206,822,822&sign=d0ceb81b91eb33c5cb906bb9f1b85414&c_uniq_tag=e2b6fBZhkPHls7NpjLJo8Gp9J6agvqcbEth_odlQt_s&ava=1",
              "photo_100": "https://sun9-11.userapi.com/impg/c856524/v856524902/192e1a/s8Sip6jVv1w.jpg?size=100x0&quality=90&crop=63,206,822,822&sign=c6ffcd9e4a18c7f86fde3dec11422b34&c_uniq_tag=idewtlZe9FY3Uer5cuNG9w9epOQ-PTYAo-ED7GOQjvs&ava=1",
              "photo_200": "https://sun9-11.userapi.com/impg/c856524/v856524902/192e1a/s8Sip6jVv1w.jpg?size=200x0&quality=90&crop=63,206,822,822&sign=91a7334469a3a71f61672f1136fdbf9a&c_uniq_tag=cBn8OoWbx4mVH-7SZ-RNpI5PkVKdrZmVsz7E680OtKs&ava=1",
              "friend_status": 3
            }
          ],
          "image": [
            {
              "height": 44,
              "url": "https://vk.com/images/donate/vk_donate_44.png",
              "width": 44
            },
            {
              "height": 66,
              "url": "https://vk.com/images/donate/vk_donate_44_1,5x.png",
              "width": 66
            },
            {
              "height": 88,
              "url": "https://vk.com/images/donate/vk_donate_44_2x.png",
              "width": 88
            },
            {
              "height": 132,
              "url": "https://vk.com/images/donate/vk_donate_44_3x.png",
              "width": 132
            },
            {
              "height": 176,
              "url": "https://vk.com/images/donate/vk_donate_44_4x.png",
              "width": 176
            }
          ],
          "statistics": [
            {
              "description": "4 дона · 3 друга",
              "icon": "subscribers",
              "show_friends": true
            },
            {
              "description": "7 эксклюзивных записей",
              "icon": "wall"
            }
          ],
          "price": 50
        }
      },
      "photo_50": "https://sun9-50.userapi.com/c855036/v855036378/240b6b/qvGHxCbM6DA.jpg?ava=1",
      "photo_100": "https://sun9-25.userapi.com/c855036/v855036378/240b6a/bW_CQRrO_YU.jpg?ava=1",
      "photo_200": "https://sun9-46.userapi.com/c855036/v855036378/240b69/Wb9UIrkr2rw.jpg?ava=1"
    }
  }
  ```
</details>

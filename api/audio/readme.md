# audio
Методы для работы с аудиозаписями

## Список методов
* [audio.add](#audio.add)
* [audio.addAlbum](#audio.addalbum)
* [audio.addToFavorites](#audio.addtofavorites)
* [audio.addToPlaylist](#audio.addtoplaylist)
* [audio.delete](#audio.delete)
* [audio.deleteAlbum](#audio.deletealbum)
* [audio.deletePlaylist](#audio.deleteplaylist)
* [audio.edit](#audio.edit)
* [audio.editAlbum](#audio.editalbum)
* [audio.editPlaylist](#audio.editplaylist)
* [audio.followArtist](#audio.followartist)
* [audio.followPlaylist](#audio.followplaylist)
* [audio.get](#audio.get)
* [audio.getAlbums](#audio.getalbums)
* [audio.getAlbumsByArtist](#audio.getalbumsbyartist)
* [audio.getArtists](#audio.getartists)
* [audio.getAudiosByArtist](#audio.getaudiosbyartist)
* [audio.getBroadcast](#audio.getbroadcast)
* [audio.getById](#audio.getbyid)
* [audio.getCatalog](#audio.getcatalog)
* [audio.getCatalogBlockById](#audio.getcatalogblockbyid)
* [audio.getCatalogSearch](#audio.getcatalogsearch)
* [audio.getCatalogSection](#audio.getcatalogsection)
* [audio.getCount](#audio.getcount)
* [audio.getFavorites](#audio.getfavorites)
* [audio.getForDownload](#audio.getfordownload)
* [audio.getHints](#audio.gethints)
* [audio.getLyrics](#audio.getlyrics)
* [audio.getOnboardingOffer](#audio.getonboardingoffer)
* [audio.getPlaylistForDownload](#audio.getplaylistfordownload)
* [audio.getPlaylists](#audio.getplaylists)
* [audio.getPopular](#audio.getpopular)
* [audio.getRecentAudios](#audio.getrecentaudios)
* [audio.getRecommendations](#audio.getrecommendations)
* [audio.getRestrictionPopup](#audio.getrestrictionpopup)
* [audio.getSearchTrends](#audio.getsearchtrends)
* [audio.getStoryCatalog](#audio.getstorycatalog)
* [audio.getStoryCatalogBlock](#audio.getstorycatalogblock)
* [audio.getStorySearchCatalog](#audio.getstorysearchcatalog)
* [audio.getUploadServer](#audio.getuploadserver)
* [audio.moveToAlbum](#audio.movetoalbum)
* [audio.reorder](#audio.reorder)
* [audio.reorderPlaylists](#audio.reorderplaylists)
* [audio.restore](#audio.restore)
* [audio.save](#audio.save)
* [audio.search](#audio.search)
* [audio.searchAlbums](#audio.searchalbums)
* [audio.searchArtists](#audio.searchartists)
* [audio.searchMain](#audio.searchmain)
* [audio.searchPlaylists](#audio.searchplaylists)
* [audio.sendStartEvent](#audio.sendstartevent)
* [audio.setBroadcast](#audio.setbroadcast)
* [audio.setForDownload](#audio.setfordownload)
* [audio.setPlaylistForDownload](#audio.setplaylistfordownload)
* [audio.subscribeToQueue](#audio.subscribetoqueue)
* [audio.unfollowArtist](#audio.unfollowartist)

## audio.add
Добавить аудиозапись к себе

### Параметры

| Параметр   | Тип    | Описание                |
|------------|--------|-------------------------|
| owner_id   | int    | ID владельца            |
| audio_id   | int    | ID аудио                |
| access_key | string | Ключ доступа            |
| track_code | string | Трек-код для статистики |
| ref        | string | Неизвестно              |

### Пример ответа
```json
{
  "response": 456200000
}
```
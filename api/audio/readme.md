# audio
Методы для работы с аудиозаписями

## Список методов
* [audio.add](#audioadd)
* [audio.addAlbum](#audioaddalbum)
* [audio.addToFavorites](#audioaddtofavorites)
* [audio.addToPlaylist](#audioaddtoplaylist)
* [audio.delete](#audiodelete)
* [audio.deleteAlbum](#audiodeletealbum)
* [audio.deletePlaylist](#audiodeleteplaylist)
* [audio.edit](#audioedit)
* [audio.editAlbum](#audioeditalbum)
* [audio.editPlaylist](#audioeditplaylist)
* [audio.followArtist](#audiofollowartist)
* [audio.followPlaylist](#audiofollowplaylist)
* [audio.get](#audioget)
* [audio.getAlbums](#audiogetalbums)
* [audio.getAlbumsByArtist](#audiogetalbumsbyartist)
* [audio.getArtists](#audiogetartists)
* [audio.getAudiosByArtist](#audiogetaudiosbyartist)
* [audio.getBroadcast](#audiogetbroadcast)
* [audio.getById](#audiogetbyid)
* [audio.getCatalog](#audiogetcatalog)
* [audio.getCatalogBlockById](#audiogetcatalogblockbyid)
* [audio.getCatalogSearch](#audiogetcatalogsearch)
* [audio.getCatalogSection](#audiogetcatalogsection)
* [audio.getCount](#audiogetcount)
* [audio.getFavorites](#audiogetfavorites)
* [audio.getForDownload](#audiogetfordownload)
* [audio.getHints](#audiogethints)
* [audio.getLyrics](#audiogetlyrics)
* [audio.getOnboardingOffer](#audiogetonboardingoffer)
* [audio.getPlaylistForDownload](#audiogetplaylistfordownload)
* [audio.getPlaylists](#audiogetplaylists)
* [audio.getPopular](#audiogetpopular)
* [audio.getRecentAudios](#audiogetrecentaudios)
* [audio.getRecommendations](#audiogetrecommendations)
* [audio.getRestrictionPopup](#audiogetrestrictionpopup)
* [audio.getSearchTrends](#audiogetsearchtrends)
* [audio.getStoryCatalog](#audiogetstorycatalog)
* [audio.getStoryCatalogBlock](#audiogetstorycatalogblock)
* [audio.getStorySearchCatalog](#audiogetstorysearchcatalog)
* [audio.getUploadServer](#audiogetuploadserver)
* [audio.moveToAlbum](#audiomovetoalbum)
* [audio.reorder](#audioreorder)
* [audio.reorderPlaylists](#audioreorderplaylists)
* [audio.restore](#audiorestore)
* [audio.save](#audiosave)
* [audio.search](#audiosearch)
* [audio.searchAlbums](#audiosearchalbums)
* [audio.searchArtists](#audiosearchartists)
* [audio.searchMain](#audiosearchmain)
* [audio.searchPlaylists](#audiosearchplaylists)
* [audio.sendStartEvent](#audiosendstartevent)
* [audio.setBroadcast](#audiosetbroadcast)
* [audio.setForDownload](#audiosetfordownload)
* [audio.setPlaylistForDownload](#audiosetplaylistfordownload)
* [audio.subscribeToQueue](#audiosubscribetoqueue)
* [audio.unfollowArtist](#audiounfollowartist)

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
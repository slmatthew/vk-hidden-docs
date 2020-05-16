# Методы секции bugtracker
Методы для работы с баг-трекером.

## Список методов
* [bugtracker.addUserDevice](addUserDevice.md)
* [bugtracker.bookmark](bookmark.md)
* [bugtracker.changeBugreportStatus](changeBugreportStatus.md)
* [bugtracker.createComment](createComment.md)
* [bugtracker.deleteComment](deleteComment.md)
* [bugtracker.deleteUserDevice](deleteUserDevice.md)
* [bugtracker.editBugreport](editBugreport.md)
* [bugtracker.editComment](editComment.md)
* [bugtracker.getBookmarks](getBookmarks.md)
* [bugtracker.getBugreportById](getBugreportById.md)
* [bugtracker.getBugreportSectionList](getBugreportSectionList.md)
* [bugtracker.getBugreportStatusBox](getBugreportStatusBox.md)
* [bugtracker.getComments](getComments.md)
* [bugtracker.getDownloadVersionUrl](getDownloadVersionUrl.md)
* [bugtracker.getEditDeviceFormData](getEditDeviceFormData.md)
* [bugtracker.getInfo](getInfo.md)
* [bugtracker.getProductBranches](getProductBranches.md)
* [bugtracker.getProductVersions](getProductVersions.md)
* [bugtracker.getProducts](getProducts.md)
* [bugtracker.getProductsById](getProductsById.md)
* [bugtracker.getReporterProducts](getReporterProducts.md)
* [bugtracker.getReportersById](getReportersById.md)
* [bugtracker.getReportersTop](getReportersTop.md)
* [bugtracker.getSearchParameters](getSearchParameters.md)
* [bugtracker.getSettings](getSettings.md)
* [bugtracker.joinProduct](joinProduct.md)
* [bugtracker.leaveProduct](leaveProduct.md)
* [bugtracker.removeBugreport](removeBugreport.md)
* [bugtracker.reproduce](reproduce.md)
* [bugtracker.restoreComment](restoreComment.md)
* [bugtracker.saveBugreport](saveBugreport.md)
* [bugtracker.saveDevice](saveDevice.md)
* [bugtracker.saveUserDevice](saveUserDevice.md)
* [bugtracker.searchBugreports](searchBugreports.md)
* [bugtracker.searchDevices](searchDevices.md)
* [bugtracker.setProductVersionNotify](setProductVersionNotify.md)
* [bugtracker.updateBugreportVersion](updateBugreportVersion.md)

## Доступ
Для доступа к этим методам нужен токен от приложения `6831669` (Мобильный баг-трекер).

### Лёгкий способ
Открыть ссылку `https://oauth.vk.com/authorize?client_id=6831669&scope=65536&redirect_uri=https://oauth.vk.com/blank.html&display=page&response_type=token&revoke=1` и скопировать токен.

### Сложный способ
1. Авторизоваться на `m.vk.com` и сохранить куки
2. Сделать запрос на `https://m.vk.com/vkui_internal?app_id=6831669&act=login` со следующими заголовками:
	* User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:77.0) Gecko/20100101 Firefox/77.0 *или от любого другого браузера*
	* Accept: \*/\*
	* Accept-Language: ru,en-US;q=0.7,en;q=0.3
	* vkui: 1
	* Cache-Control: max-age=0
3. Получить токен из запроса

## Загрзука фотографий
Загрузка фотографий производится с тем же токеном, но нужен доступ к `photos`.

1. Вызвать метод `photos.getUploadServer`
2. Загрузить фотографию в поле `file` на `upload_url`
3. `photos.save`

## Ещё кое-что
Все хеши заменены на пустую строку, большинство значений были изменены.
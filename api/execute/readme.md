# execute
Различные методы, используемые в VK для Android.

* execute.CommunityAudiosAndPlaylists
* execute.CommunityPhotosCounter
* execute.addAudioToPlaylist
* execute.cancelDonutSubscription
* execute.createCommentRestricted
* execute.deleteAvatarNew
* execute.deleteStory
* execute.discoverCategories
* execute.editComment
* execute.fetchComments
* execute.friendsAddWithRecommendations
* execute.getAccountSettings
* execute.getAudioServicePackages
* execute.getAvailableForGiftStickers
* execute.getBirthdaysInfo
* execute.getClipsPage
* execute.getCommentsNew
* execute.getCommunityChats
* execute.getCommunityDetails
* execute.getCommunityNotificationSettings
* execute.getCopyrightInfo
* execute.getDiscover
* execute.getDocTypes
* execute.getFave
* execute.getFaveWithPages
* execute.getFeedLikes
* execute.getFriendRequestsMaterial
* execute.getFriendRequestsNotifications
* execute.getFriendsAndLists
* execute.getFriendsUsedMoneyTransfers
* execute.getFullAddress
* execute.getFullGroupNewNew
* execute.getFullProfileNewNew
* execute.getGameLeaderboard
* execute.getGamePage
* execute.getGamesPage
* execute.getGeoNews
* execute.getGiftByStickerId
* execute.getGifts
* execute.getGiftsCatalogMaterial
* execute.getGroupBannedUsers
* execute.getMarketItemFullPage
* execute.getMarketPage
* execute.getMusicPage
* execute.getMutualFriendsExtended
* execute.getNewPhotoTagsWithProfiles
* execute.getNewsfeedCustom
* execute.getNewsfeedSmart
* execute.getNotifications
* execute.getNotificationsIgnoredSources
* execute.getNotificationsSettings
* execute.getPhotoAlbum
* execute.getPlaceCheckinsNew
* execute.getPlaceInfoNew
* execute.getPlaylist
* execute.getPodcastEpisodesWithInfo
* execute.getPodcastList
* execute.getPodcastListPage
* execute.getPodcastPage
* execute.getPostPreviewWithInfo
* execute.getPostingSettings
* execute.getRequestsAndRecommendations
* execute.getServiceApp
* execute.getSourcesForClips
* execute.getSpecialEventsInfo
* execute.getStickersCatalogFirstPage
* execute.getStoriesAndOwners
* execute.getTrustedPackage
* execute.getUserInfo
* execute.getUserPhotosAndNewTags
* execute.getUsersAndGroups
* execute.getVideoAlbums
* execute.getVideoById
* execute.getVideosWithProfiles
* execute.getWallSubscriptions
* execute.groupsGet
* execute.imGetLongPollHistoryExtended
* execute.imLpInit
* execute.isVideoAdded
* execute.joinGroup
* execute.leaveGroup
* execute.marketReplaceCartItem
* execute.moneyGetTransferFull
* execute.newsfeedIgnoreItem
* execute.notificationsDeleteGroupSource
* execute.podcastsJoinGroup
* execute.podcastsLeaveGroup
* execute.pollsAddVote
* execute.pollsDeleteVote
* execute.pollsEdit
* execute.pollsGetExtraWithCriteria
* execute.removeAudioFromPlaylist
* execute.resolveScreenName
* execute.savePlaylist
* execute.searchAll
* execute.searchApps
* execute.searchGetHintsWithAttachments
* execute.searchGroups
* execute.searchNewsfeedSmart
* execute.searchPeople
* execute.searchVideosWithProfiles
* execute.setPostTopic
* execute.setSubscriptionStatus
* execute.setVideoAlbums
* execute.storiesAddBan
* execute.storiesAskQuestion
* execute.storiesDeleteBan
* execute.storiesGetFeedSettings
* execute.storiesGetRepliesFull
* execute.videoGetTabs
* execute.wallArchive
* execute.wallEdit
* execute.wallGetWrapNew
* execute.wallPost
* execute.wallReveal

## execute.getGameLeaderboard
app_id (int), fields (string)

## execute.getGamePage
platform ('android'), type ('points'), app_id (int), fields (string), func_v (int)

## execute.getGamesPage
platform ('android'), fields (string), func_v (int | 12)

## execute.getServiceApp
app_id (int), url (https://vk.com/app<app_id>#<hash (optional)>), ref (string), func_v (int | 3)

## execute.notificationsDeleteGroupSource
group_id (int)

## execute.getAccountSettings
func_v (int | 2)

## execute.getCommunityDetails
group_id (int), need_events (bool), need_chats (bool)

## execute.getCommunityNotificationSettings
group_id (int), force_settings (1)

## execute.CommunityPhotosCounter
gid (int), main_album_id (int), skip_hidden (1), count (int), loadAlbum (1)

## execute.groupsGet
user_id (int), extended (1), fields (string)

## execute.resolveScreenName
screen_name (string), url (string), owner_id (int), func_v (int | 17), ref (string), ref_section_id (string)

## execute.setSubscriptionStatus
id (int), subscribe (1 | 0), func_v (int | 3)

## execute.getFave
func_v 1, count int, extended 1, photo_sizes 1, offset int, fields string, ref string, is_from_snackbar bool, item_type string, tag_id int, filter string

## execute.getFaveWithPages
func_v 1, count int, extended 1, photo_sizes 1, offset int, fields string, ref string, is_from_snackbar bool, tag_id int, type 'hints'

## execute.friendsAddWithRecommendations
user_id int, text string, follow 0, add_only bool, source string, track_code string

## execute.getFriendsAndLists
fields string, order 'hints', need_lists 1, user_id int, func_v int 3, need_requests 1, need_suggest 1

## execute.getMutualFriendsExtended
fields string, target_uid int

## execute.getFriendRequestsMaterial
offset int, func_v int 3, count int, fields string, suggested 1, out 1

## execute.getRequestsAndRecommendations
count int, func_v int 3, ref string

## execute.getFriendRequestsNotifications
count int, offset int, sort 0, need_mutual 1, need_messages 1, fields string, ref string

## execute.joinGroup
group_id int, not_sure 1, video_id int, owner_id int, need_suggestions bool, source string, track_code string

## execute.getFullAddress
group_id int, extended 1, count int, func_v 3, need_taxi 1|0, address_ids int, latitude int, longitude int

## execute.getGroupBannedUsers
fields string, group_id int, owner_id int, func_v 2

## execute.getCommunityChats
group_id int, offset int, count int

## execute.leaveGroup
group_id int, func_v 2, cancel_donut_subscription bool, source string, track_code string

## execute.getMarketPage
owner_id int, count int, offset int, extended 1, photo_sizes 1, query string, load_market 1, albums_count int, albums_offset int, func_v 2, sort_type 0 - byDefault 2 - byAddDate 3 - byPriceAsk 4 - byPriceDesc, album_id int, price_from long, price_to long

## execute.getMarketItemFullPage
owner_id int, id int, offset int, count int, need_likes 1, forceLoadGood 1, func_v 7, access_key string

## execute.marketReplaceCartItem
item_ids `(-int)_(int)`, old_item_id int, new_item_id int, quantity int, group_id int, extended 1

## execute.getCopyrightInfo
owner_id int, source_id int, source_type string (unknown, owner, vk_app, app, artist, external_link)

## execute.searchGetHintsWithAttachments
q string, limit int, fields string

## execute.deleteAvatarNew
owner_id int

## execute.getNewPhotoTagsWithProfiles
offset int, count int, photo_sizes 1

## execute.getUserPhotosAndNewTags
offset i, count i2, extended 1, sort 'desk', photo_sizes 1

## execute.getPlaceCheckinsNew
place_id int, offset int, count int, func_v 3, fields

## execute.getPlaceInfoNew
place_id int, func_v 3

## execute.searchAll
q string, limit int, offset int, func_v 2

я устал

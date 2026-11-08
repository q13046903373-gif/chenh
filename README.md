# chenh
#!name=Spotify Enhanced
#!desc=Spotify页面兼容优化版 | Loon
#!openUrl=https://github.com/app2smile/rules

[Rewrite]
# 清除自定义配置接口的缓存标记
^https:\/\/(spclient\.wg\.spotify\.com|.*-spclient\.spotify\.com(:443)?)\/user-customization-service\/v1\/customize$ header-del if-none-match

[Script]
# 歌手及专辑页面兼容
http-request ^https:\/\/(spclient\.wg\.spotify\.com|.*-spclient\.spotify\.com(:443)?)\/(artistview\/v1\/artist|album-entity-view\/v2\/album)\/ script-path=https://raw.githubusercontent.com/app2smile/rules/master/js/spotify-json.js, timeout=10, tag=Spotify_JSON

[Mitm]
hostname = %APPEND% spclient.wg.spotify.com, *.spclient.spotify.com

[Rule]

//ZhiHu

URL-REGEX,https://api.zhihu.com/(ab|fringe|zst|commercial|ad-style-service|topstory/hot-lists|market/popover|search/(top|tab|preset)|.*(recommendations|featured-comment-ad)),REJECT
AND,((USER-AGENT,osee2*), (NOT,((DOMAIN,api.zhihu.com))), (NOT,((DOMAIN,link.zhihu.com))), (NOT,((DOMAIN,lens.zhihu.com))), (NOT,((DOMAIN,www.zhihu.com))), (NOT,((DOMAIN-SUFFIX,zhimg.com)))),REJECT

//BiliBili

URL-REGEX,https://app.bilibili.com/(pgc/season/rank/cn|x/v2/(rank.*rid=(168|5)|search/(defaultword|hot|recommend|resource))),REJECT


[MITM]

hostname = api.amemv.com, api*.musical.ly, api*.tiktokv.com, api.zhihu.com, app.bilibili.com, api.bilibili.com, *.kuwo.cn, *.api.vcinema.cn, api.weibo.cn, mapi.weibo.com, *.uve.weibo.com, api-163.biliapi.net, getuserinfo-globalapi.zymk.cn



[Script]

// tiktok去水印

http-request ^https:\/\/[\s\S]*\/aweme\/v1\/play\/\?video script-path=https://raw.githubusercontent.com/Cyansx/Profiles/master/Surge/Script/Amark.js,requires-body=true

[MITM]

hostname = api.amemv.com, api*.musical.ly, api*.tiktokv.com


//zhihu

http-response https://api.zhihu.com/moments requires-body=1,max-size=0,script-path=https://raw.githubusercontent.com/Cyansx/Profiles/master/Surge/Script/zhihuFeed.js,script-update-interval=-1
http-response https://api.zhihu.com/topstory/recommend requires-body=1,max-size=0,script-path=https://raw.githubusercontent.com/Cyansx/Profiles/master/Surge/Script/zhihuRecommed.js,script-update-interval=-1
http-response https://api.zhihu.com/.*/questions requires-body=1,max-size=0,script-path=https://raw.githubusercontent.com/Cyansx/Profiles/master/Surge/Script/zhihuAnswer.js,script-update-interval=-1
http-response https://api.zhihu.com/market/header requires-body=1,max-size=0,script-path=https://raw.githubusercontent.com/Cyansx/Profiles/master/Surge/Script/zhihuMarket.js,script-update-interval=-1

[MITM]

hostname = api.zhihu.com,

//bilibili

http-response https://app.bilibili.com/x/resource/show/tab requires-body=1,max-size=0,script-path=https://raw.githubusercontent.com/Cyansx/Profiles/master/Surge/Script/bilibiliTab.js,script-update-interval=-1
http-response https://app.bilibili.com/x/v2/feed requires-body=1,max-size=0,script-path=https://raw.githubusercontent.com/Cyansx/Profiles/master/Surge/Script/bilibiliFeed.js,script-update-interval=-1
http-response https://app.bilibili.com/x/v2/account/mine requires-body=1,max-size=0,script-path=https://raw.githubusercontent.com/Cyansx/Profiles/master/Surge/Script/bilibiliAccount.js,script-update-interval=-1
http-response https://app.bilibili.com/x/v2/view\?access_key requires-body=1,max-size=0,script-path=https://raw.githubusercontent.com/Cyansx/Profiles/master/Surge/Script/bilibiliView.js,script-update-interval=-1
http-response https://app.bilibili.com/x/v2/rank requires-body=1,max-size=0,script-path=https://raw.githubusercontent.com/Cyansx/Profiles/master/Surge/Script/bilibiliRank.js,script-update-interval=-1

[MITM]

hostname = app.bilibili.com, api.bilibili.com

//kuwovip

https?:\/\/.*\.kuwo\.cn script-path=https://raw.githubusercontent.com/Cyansx/Profiles/master/Surge/Script/kuwovip.js,requires-body=true

[MITM]

hostname = *.kuwo.cn,
//南瓜电影

http-response https?:\/\/p\.doras\.api\.vcinema\.cn\/v5.0\/user/  script-path= https://raw.githubusercontent.com/Cyansx/Profiles/master/Surge/Script/ngdy.js,requires-body=true

[MITM]

hostname = *.api.vcinema.cn

//微博

http-response ^https?:\/\/(api|mapi)\.weibo\.(cn|com)\/2/(statuses\/(unread|extend|positives/get|friends(\/|_)timeline)|stories\/(video_stream|home_list)|groups\/timeline|fangle\/timeline|profile\/statuses|comments\/build_comments|photo\/recommend_list|service\/picfeed|searchall|cardlist) script-path=https://raw.githubusercontent.com/Cyansx/Profiles/master/Surge/Script/wb_ad.js,requires-body=true

[MITM]

hostname = api.weibo.cn, mapi.weibo.com, *.uve.weibo.com

//网易漫画

 http-response https?:\/\/api-163\.biliapi\.net\/getUserProfile script-path=https://raw.githubusercontent.com/Cyansx/Profiles/master/Surge/Script/wymh.js,requires-body=true

[MITM]

hostname = api-163.biliapi.net, getuserinfo-globalapi.zymk.cn

//知音漫客

http-response ^https://getuserinfo-globalapi.zymk.cn/app_api/v5/(getuserinfo|coin_account|getuserinfo_ticket|getcomicinfo)/ script-path=https://raw.githubusercontent.com/Cyansx/Profiles/master/Surge/Script/zymk.js,requires-body = true

[MITM]

hostname = getuserinfo-globalapi.zymk.cn

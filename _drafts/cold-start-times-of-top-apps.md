---
layout: post
title:  "Cold Start Times: An Analysis of Top Apps"
name: "top apps"
lang: "English"
comments: true
visible: true
author: junfeng/sarvar
---

<script>
var all_data = { "all" : [{"category": "MESSAGING", "rating": 3.9, "methods": -1, "package": "com.facebook.orca", "startTime": 2.22, "name": "Messenger"},
{"category": "SOCIAL", "rating": 4.0, "methods": -1, "package": "com.facebook.katana", "startTime": 2.67, "name": "Facebook"},
{"category": "GAME_ARCADE", "rating": 4.7, "methods": -1, "package": "com.cmplay.tiles2", "startTime": 2.08, "name": "Piano Tiles 2(Don't Tap...2)"},
{"category": "SOCIAL", "rating": 3.9, "methods": -1, "package": "com.snapchat.android", "startTime": 3.35, "name": "Snapchat"},
{"category": "SOCIAL", "rating": 4.5, "methods": -1, "package": "com.instagram.android", "startTime": 1.74, "name": "Instagram"},
{"category": "MUSIC_STREAMING", "rating": 4.4, "methods": -1, "package": "com.pandora.android", "startTime": 3.48, "name": "Pandora Radio"},
{"category": "VIDEO", "rating": 4.4, "methods": -1, "package": "com.netflix.mediaclientS", "startTime": 3.24, "name": "Netflix"},
{"category": "PHOTO_STORING", "rating": 4.3, "methods": -1, "package": "com.google.android.apps.photos", "startTime": 2.39, "name": "Google Photos"},
{"category": "SHOPPING", "rating": 4.5, "methods": -1, "package": "com.contextlogic.wish", "startTime": 1.85, "name": "Wish - Shopping Made Fun"},
{"category": "FLASHLIGHT", "rating": 4.5, "methods": -1, "package": "com.surpax.ledflashlight.panel", "startTime": 2.78, "name": "Super-Bright LED Flashlight"},
{"category": "MUSIC_STREAMING", "rating": 4.5, "methods": -1, "package": "com.spotify.music", "startTime": 2.24, "name": "Spotify Music"},
{"category": "MESSAGING", "rating": 4.4, "methods": -1, "package": "com.whatsapp", "startTime": 2.33, "name": "WhatsApp Messenger"},
{"category": "SPEED_BOOSTER", "rating": 4.7, "methods": -1, "package": "com.cleanmaster.mguard", "startTime": 2.78, "name": "Clean Master (Boost & AppLock)"},
{"category": "VIDEO", "rating": 4.0, "methods": -1, "package": "com.hulu.plus", "startTime": 4.08, "name": "Hulu"},
{"category": "MESSAGING", "rating": 4.3, "methods": -1, "package": "kik.android", "startTime": 3.04, "name": "Kik"},
{"category": "MESSAGING", "rating": 4.4, "methods": -1, "package": "com.jb.gosms", "startTime": 4.06, "name": "GO SMS Pro"},
{"category": "SOCIAL", "rating": 4.5, "methods": -1, "package": "com.pinterest", "startTime": 2.3, "name": "Pinterest"},
{"category": "SPEED_BOOSTER", "rating": 4.6, "methods": -1, "package": "com.qihoo.security", "startTime": 3.51, "name": "360 Security - Antivirus Boost"},
{"category": "PERSONALIZATION", "rating": 4.6, "methods": -1, "package": "net.zedge.android", "startTime": 4.71, "name": "ZEDGE Ringtones & Wallpapers"},
{"category": "SPEED_BOOSTER", "rating": 4.5, "methods": -1, "package": "com.dianxinos.dxbs", "startTime": 2.02, "name": "DU Battery Saver&Phone Charger"},
{"category": "SHOPPING", "rating": 4.2, "methods": -1, "package": "com.amazon.mShop.android.shopping", "startTime": 4.38, "name": "Amazon Shopping"},
{"category": "FINANCE", "rating": 4.7, "methods": -1, "package": "com.creditkarma.mobile", "startTime": 1.83, "name": "Credit Karma"},
{"category": "MESSAGING", "rating": 4.1, "methods": -1, "package": "com.skype.raider", "startTime": 6.71, "name": "Skype - free IM & video calls"},
{"category": "MUSIC_STREAMING", "rating": 4.4, "methods": -1, "package": "com.soundcloud.android", "startTime": 2.95, "name": "SoundCloud - Music & Audio"},
{"category": "GAME_STRATEGY", "rating": 4.6, "methods": -1, "package": "com.supercell.clashofclans", "startTime": 1.84, "name": "Clash of Clans"},
{"category": "WEATHER", "rating": 4.3, "methods": -1, "package": "com.weather.Weather", "startTime": 3.84, "name": "The Weather Channel"},
{"category": "TOOLS", "rating": 4.4, "methods": -1, "package": "com.emoji.coolkeyboard", "startTime": 2.34, "name": "Emoji Keyboard Pro Kika Free"},
{"category": "SPEED_BOOSTER", "rating": 4.6, "methods": -1, "package": "com.gto.zero.zboost", "startTime": 1.54, "name": "Z Speed+ | Junk Clean, AppLock"},
{"category": "TRANSPORTATION", "rating": 4.2, "methods": -1, "package": "com.ubercab", "startTime": 11.83, "name": "Uber"},
{"category": "EMAIL", "rating": 4.2, "methods": -1, "package": "com.yahoo.mobile.client.android.mail", "startTime": 2.24, "name": "Yahoo Mail \u2013 Free Email App"},
{"category": "GAME_CASUAL", "rating": 4.3, "methods": -1, "package": "com.king.candycrushsaga", "startTime": 2.06, "name": "Candy Crush Saga"},
{"category": "SPEED_BOOSTER", "rating": 4.7, "methods": -1, "package": "com.cleanmaster.security", "startTime": 2.42, "name": "CM Security Antivirus AppLock"},
{"category": "SOCIAL", "rating": 4.2, "methods": -1, "package": "com.twitter.android", "startTime": 2.46, "name": "Twitter"},
{"category": "SHOPPING", "rating": 4.6, "methods": -1, "package": "com.offerup", "startTime": 4.67, "name": "OfferUp - Buy. Sell. Offer Up"},
{"category": "HEALTH_AND_FITNESS", "rating": 3.9, "methods": -1, "package": "com.fitbit.FitbitMobile", "startTime": 2.09, "name": "Fitbit"},
{"category": "MUSIC_STREAMING", "rating": 4.6, "methods": -1, "package": "com.clearchannel.iheartradio.controller", "startTime": 3.25, "name": "iHeartRadio: Top Radio & Music"},
{"category": "SHOPPING", "rating": 4.3, "methods": -1, "package": "com.wallapop", "startTime": 2.77, "name": "Wallapop"},
{"category": "PHOTO_EDITING", "rating": 4.2, "methods": -1, "package": "com.instagram.layout", "startTime": 2.32, "name": "Layout from Instagram: Collage"},
{"category": "PHOTO_EDITING", "rating": 4.4, "methods": -1, "package": "com.cyberlink.youcammakeup", "startTime": 4.3, "name": "YouCam Makeup - Makeover Studio"},
{"category": "SHOPPING", "rating": 4.0, "methods": -1, "package": "com.mcdonalds.app", "startTime": 2.92, "name": "McDonald's"},
{"category": "SPEED_BOOSTER", "rating": 4.5, "methods": -1, "package": "com.lionmobi.powerclean", "startTime": 4.34, "name": "Power Clean - Optimize Cleaner"},
{"category": "FILE_SHARING", "rating": 4.3, "methods": -1, "package": "com.fw.appshare", "startTime": 3.12, "name": "ShareCloud - Share By 1-Click"},
{"category": "TOOLS", "rating": 4.3, "methods": -1, "package": "com.google.android.apps.chromecast.app", "startTime": 1.98, "name": "Chromecast"},
{"category": "MESSAGING", "rating": 4.1, "methods": -1, "package": "com.pinger.textfree", "startTime": 2.69, "name": "Text Free - Free Text + Calls"},
{"category": "MESSAGING", "rating": 4.2, "methods": -1, "package": "com.imo.android.imoim", "startTime": 2.58, "name": "imo free video calls and chat"},
{"category": "TOOLS", "rating": 4.2, "methods": -1, "package": "emoji.keyboard.emoticonkeyboard", "startTime": 2.08, "name": "Emoji Keyboard Cute Emoticons"},
{"category": "MESSAGING", "rating": 4.2, "methods": -1, "package": "com.enflick.android.TextNow", "startTime": 2.12, "name": "TextNow - free text + calls"},
{"category": "PHOTO_EDITING", "rating": 4.4, "methods": -1, "package": "com.cheerfulinc.flipagram", "startTime": 2.68, "name": "Flipagram"},
{"category": "SHOPPING", "rating": 4.2, "methods": -1, "package": "com.ebay.mobile", "startTime": 4.65, "name": "eBay"},
{"category": "TOOLS", "rating": 4.5, "methods": -1, "package": "com.jb.emoji.gokeyboard", "startTime": 1.83, "name": "GO Keyboard - Emoji, Sticker"},
{"category": "NEWS", "rating": 4.2, "methods": -1, "package": "com.espn.score_center", "startTime": 2.31, "name": "ESPN"},
{"category": "SHOPPING", "rating": 4.4, "methods": -1, "package": "com.zillow.android.zillowmap", "startTime": 3.77, "name": "Zillow Real Estate & Rentals"},
{"category": "BOOKS_AND_REFERENCE", "rating": 4.6, "methods": -1, "package": "com.sirma.mobile.bible.android", "startTime": 6.65, "name": "Bible"},
{"category": "MESSAGING", "rating": 4.3, "methods": -1, "package": "com.oovoo", "startTime": 2.89, "name": "ooVoo Video Call, Text & Voice"},
{"category": "TOOLS", "rating": 4.4, "methods": -1, "package": "com.google.android.apps.translate", "startTime": 1.3, "name": "Google Translate"},
{"category": "TRAVEL_AND_LOCAL", "rating": 4.6, "methods": -1, "package": "com.waze", "startTime": 12.49, "name": "Waze - GPS, Maps & Traffic"},
{"category": "SHOPPING", "rating": 4.4, "methods": -1, "package": "com.walmart.android", "startTime": 3.31, "name": "Walmart"},
{"category": "MESSAGING", "rating": 4.2, "methods": -1, "package": "com.sgiggle.production", "startTime": 2.73, "name": "Tango - Free Video Call & Chat"},
{"category": "DATING", "rating": 4.0, "methods": -1, "package": "com.tinder", "startTime": 1.71, "name": "Tinder"},
{"category": "MEDIA_AND_VIDEO", "rating": 4.1, "methods": -1, "package": "com.riffsy.FBMGIFApp", "startTime": 3.38, "name": "GIF Keyboard"},
{"category": "TRAVEL_AND_LOCAL", "rating": 4.3, "methods": -1, "package": "com.yelp.android", "startTime": 2.15, "name": "Yelp"},
{"category": "PRODUCTIVITY", "rating": 4.1, "methods": -1, "package": "com.google.android.apps.docs.editors.docs", "startTime": 3.14, "name": "Google Docs"},
{"category": "LIFESTYLE", "rating": 4.0, "methods": -1, "package": "com.lucktastic.scratch", "startTime": 5.27, "name": "Lucktastic"},
{"category": "HEALTH_AND_FITNESS", "rating": 4.6, "methods": -1, "package": "com.myfitnesspal.android", "startTime": 4.27, "name": "Calorie Counter - MyFitnessPal"},
{"category": "MUSIC_STREAMING", "rating": 4.5, "methods": -1, "package": "my.googlemusic.play", "startTime": 2.15, "name": "My Mixtapez Music & Mixtapes"},
{"category": "KARAOKE", "rating": 3.9, "methods": -1, "package": "com.smule.singandroid", "startTime": 3.47, "name": "Sing! Karaoke by Smule"},
{"category": "SHOPPING", "rating": 4.4, "methods": -1, "package": "com.contextlogic.geek", "startTime": 1.86, "name": "Geek - Smarter Shopping"},
{"category": "VIDEO", "rating": 4.1, "methods": -1, "package": "com.google.android.youtube", "startTime": 1.99, "name": "YouTube"},
{"category": "MUSIC_AND_AUDIO", "rating": 4.4, "methods": -1, "package": "com.shazam.android", "startTime": 4.86, "name": "Shazam"},
{"category": "SOCIAL", "rating": 4.4, "methods": -1, "package": "com.tumblr", "startTime": 2.26, "name": "Tumblr"},
{"category": "TOOLS", "rating": 4.3, "methods": -1, "package": "com.gamma.scan", "startTime": 2.42, "name": "QR & Barcode Scanner"},
{"category": "VIDEO", "rating": 4.2, "methods": -1, "package": "com.google.android.apps.youtube.kids", "startTime": 7.51, "name": "YouTube Kids"},
{"category": "TRAVEL_AND_LOCAL", "rating": 4.3, "methods": -1, "package": "com.google.earth", "startTime": 1.97, "name": "Google Earth"},
{"category": "PRODUCTIVITY", "rating": 3.6, "methods": -1, "package": "com.microsoft.office.outlook", "startTime": 2.71, "name": "Microsoft Outlook"},
{"category": "LAUNCHER", "rating": 4.5, "methods": -1, "package": "com.hola.launcher", "startTime": 2.63, "name": "Hola Launcher"},
{"category": "EDUCATION", "rating": 4.6, "methods": -1, "package": "com.duolingo", "startTime": 2.53, "name": "Duolingo: Learn Languages Free"},
{"category": "SOCIAL", "rating": 4.2, "methods": -1, "package": "com.mobilemotion.dubsmash", "startTime": 3.25, "name": "Dubsmash"},
{"category": "BOOKS_AND_REFERENCE", "rating": 4.1, "methods": -1, "package": "com.amazon.kindle", "startTime": 5.18, "name": "Amazon Kindle"},
{"category": "SHOPPING", "rating": 4.5, "methods": -1, "package": "com.groupon", "startTime": 3.82, "name": "Groupon - Shop Deals & Coupons"},
{"category": "PRODUCTIVITY", "rating": 4.3, "methods": -1, "package": "com.adobe.reader", "startTime": 1.56, "name": "Adobe Acrobat Reader"},
{"category": "PHOTO_EDITING", "rating": 4.4, "methods": -1, "package": "com.pipcamera.activity", "startTime": 2.76, "name": "PIP Camera - Photo Editor Pro"},
{"category": "DATING", "rating": 4.4, "methods": -1, "package": "com.badoo.mobile", "startTime": 2.82, "name": "Badoo - Meet New People"},
{"category": "SOCIAL", "rating": 4.2, "methods": -1, "package": "co.vine.android", "startTime": 1.18, "name": "Vine - video entertainment"},
{"category": "SPEED_BOOSTER", "rating": 4.5, "methods": -1, "package": "com.psafe.msuite", "startTime": 3.56, "name": "Antivirus Booster & Cleaner"},
{"category": "SPEED_BOOSTER", "rating": 4.5, "methods": -1, "package": "com.dianxinos.optimizer.duplay", "startTime": 4.05, "name": "DU Speed Booster & Antivirus"},
{"category": "PHOTO_EDITING", "rating": 4.5, "methods": -1, "package": "com.roidapp.photogrid", "startTime": 2.87, "name": "Photo Grid - Collage Maker"},
{"category": "DATING", "rating": 4.2, "methods": -1, "package": "com.pof.android", "startTime": 2.69, "name": "POF Free Dating App"},
{"category": "BOOKS_AND_REFERENCE", "rating": 4.2, "methods": -1, "package": "com.audible.application", "startTime": 5.53, "name": "Audiobooks from Audible"},
{"category": "PHOTO_EDITING", "rating": 4.4, "methods": -1, "package": "com.picsart.studio", "startTime": 3.48, "name": "PicsArt Photo Studio"},
{"category": "TRANSPORTATION", "rating": 4.3, "methods": -1, "package": "me.lyft.android", "startTime": 3.45, "name": "Lyft - Taxi & Bus Alternative"},
{"category": "MUSIC_AND_AUDIO", "rating": 4.0, "methods": -1, "package": "com.musicplayer.music", "startTime": 1.75, "name": "Default Music Player"},
{"category": "FLASHLIGHT", "rating": 4.5, "methods": -1, "package": "com.intellectualflame.ledflashlight.washer", "startTime": 3.35, "name": "Brightest LED Flashlight"},
{"category": "MESSAGING", "rating": 4.2, "methods": -1, "package": "jp.naver.line.android", "startTime": 2.78, "name": "LINE: Free Calls & Messages"},
{"category": "MUSIC_STREAMING", "rating": 4.2, "methods": -1, "package": "com.madebyappolis.spinrilla", "startTime": 4.16, "name": "Spinrilla"},
{"category": "BROWSER", "rating": 4.4, "methods": -1, "package": "org.mozilla.firefox", "startTime": 1.46, "name": "Firefox Browser for Android"},
{"category": "PHOTO_EDITING", "rating": 4.3, "methods": -1, "package": "com.zentertain.photoeditor", "startTime": 3.55, "name": "Photo Editor Pro"},
{"category": "SHOPPING", "rating": 4.4, "methods": -1, "package": "com.whaleshark.retailmenot", "startTime": 2.69, "name": "RetailMeNot Coupons, Discounts"},
{"category": "MESSAGING", "rating": 4.3, "methods": -1, "package": "com.viber.voip", "startTime": 2.4, "name": "Viber"},
{"category": "ENTERTAINMENT", "rating": 4.2, "methods": -1, "package": "com.scee.psxandroid", "startTime": 2.4, "name": "PlayStationApp"},
{"category": "MUSIC_CREATION", "rating": 4.0, "methods": -1, "package": "com.smule.magicpiano", "startTime": 9.77, "name": "Magic Piano by Smule"},
{"category": "COMMUNICATION", "rating": 4.0, "methods": -1, "package": "com.talkatone.android", "startTime": 3.53, "name": "Talkatone free calls & texting"},
{"category": "ENTERTAINMENT", "rating": 4.2, "methods": -1, "package": "com.digidust.elokence.akinator.freemium", "startTime": 6.01, "name": "Akinator the Genie FREE"},
{"category": "MEDIA_AND_VIDEO", "rating": 4.0, "methods": -1, "package": "audio.mp3.music.player", "startTime": 7.75, "name": "Music Player Pro"},
{"category": "SOCIAL", "rating": 4.2, "methods": -1, "package": "com.linkedin.android", "startTime": 2.5, "name": "LinkedIn"},
{"category": "ENTERTAINMENT", "rating": 3.7, "methods": -1, "package": "com.gotv.crackle.handset", "startTime": 3.33, "name": "Crackle - Movies & TV"},
{"category": "MUSIC_STREAMING", "rating": 4.0, "methods": -1, "package": "com.nextradioapp.nextradio", "startTime": 1.84, "name": "NextRadio - Free Live FM Radio"},
{"category": "COMMUNICATION", "rating": 4.4, "methods": -1, "package": "com.antivirus", "startTime": 2.28, "name": "AntiVirus FREE - Security Scan"},
{"category": "TOOLS", "rating": 4.2, "methods": -1, "package": "com.apalon.myclockfree", "startTime": 3.05, "name": "My Alarm Clock Free"},
{"category": "FINANCE", "rating": 4.4, "methods": -1, "package": "com.chase.sig.android", "startTime": 3.66, "name": "Chase Mobile"},
{"category": "EDUCATION", "rating": 4.1, "methods": -1, "package": "org.pbskids.video", "startTime": 2.13, "name": "PBS KIDS Video"},
{"category": "ENTERTAINMENT", "rating": 3.5, "methods": -1, "package": "com.nbcuni.nbc", "startTime": 7.51, "name": "NBC"},
{"category": "TOOLS", "rating": 4.3, "methods": -1, "package": "com.domobile.applock", "startTime": 1.42, "name": "AppLock"},
{"category": "MUSIC_STREAMING", "rating": 4.3, "methods": -1, "package": "tunein.player", "startTime": 5.23, "name": "TuneIn Radio - Radio & Music"},
{"category": "SHOPPING", "rating": 4.1, "methods": -1, "package": "com.poshmark.app", "startTime": 2.22, "name": "Poshmark - Buy & Sell Fashion"},
{"category": "MEDIA_AND_VIDEO", "rating": 4.5, "methods": -1, "package": "com.quvideo.xiaoying", "startTime": 4.12, "name": "VivaVideo: Free Video Editor"},
{"category": "MUSIC_STREAMING", "rating": 4.3, "methods": -1, "package": "com.beatsmusic.android.client", "startTime": 2.09, "name": "Beats Music"},
{"category": "PRODUCTIVITY", "rating": 4.4, "methods": -1, "package": "com.dropbox.android", "startTime": 2.02, "name": "Dropbox"},
{"category": "WEATHER", "rating": 4.5, "methods": -1, "package": "com.handmark.expressweather", "startTime": 2.49, "name": "1Weather:Widget Forecast Radar"},
{"category": "ENTERTAINMENT", "rating": 3.9, "methods": -1, "package": "com.disney.disneymoviesanywhere_goo", "startTime": 2.48, "name": "Disney Movies Anywhere"},
{"category": "FINANCE", "rating": 4.2, "methods": -1, "package": "com.infonow.bofa", "startTime": 3.76, "name": "Bank of America"},
{"category": "COMMUNICATION", "rating": 4.2, "methods": -1, "package": "com.android.chrome", "startTime": 2.78, "name": "Chrome Browser - Google"},
{"category": "MEDIA_AND_VIDEO", "rating": 3.8, "methods": -1, "package": "com.turner.cnvideoapp", "startTime": 2.94, "name": "Cartoon Network App"},
{"category": "SOCIAL", "rating": 3.9, "methods": -1, "package": "tv.periscope.android", "startTime": 2.27, "name": "Periscope"},
{"category": "ENTERTAINMENT", "rating": 4.3, "methods": -1, "package": "com.outfit7.talkingtom2free", "startTime": 2.56, "name": "Talking Tom Cat 2"},
{"category": "ENTERTAINMENT", "rating": 4.7, "methods": -1, "package": "tv.twitch.android.app", "startTime": 2.41, "name": "Twitch"},
{"category": "WEATHER", "rating": 4.3, "methods": -1, "package": "com.droid27.transparentclockweather", "startTime": 1.84, "name": "Transparent clock & weather"},
{"category": "PRODUCTIVITY", "rating": 4.1, "methods": -1, "package": "com.google.android.calendar", "startTime": 1.99, "name": "Google Calendar"},
{"category": "SHOPPING", "rating": 4.2, "methods": -1, "package": "com.shopkick.app", "startTime": 2.12, "name": "shopkick: Rewards & Deals"},
{"category": "FINANCE", "rating": 4.2, "methods": -1, "package": "com.wf.wellsfargomobile", "startTime": 1.93, "name": "Wells Fargo Mobile"},
{"category": "TOOLS", "rating": 4.7, "methods": -1, "package": "goldenshorestechnologies.brightestflashlight.free", "startTime": 3.93, "name": "Brightest Flashlight Free "},
{"category": "SHOPPING", "rating": 4.1, "methods": -1, "package": "com.amazon.now", "startTime": 2.16, "name": "Amazon Prime Now"},
{"category": "BUSINESS", "rating": 4.0, "methods": -1, "package": "com.indeed.android.jobsearch", "startTime": 1.8, "name": "Job Search"},
{"category": "WEATHER", "rating": 4.3, "methods": -1, "package": "com.accuweather.android", "startTime": 1.78, "name": "AccuWeather"},
{"category": "SPORTS", "rating": 4.1, "methods": -1, "package": "air.WatchESPN", "startTime": 4.81, "name": "WatchESPN"},
{"category": "ENTERTAINMENT", "rating": 4.1, "methods": -1, "package": "com.xfinity.playnow", "startTime": 2.22, "name": "XFINITY TV Go"},
{"category": "TOOLS", "rating": 4.4, "methods": -1, "package": "com.google.android.googlequicksearchbox", "startTime": 2.35, "name": "Google"},
{"category": "FINANCE", "rating": 4.2, "methods": -1, "package": "com.paypal.android.p2pmobile", "startTime": 2.18, "name": "PayPal"},
{"category": "ENTERTAINMENT", "rating": 4.5, "methods": -1, "package": "com.fandango", "startTime": 8.79, "name": "Fandango Movies"},
{"category": "HEALTH_AND_FITNESS", "rating": 4.4, "methods": -1, "package": "com.fitnow.loseit", "startTime": 1.85, "name": "Lose It!"},
{"category": "PRODUCTIVITY", "rating": 4.2, "methods": -1, "package": "com.google.android.apps.docs.editors.sheets", "startTime": 3.02, "name": "Google Sheets"},
{"category": "MUSIC_AND_AUDIO", "rating": 4.0, "methods": -1, "package": "com.eliferun.music", "startTime": 6.33, "name": "Music Player for Android"},
{"category": "ENTERTAINMENT", "rating": 4.5, "methods": -1, "package": "com.bitstrips.imoji", "startTime": 1.97, "name": "Bitmoji - Your Avatar Emoji"},
{"category": "FINANCE", "rating": 4.1, "methods": -1, "package": "com.intuit.turbotax.mobile", "startTime": 6.93, "name": "TurboTax Tax Return App"},
{"category": "SHOPPING", "rating": 4.2, "methods": -1, "package": "com.ibotta.android", "startTime": 2.34, "name": "Ibotta \u2013 Cash back Coupons."},
{"category": "SOCIAL", "rating": 4.1, "methods": -1, "package": "com.gogii.textplus", "startTime": 4.03, "name": "textPlus Free Text + Calls"},
{"category": "ENTERTAINMENT", "rating": 4.5, "methods": -1, "package": "com.roku.remote", "startTime": 1.47, "name": "Roku"},
{"category": "MEDIA_AND_VIDEO", "rating": 4.1, "methods": -1, "package": "com.giphy.messenger", "startTime": 2.4, "name": "GIPHY for Messenger"},
{"category": "BOOKS_AND_REFERENCE", "rating": 4.6, "methods": -1, "package": "com.hmobile.biblekjv", "startTime": 2.54, "name": "King James Bible (KJV) Free"},
{"category": "PHOTOGRAPHY", "rating": 4.5, "methods": -1, "package": "com.cardinalblue.piccollage.google", "startTime": 2.33, "name": "Pic Collage"},
{"category": "ENTERTAINMENT", "rating": 3.7, "methods": -1, "package": "com.mtvn.mtvPrimeAndroid", "startTime": 8.18, "name": "MTV"},
{"category": "ENTERTAINMENT", "rating": 4.4, "methods": -1, "package": "mobi.ifunny", "startTime": 2.87, "name": "iFunny :)"},
{"category": "ENTERTAINMENT", "rating": 4.1, "methods": -1, "package": "com.outfit7.tomlovesangelafree", "startTime": 2.3, "name": "Tom Loves Angela"},
{"category": "SPORTS", "rating": 4.1, "methods": -1, "package": "com.gotv.nflgamecenter.us.lite", "startTime": 7.43, "name": "NFL Mobile"},
{"category": "SHOPPING", "rating": 4.2, "methods": -1, "package": "com.mercariapp.mercari", "startTime": 3.12, "name": "Mercari: Anyone can buy & sell"},
{"category": "MEDIA_AND_VIDEO", "rating": 4.3, "methods": -1, "package": "org.videolan.vlc", "startTime": 2.28, "name": "VLC for Android"},
{"category": "TOOLS", "rating": 4.2, "methods": -1, "package": "com.socialnmobile.hd.flashlight", "startTime": 1.97, "name": "Color Flashlight"},
{"category": "ENTERTAINMENT", "rating": 3.7, "methods": -1, "package": "com.outfit7.talkingangelafree", "startTime": 3.54, "name": "Talking Angela"},
{"category": "ENTERTAINMENT", "rating": 3.8, "methods": -1, "package": "com.cbs.app", "startTime": 10.17, "name": "CBS"},
{"category": "ENTERTAINMENT", "rating": 4.0, "methods": -1, "package": "com.hbo.hbonow", "startTime": 2.56, "name": "HBO NOW"},
{"category": "SOCIAL", "rating": 4.2, "methods": -1, "package": "com.myyearbook.m", "startTime": 2.93, "name": "MeetMe: Chat & Meet New People"},
{"category": "PERSONALIZATION", "rating": 4.6, "methods": -1, "package": "com.cmcm.locker", "startTime": 2.54, "name": "CM Locker (Secure & Boost)"},
{"category": "FINANCE", "rating": 4.0, "methods": -1, "package": "com.konylabs.capitalone", "startTime": 2.78, "name": "Capital One Mobile"},
{"category": "MUSIC_AND_AUDIO", "rating": 4.3, "methods": -1, "package": "com.melodis.midomiMusicIdentifier.freemium", "startTime": 3.2, "name": "SoundHound Music Search"},
{"category": "ENTERTAINMENT", "rating": 4.3, "methods": -1, "package": "com.outfit7.talkinggingerfree", "startTime": 3.29, "name": "Talking Ginger"},
{"category": "TOOLS", "rating": 4.0, "methods": -1, "package": "me.scan.android.client", "startTime": 1.82, "name": "QR Code Reader"},
{"category": "TOOLS", "rating": 4.1, "methods": -1, "package": "com.yadavapp.keypadlockscreen", "startTime": 3.01, "name": "Keypad Lock Screen"},
{"category": "SHOPPING", "rating": 4.0, "methods": -1, "package": "com.target.socsav", "startTime": 2.47, "name": "Cartwheel by Target"},
{"category": "EDUCATION", "rating": 4.3, "methods": -1, "package": "com.classdojo.android", "startTime": 2.02, "name": "ClassDojo"},
{"category": "SHOPPING", "rating": 4.2, "methods": -1, "package": "com.usablenet.mobile.walgreen", "startTime": 6.42, "name": "Walgreens"},
{"category": "ENTERTAINMENT", "rating": 4.4, "methods": -1, "package": "com.microsoft.xboxone.smartglass", "startTime": 2.21, "name": "Xbox One SmartGlass"},
{"category": "ENTERTAINMENT", "rating": 3.6, "methods": -1, "package": "air.com.vudu.air.DownloaderTablet", "startTime": 7.91, "name": "VUDU Movies & TV"},
{"category": "PRODUCTIVITY", "rating": 4.5, "methods": -1, "package": "com.estrongs.android.pop", "startTime": 4.22, "name": "ES File Explorer File Manager"},
{"category": "EDUCATION", "rating": 4.2, "methods": -1, "package": "mobi.abcmouse.academy_goo", "startTime": 13.71, "name": "ABCmouse.com"},
{"category": "SHOPPING", "rating": 4.2, "methods": -1, "package": "com.etsy.android", "startTime": 3.54, "name": "Etsy: Handmade & Vintage Goods"},
{"category": "SOCIAL", "rating": 4.2, "methods": -1, "package": "com.google.android.apps.plus", "startTime": 1.8, "name": "Google+"},
{"category": "TOOLS", "rating": 4.4, "methods": -1, "package": "org.zwanoo.android.speedtest", "startTime": 2.68, "name": "Speedtest.net"},
{"category": "ENTERTAINMENT", "rating": 3.7, "methods": -1, "package": "com.turner.cnanything", "startTime": 2.73, "name": "Cartoon Network Anything"},
{"category": "SOCIAL", "rating": 3.8, "methods": -1, "package": "com.match.android.matchmobile", "startTime": 2.42, "name": "Match Dating - Meet Singles"},
{"category": "ENTERTAINMENT", "rating": 4.3, "methods": -1, "package": "com.outfit7.talkingtom", "startTime": 2.72, "name": "Talking Tom Cat"},
{"category": "PHOTOGRAPHY", "rating": 4.1, "methods": -1, "package": "com.fotoable.fotobeauty", "startTime": 3.84, "name": "InstaBeauty - Selfie Camera"},
{"category": "MEDIA_AND_VIDEO", "rating": 4.2, "methods": -1, "package": "com.herman.ringtone", "startTime": 1.93, "name": "Ringtone Maker"},
{"category": "COMMUNICATION", "rating": 4.4, "methods": -1, "package": "com.groupme.android", "startTime": 1.85, "name": "GroupMe"},
{"category": "ENTERTAINMENT", "rating": 4.3, "methods": -1, "package": "com.outfit7.talkingben", "startTime": 2.06, "name": "Talking Ben the Dog"},
{"category": "SHOPPING", "rating": 4.3, "methods": -1, "package": "com.abtnprojects.ambatana", "startTime": 2.54, "name": "letgo: Buy & Sell Used Stuff"},
{"category": "ENTERTAINMENT", "rating": 3.0, "methods": -1, "package": "com.disney.datg.videoplatforms.android.abc", "startTime": 2.31, "name": "WATCH ABC"},
{"category": "SHOPPING", "rating": 4.2, "methods": -1, "package": "com.tophatter", "startTime": 2.71, "name": "Tophatter: up to 80% Off"},
{"category": "PRODUCTIVITY", "rating": 4.5, "methods": -1, "package": "com.socialnmobile.dictapps.notepad.color.note", "startTime": 1.84, "name": "ColorNote Notepad Notes"},
{"category": "PHOTOGRAPHY", "rating": 4.0, "methods": -1, "package": "com.superphoto", "startTime": 1.63, "name": "SuperPhoto - Effects + Filters"},
] };


function compareTime(arrObj1, arrObj2) {
  return arrObj1["startTime"] - arrObj2["startTime"];
}

var cat_data = jQuery.extend(true, {}, all_data);

var filteredArr = {};

for (var i=0, len=cat_data["all"].length; i < len; i++)
    filteredArr[cat_data["all"][i]['name']] = cat_data["all"][i];

cat_data["all"] = new Array();
for (var key in filteredArr)
    cat_data["all"].push(filteredArr[key]);

Chart.types.HorizontalBar.extend({
  name:"HorizontalBarWithXLabel",
  draw: function () {
      Chart.types.HorizontalBar.prototype.draw.apply(this, arguments);

      this.chart.ctx.save();
      this.chart.ctx.textAlign = "center";
      this.chart.ctx.textBaseline = "top";
      this.chart.ctx.fillStyle = this.options.scaleFontColor;
      var x = this.scale.width/1.7;
      var y = 0;
      this.chart.ctx.translate(x,y);
      this.chart.ctx.fillText("Cold Start Time (seconds)", 0, 0);
      this.chart.ctx.restore();


    }
});

    Chart.types.Bar.extend({
        name: "BarWithLine",
        draw: function () {
            Chart.types.Bar.prototype.draw.apply(this, arguments);

            var lines = this.options.limitLines;

            for (var i = lines.length; --i >= 0;) {

                var xStart = Math.round(this.scale.xScalePaddingLeft);
                var linePositionY = this.scale.calculateY(lines[i].value);

                this.chart.ctx.fillStyle = lines[i].color ? lines[i].color : this.scale.textColor;
                this.chart.ctx.font = this.scale.font;
                this.chart.ctx.textAlign = "left";
                this.chart.ctx.textBaseline = "top";

                if (this.scale.showLabels && lines[i].label) {
                    this.chart.ctx.fillText(lines[i].label, xStart, linePositionY+3);
                }

                this.chart.ctx.lineWidth = this.scale.gridLineWidth;
                this.chart.ctx.strokeStyle = lines[i].color ? lines[i].color : this.scale.gridLineColor;

                if (this.scale.showHorizontalLines) {
                    this.chart.ctx.beginPath();
                    this.chart.ctx.moveTo(xStart, linePositionY);
                    this.chart.ctx.lineTo(this.scale.width, linePositionY);
                    this.chart.ctx.stroke();
                    this.chart.ctx.closePath();
                }

                this.chart.ctx.lineWidth = this.lineWidth;
                this.chart.ctx.strokeStyle = this.lineColor;
                this.chart.ctx.beginPath();
                this.chart.ctx.moveTo(xStart, linePositionY);
                this.chart.ctx.lineTo(xStart, linePositionY);
                this.chart.ctx.stroke();
                this.chart.ctx.closePath();
            }

            //Add y axis label
            this.chart.ctx.save();
            // text alignment and color
            this.chart.ctx.textAlign = "center";
            this.chart.ctx.textBaseline = "bottom";
            this.chart.ctx.fillStyle = this.options.scaleFontColor;
            // position
            var x = this.scale.xScalePaddingLeft * 0.4;
            var y = this.chart.height / 2;
            // change origin
            this.chart.ctx.translate(x, y)
            // rotate text
            this.chart.ctx.rotate(-90 * Math.PI / 180);
            this.chart.ctx.fillText(this.datasets[0].label, 0, 0);
            this.chart.ctx.restore();

            //Add x axis label
            // this.chart.ctx.save();
            // this.chart.ctx.textAlign = "center";
            // this.chart.ctx.textBaseline = "bottom";
            // this.chart.ctx.fillStyle = this.options.scaleFontColor;
            // var x = this.scale.width/2;
            // var y = this.chart.height;
            // this.chart.ctx.translate(x,y);
            // this.chart.ctx.fillText("App Name", 0, 0);
            // this.chart.ctx.restore();

        }
    });
</script>

We’ve stressed that apps need to start up fast in
[a prior blog post]({{site.url }}{{ site.baseurl}}/2015/09/17/how-to-make-your-application-fluid.html), but how fast do
existing apps start?  Here we examine the startup times of the top 100
apps in Google Play and share the insights we find.

#Background: Three Types of App Starts

There are actually three different types of app starts: first starts, cold
starts, and warm starts.

*First starts* are what you'd expect them to be -- when a user opens your
app for the first time after installing your app.  First starts are the
slowest because the mobile operating system and the app need to initialize
many things such as creating a SQLite database or compiling multidex files
into native code.  While first starts should be as short as possible, they
only occur once per app install/upgrade, so continuously measuring them
isn’t as significant as measuring the other types of starts.

*Cold starts* occur when users open your app after they haven't run it for
a while.  Cold starts are "cold" because mobile operating systems remove
inactive apps from memory to make room for active apps.  Cold starts are
thus slow because the app's code, assets, and objects have to be reloaded
or recreated.  If users open your app a few times a day, each of these
starts is a cold start, so it is important to optimize cold starts for
better user experience.

*Warm starts* occur when users quickly return to your app after switching
away.  The app is still "warm" in memory, so warm starts are often very
fast.

To summarize, among the three types of starts, **cold starts affect user
experience the most**, so below we focus on cold start times in our study.

#What Are Cold Start Times for Top Apps Like?

To study app cold start times, we picked the top 100 non-game apps ranked
by Google Play.  We used the ranking data as of Jan 6, 2016 because Google
Play ranks apps based on [a number of different
elements](http://getappcase.com/blog/app-stores/how-does-google-play-rank-mobile-apps)
including download volume, performance, user ratings, and social media
popularity, most of which change over time.  We excluded games because
users have higher tolerance for slow game starts because they know the
games have to load much graphics resources. We also excluded some apps
that we don't currently support, such as those that require accurate GPS
location (our device cloud is indoor).

<!--- When we compare the 20 fastest and 20 slowest apps in the Play Store's top 200, we see that the faster group's average rating of 4.26 is higher than the slower group's rating of 4.13. This suggests a slight negative correlation between cold start time and user satisfaction.

To be fair, the order of the top apps is constantly changing, so this data will inevitably fluctuate. However, it’s only intuitive that users will be happier with faster apps. A ton of factors affect user satisfaction, and even though it's easily forgotten, startup time is arguably one of the most important since it’s the first impression a user has of your app.

The fact that the top 20 apps have such low start times relative to their complexity hints at the emphasis good developers (and companies!) place on app performance. For example, [Facebook has cut its cold start time by nearly four seconds across versions](https://nimbledroid.com/play/com.facebook.katana?p=2DGKv6k20NTBdL#Summary) whereas less popular apps such as [Fox News](https://nimbledroid.com/play/com.foxnews.android) tend to fluctuate in start times across versions.

ideas:
  which company makes the fastest apps
  are apps getting faster?
--->

We've compiled the data in the following graph:


<a name ="top"></a>

<div style="margin-left:20%; margin-bottom:10px"> Show me the top

<select ONCHANGE="changeDataNum(this)" class ="custom-select" id="select-all-data" style="float:none; margin-left:0; width: 80px">
<option value = "25">25</option>
<option value = "50">50</option>
<option value = "100">100</option>
</select>

apps sorted by

<select ONCHANGE="toggleCheckbox(); sortCheckbox(this)" id="toggle-top-sort" class="custom-select" style="float:none; margin-left:0; width:150px">
<option value = "rank">google play rank</option>
<option value = "time">cold start time</option>
</select>
</div>


<div style="margin: 0 auto;">
  <canvas id="top25" height="500px" width="500px" style=""></canvas>
</div>

<label class="custom-checkbox" style="margin-left:0; display: none" ><input type="checkbox" onclick="sortCheckbox(this)" id="sort-by-time"></label>





<br>

There are a number of interesting insights in this data.  Let's look at
the top 25 apps first.  Of them, 6 apps start in under or around 2
seconds, 15 in under 3 seconds -- these apps are pretty quick to start up.
[Instagram](XXX-link-to-nimbledroid-results) starts the fastest -- which
is not surprising given [the huge effort the Instagram developers put into
profiling and optimizing their Android
app](http://instagram-engineering.tumblr.com/post/97740520316/betterandroid).
[Skype](XXX) is the slowest with a 6.71 second startup time, even **42%**
slower than [ZEDGE](XXX) the second slowest app.

Of the top 50 apps, 12 apps start in under or around 2 seconds, and 33 in
under 3 seconds.  [Z Speed+](XXX) app is the fastest with a 1.54 seconds
start time, which is (sort of) expected because this app's main function
is to boost phone performance. [Uber](XXX) is the slowest with 11.83
seconds start time -- that's **76%** slower than Skype, the slowest of the
top 25.  Based on [our fine-grained performance analysis of Uber](XXX), it
spends majority of the startup time acquiring accurate GPS coordinates
(XXX double check).

Of the top 100 apps, 20 apps start in under or around 2 seconds, and 60 in
under 3 seconds. [Vine] is the fastest with a 1.18 seconds start time.
[Waze](XXX) overtakes Uber to be the slowest, with a 12.49 seconds startup
time for the same reason of acquiring accurate GPS coordinates (XXX double
check).

Across the three groups of apps, there's also an interesting pattern.
Most of these apps starts fast (20% starts under or around 2 seconds, and
60\% 3 seconds) which is not surprising because these are really the most
popular apps.  However, some slow apps are very slow.

<br>

***
<br>

<a name="categories">


##Categorical Breakdown

We've also compared the top apps that fall into the same category and
compiled the data into the following graph:

<div style="margin-left:14%; margin-bottom:10px"> Show me the top

<select ONCHANGE="changeCat(this)" class="custom-select" id="select-cat-data" style="margin-top: 5px; margin-left:0px">
<option value = "MUSIC_STREAMING">music streaming</option>
<option value = "MESSAGING">messaging</option>
<option value = "SHOPPING">shopping</option>
<option value = "SOCIAL">social media</option>
<option value = "VIDEO">streaming video</option>
<option value = "SPEED_BOOSTER">device optimization</option>
<option value = "PHOTO_EDITING">photo editing</option>
</select>

apps sorted by

<select ONCHANGE="toggleCheckboxCat(); sortCheckboxCat(this)" id="toggle-cat-sort" class="custom-select" style="float:none; margin-left:0; width:150px">
<option value = "rank">google play rank</option>
<option value = "time">cold start time</option>
</select>
</div>


<canvas id="cat" height="500px" width="500px" style="" onmouseover="this.style.cursor='pointer'"></canvas>




<label class="custom-checkbox" style="margin-left:2%; display:none"><input type="checkbox" onclick="sortCheckboxCat(this)" id="sort-by-time-cat"> Sort by time<label>





<br><br><br>

Among all music streaming apps, [NextRadio](XXX) starts the fastest, and
XXX and XXX are very close.  (XXX is the slowest.

XXX do the same for all other categories.


<!--- With this data, we see that two categories immediately stand out. Social Media apps, with the lowest median start time (2.48s) of the group, are significantly faster than Video Streaming apps, which have a median cold start time of 5.79s. It makes sense that video streaming apps have larger start times: big companies like Netflix and YouTube have a heap of resources to load on app startup to provide a smooth UX throughout the duration of a stream, especially if you consider the appreciable size of a video. Social categories (like Messaging and Social Media) had the lowest overall start times, which also makes sense: users want to be able to open, read, and respond to their friends' messages quickly. Responding to a message likely holds more urgency than playing a song or cleaning up your device via one of the speed boosters in the Device Optimization category.

Overall, these apps are quick. We cannot stress enough that this is an integral part of what makes them so successful. Good developers are constantly looking to reduce start time, and as a great developer, you should too.
--->

<a href="https://nimbledroid.com"><button class="call-to-action"> See how your app ranks now! </button></a>

<script>


window.onload = function(){
  var top25 = document.getElementById("top25").getContext("2d");

  window.myBar1 = new Chart(top25).HorizontalBarWithXLabel(top25data, {
    responsive : true
  });


  var cat = document.getElementById("cat").getContext("2d");

  window.myBar2 = new Chart(cat).BarWithLine(catData, {
    responsive : true,
    limitLines : [
      {label: "Average",
      value: getAvg(catData["datasets"][0]["data"]),
      color: "#cc0000"
      }
    ]

  });



}

top25.onclick = function(evt){
    var activeBars = window.myBar1.getBarsAtEvent(evt);
    var notFound = true;
    if (typeof(activeBars[0]) != 'undefined') {
      count = 0;
      packageName="";
      while (notFound) {
        if (all_data["all"][count]["name"] == activeBars[0]["label"]) {
          packageName = all_data["all"][count]["package"];
          notFound = false;
        }
        count++;
      }
      location.href='https://nimbledroid.com/play/'+packageName
    }
    else {
      // var ctx = document.getElementById("canvas").getContext("2d");
      // from the endPoint we get the end of the bars area
      var base = window.myBar1.scale.endPoint;
      var height = window.myBar1.chart.height;
      var width = window.myBar1.chart.width;
      console.log("height: " + height);
      console.log("width: " + width);
      // only call if event is under the xAxis
          // how many xLabels we have
          var count = window.myBar1.scale.valuesCount;
          var padding_left = window.myBar1.scale.xScalePaddingLeft;
          var padding_right = window.myBar1.scale.xScalePaddingRight;
          // calculate width for each label
          var ywidth = height/count - 25/count;

          // determine what label were clicked on AND PUT IT INTO bar_index
          var relativeY = evt.pageY - this.offsetTop
          relativeY = relativeY -11;
          console.log(relativeY/ywidth - .4);
          var bar_index = count - relativeY/ywidth - relativeY/evt.pageY;
          console.log("pageY: " + evt.pageY)
          console.log("ywidth: " + ywidth);
          console.log("relativeY: " + relativeY);
          console.log("bar index: " + bar_index);
          console.log("*****")
          // don't call for padding areas
          if(bar_index > 0 & bar_index < count){
              bar_index = parseInt(bar_index);
              // either get label from catData
              // or from current data
              var ret = [];
              for (var i = 0; i < window.myBar1.datasets[0].bars.length; i++) {
                  ret.push(window.myBar1.datasets[0].bars[i].label)
              };
              console.log("current data:" + ret[bar_index]);
              var count = 0;
              while (notFound) {
                if (all_data["all"][count]["name"] == ret[bar_index]) {
                  packageName = all_data["all"][count]["package"];
                  notFound = false;
                }
                count++;
              }
              location.href='https://play.google.com/store/apps/details?id='+packageName + "&hl=en";
              // based on the label you can call any function
          }

    }
    // => activeBars is an array of bars on the canvas that are at the same position as the click event.
};



cat.onclick = function(evt){
    var activeBars = window.myBar2.getBarsAtEvent(evt);
    var x;
    var y;
    x = evt.pageX;
    y = evt.pageY;
    console.log(x + ", " + y);
    console.log(typeof(activeBars[0]));
    var notFound = true;
    if (typeof(activeBars[0]) != 'undefined') {
      count = 0;
      packageName="";
      while (notFound) {
        if (cat_data["all"][count]["name"] == activeBars[0]["label"]) {
          packageName = cat_data["all"][count]["package"];
          notFound = false;
        }
        count++;
      }
      location.href='https://nimbledroid.com/play/'+packageName
    }
    else {
      // var ctx = document.getElementById("canvas").getContext("2d");
      // from the endPoint we get the end of the bars area
      var base = window.myBar2.scale.endPoint;
      var height = window.myBar2.chart.height;
      var width = window.myBar2.chart.width;
      // only call if event is under the xAxis
      if(evt.pageY > base){
          // how many xLabels we have
          var count = window.myBar2.scale.valuesCount;
          var padding_left = window.myBar2.scale.xScalePaddingLeft;
          var padding_right = window.myBar2.scale.xScalePaddingRight;
          // calculate width for each label
          var xwidth = (width-padding_left-padding_right)/count;
          // determine what label were clicked on AND PUT IT INTO bar_index
          var bar_index = (evt.offsetX - padding_left) / xwidth;
          // don't call for padding areas
          if(bar_index > 0 & bar_index < count){
              bar_index = parseInt(bar_index);
              // either get label from catData
              // or from current data
              var ret = [];
              for (var i = 0; i < window.myBar2.datasets[0].bars.length; i++) {
                  ret.push(window.myBar2.datasets[0].bars[i].label)
              };
              console.log("current data:" + ret[bar_index]);
              var count = 0;
              while (notFound) {
                if (cat_data["all"][count]["name"] == ret[bar_index]) {
                  packageName = cat_data["all"][count]["package"];
                  notFound = false;
                }
                count++;
              }
              location.href='https://play.google.com/store/apps/details?id='+packageName + "&hl=en";
              // based on the label you can call any function
          }
      }
    }
};




var top25data = {
    labels: [],
    datasets: [
        {
            label: "Cold Start Time (seconds)",
            fillColor: "#ff0000",
            strokeColor: "#ff0000",
            highlightFill: "#cc0000",
            highlightStroke: "#cc0000",
            data: []
        },
    ]
};





var catData = {
    labels: [],
    datasets: [
        {
            label: "Cold Start Time (Seconds)",
            fillColor: "#ff0000",
            strokeColor: "#ff0000",
            highlightFill: "#cc0000",
            highlightStroke: "#cc0000",
            data: []
        },
    ]
};

var dataToUse = all_data;

function getNData() {
  var n;
  if(window.location.href.indexOf("&category=") != -1) {
   n = window.location.href.substring(window.location.href.indexOf("top?=") + 5, window.location.href.indexOf("&category="));
  }
  else {
    n = window.location.href.substring(window.location.href.indexOf("top?=") + 5);
  }
  var masterChartData = [];
  for (i = 0; i < n; i++) {
    masterChartData.push(all_data["all"][i]);
  }
  if (document.getElementById("sort-by-time").checked) {
    masterChartData.sort(compareTime);
    masterChartData.reverse();
  }
  else {
    masterChartData = [];
    for (i = 0; i < n; i++) {
      masterChartData.push(all_data["all"][i]);
    }
  }
  for (i = 0; i < masterChartData.length; i++) {
    top25data["labels"].push(masterChartData[i]["name"]);
    top25data["datasets"][0]["data"].push(masterChartData[i]["startTime"]);
  }
  if (n <= 50) {
    document.getElementById('top25').style.width = '680px';
    document.getElementById('top25').style.height = '700px';
  }
  else {
    document.getElementById('top25').style.height = '1150px';
    document.getElementById('top25').style.width = '700px';
  }
  if (n == 25 || n == 50 || n == 100) {
    var dropDown = document.getElementById('select-all-data');
    dropDown.value = n;
  }
}

function toggleCheckbox() {
  var dropDown = document.getElementById("toggle-top-sort");
  if (dropDown.options[dropDown.selectedIndex].value == "time") {
    document.getElementById("sort-by-time").checked = true;
  }
  else {
    document.getElementById("sort-by-time").checked = false;
  }
}

function toggleCheckboxCat() {
  var dropDown = document.getElementById("toggle-cat-sort");
  if (dropDown.options[dropDown.selectedIndex].value == "time") {
    document.getElementById("sort-by-time-cat").checked = true;
  }
  else {
    document.getElementById("sort-by-time-cat").checked = false;
  }
}

function sortCheckbox(val) {
  var dropDown = document.getElementById("select-all-data");
  var dropDownVal = dropDown.options[dropDown.selectedIndex].value;
  changeDataNum(dropDown);
}



function sortCheckboxCat(val) {
  var dropDown = document.getElementById("select-cat-data");
  changeCat(dropDown);
}

function fetchDataByCat() {
  var catName;
  if(window.location.href.indexOf("#") != -1) {
    catName = window.location.href.substring(window.location.href.indexOf("&category=") + 10, window.location.href.indexOf("#"));
  }
  else {
    catName = window.location.href.substring(window.location.href.indexOf("&category=") + 10);
  }
  catData["labels"] = [];
  catData["datasets"][0]["data"] = [];
  var masterCatArr = [];
  for (i = 0; i < cat_data["all"].length; i++) {
    if (cat_data["all"][i]["category"] == catName) {
      masterCatArr.push(cat_data["all"][i]);
    }
  }
  if (document.getElementById("sort-by-time-cat").checked) {
    masterCatArr.sort(compareTime);
  }
  else {
    masterCatArr = [];
    for (i = 0; i < cat_data["all"].length; i++) {
      if (cat_data["all"][i]["category"] == catName) {
        masterCatArr.push(cat_data["all"][i]);
      }
    }
  }
  for (i = 0; i < masterCatArr.length; i++) {
    catData["labels"].push(masterCatArr[i]["name"]);
    catData["datasets"][0]["data"].push(masterCatArr[i]["startTime"]);
  }
  var dropDown = document.getElementById("select-cat-data");
  dropDown.value= catName;
}

function sortByTime(time1, time2) {
  return time1 - time2;
}

function getAvg(arr) {
  var sum =  arr.reduce(function (p, c) {
    return (p + c);
  });
  return (sum/arr.length).toPrecision(3);
}

function getMedian(arr) {
  sortedArr = arr.slice(0);
  sortedArr = sortedArr.sort(sortByTime);
  if (sortedArr.length % 2 == 0) {
    return ((sortedArr[sortedArr.length/2] + sortedArr[sortedArr.length/2 + 1])/2).toPrecision(3)
  }
  return sortedArr[Math.floor(sortedArr.length/2)];
}

function getMax(arr) {
  sortedArr = arr.slice(0);
  sortedArr = sortedArr.sort(sortByTime);
  return sortedArr[sortedArr.length - 1];
}

function getMin(arr) {
  sortedArr = arr.slice(0);
  sortedArr = sortedArr.sort(sortByTime);
  return sortedArr[0];
}

function changeCat(filter) {
  myBar2.destroy();
  var anchor = "";
  var numTop = window.location.href.substring(window.location.href.indexOf("top?=") + 5, window.location.href.indexOf("&category="));
  if(window.location.href.indexOf("#") != -1) {
    anchor = window.location.href.substring(window.location.href.indexOf("#"));
  }
  window.history.replaceState("","", "{{ page.url }}" + "?top?=" + numTop +"&category="+filter.value + anchor);
  fetchDataByCat();
  myBar2.destroy();
  cat = document.getElementById("cat").getContext("2d");
  window.myBar2 = new Chart(cat).BarWithLine(catData, {
    datasetStroke : false,
    limitLines: [
       {
           label: 'Average',
           value: getAvg(catData["datasets"][0]["data"]),
           color: '#cc0000'
       },
   ],
  });
}


function changeDataNum(filter) {
  window.history.replaceState("","", "{{ page.url }}" + "?top?=" + filter.value+ window.location.href.substring(window.location.href.indexOf("&category=")));
  myBar1.destroy();
  top25data["labels"] = [];
  top25data["datasets"][0]["data"] = [];
  getNData();
  top25 = document.getElementById("top25").getContext("2d");
  window.myBar1 = new Chart(top25).HorizontalBarWithXLabel(top25data, {
    datasetStroke : false,
    });
}

//initialize chart data
if(window.location.href.indexOf("top?=") == -1 || window.location.href.indexOf("&category=") == -1) {
  window.history.replaceState("","", "{{ page.url }}" + "?top?=25&category=MUSIC_STREAMING");
}
getNData();
fetchDataByCat();
</script>

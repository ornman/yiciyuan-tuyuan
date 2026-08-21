# 异次元图源 清洗与体检报告

## 结论
- 原始 10 个图源文件合计 **1157 条**，按 bookSourceUrl 去重后 **233 个唯一源**
- 最终交付 **185 个**(yiciyuan_clean.json)，删除 **48 个**：DNS死21 + 旧文件不可达22 + 动态JS废源5
- 分层：网络层指纹敏感待实测 42 / 引擎全通 4 / 规则需真机评估 41 / 其他 1 / 搜索可用 15 / 本环境无静态内容(反爬/失效) 70 / 被IP屏蔽待家用实测 12

## 检测方法(4层)
1. DNS/域名存活(阿里公共DNS NXDOMAIN=域名注销)
2. 网络层: OpenSSL原始socket探测(80/443双端口, 比curl准——curl误报后可用数123→178)
3. L3速度与内容: 双采样200/TTFB/内容32KB上限
4. L4引擎级: 按异次元4次请求流(搜索→详情→目录→正文)带源UA/Referer实跑, 校验各步非空

## T1_引擎全通 (4)
- ◯ 包子漫画 | https://cn.bzmanga.com | 状态OK 目录1211章 正文6图
- ☄️ 野蛮漫画 | http://yemancomic.com | 状态OK 目录395章 正文209图
- ◯ YYDS | http://www.yydsmh.com | 状态OK 目录395章 正文209图
- ◯ 包子漫画web | https://cn.baozimhcn.com | 状态OK 目录1211章 正文6图

## T2_搜索可用 (15)
- 顶漫画 | https://www.dingmanhua.com | 搜索出 4 条
- 波洞 | https://ymcdnyfqdapp.ikmmh.com | 搜索出 15 条
- 腾讯漫画 | https://m.ac.qq.com | 搜索出 10 条
- 包子漫画cn | https://cn.czmanga.com | 搜索出 83 条
- 特漫网 | https://www.44te.com | 搜索出 1 条
- 动漫啦 | http://www.dongman.la | 搜索出 13 条
- 漫客栈w | https://www.mkzhan.com | 搜索出 12 条
- 聚合漫画屋 | https://www.52hah.com | 搜索出 11 条
- GMANHUA | http://www.gmanhua.com | 搜索出 20 条
- 国漫网 | https://www.guomanwang.com | 搜索出 4 条
- 包子漫画cw | https://cn.webmota.com | 搜索出 83 条
- 爱优漫🅰 | https://getconfig-globalapi.yyhao.com:443 | 搜索出 1 条
- 绝对领域🅿 | http://www.jdlingyu.com | 搜索出 20 条
- 特漫网 | https://www.78te.com | 搜索出 1 条
- 包子漫画₂ | https://www.baozimh.com | 搜索出 85 条

## T3_网络层指纹敏感待实测 (42)
- ◯ 拷贝漫画 | https://api.mangacopy.com
- 新新漫画₂ | https://www.77mh.xyz
- 漫画DB | https://www.manhuadb.com
- 漫画160 | https://m.mh160.cc
- 果果漫画 | https://m.guoguomh.com
- 来漫画 | https://www.laimanhua8.com
- 动漫之家v3 | https://v3api.dmzj.com
- 动漫之家M₂ | https://api.m.idmzj.com
- 动漫之家M₁ | https://m.dmzj.com
- 滴答漫画-M | https://www.didamh.com
- 动漫之家m | https://manhua.dmzj.com
- 动漫之家s₂🅰 | https://sacg.dmzj.com
- Komiic漫画 | https://komiic.com
- 漫画1234 | https://m.gmh1234.com
- 动漫之家m | https://manhua.idmzj.com
- 萌图社🅿 | https://moetu.club
- 动漫之家M₂📱 | https://m.dmzj.com/info
- 动漫之家M₃📱 | https://m.dmzj.com/search
- 动漫之家s₃🅰 | https://sacg.dmzj.com/mh
- 动漫之家v1🅰 | http://api.dmzj.com
- 动漫之家₂📱 | https://m.idmzj.com
- 最漫画📱🍙 | https://m.zuimh.com
- 夜色漫画📱 | https://www.yeseimg.com
- 🔥亲亲漫画 | http://api.acg.gd
- 冰氪漫画📱 | https://m.icekr.com
- 艾米漫画 | https://www.aimimh.com
- 漫外音 | http://m.manwaiyin.com
- 漫画楼 | https://www.manhualou.com
- 九妖漫画👙 | https://jymh07.com
- Go追漫 | https://mh.9xxsm.com
- 包子漫画₁ | https://cn.baozimh.com
- 依依漫画📱 | https://m.yiyimanhua.com
- 鸟鸟韩漫 | https://nnhanman.net
- 鸟鸟韩漫 | https://nnhanman.xyz
- SVIP漫画💡 | https://www.404mh.com
- 梦游漫画📱🌐 | https://www.mymhh.com
- KuKu动漫📱 | https://wap.kukudm.com
- 非常爱漫📱 | http://m.veryim.com
- 九妖漫画👙 | https://mobile.jymhapp.com
- 果果漫画 | https://www.guoguom.com
- 522漫画📱 | http://m.522manhua.com
- 丽图漫画 | https://litu100.xyz

## T3_规则需真机评估 (41)
- ◯ G站 | https://m.g-mh.org | RULE_MISMATCH
- naver | https://m.comic.naver.com/index.nhn | NO_KEY
- 崩坏3漫画 | https://comic.bh3.com | NO_KEY
- 咚漫 | https://www.dongmanmanhua.cn | JS_RULE
- 动漫戏说 | https://comic.acgn.cc | NO_KEY
- 极速漫画💰 | http://www.1kkk.com | RULE_MISMATCH
- 漫画屋 | https://www.mhua5.com | RULE_MISMATCH
- 风之动漫 | https://manhua.fffdm.com | NO_KEY
- 动漫星空 | http://acg.gamersky.com/manhua | RULE_MISMATCH
- 爱奇艺漫画 | https://www.iqiyi.com/manhua | RULE_MISMATCH
- 漫本 | http://www.manben.com | JS_RULE
- 咚漫-M | https://m.dongmanmanhua.cn | JS_RULE
- 非常爱漫 | http://wap.veryim.com | RULE_MISMATCH
- 知音漫客-M | https://m.zymk.cn | RULE_MISMATCH
- 日漫之家 | https://rimanzhijia.com | RULE_MISMATCH
- 奇漫屋₁ | http://m.qmanwu2.com | JS_RULE
- biliplus | https://www.biliplus.com/manga | NO_KEY
- 龙王传说网 | https://lw.131453.xyz | NO_KEY
- Webtoon_us | https://us.webtoons.com | JS_RULE
- webtoon移动版 | https://us-m.webtoons.com | JS_RULE
- MangaRead | https://www.mangaread.org | RULE_MISMATCH
- 小鸟壁纸🅿💡 | http://wallpaper.apc.360.cn | NO_KEY
- 堆糖-发现搜索可用₂🅿 | https://www.duitang.com | JS_RULE
- 漫画123📱💡 | https://m.manhua123.net | RULE_MISMATCH
- 哔哩相簿🅿❕💡 | https://h.bilibili.com | NO_KEY
- Cosplay啦🅿❕ | http://ciyuandao.com/photo | NO_KEY
- 360壁纸🅿💡 | http://wallpaper.apc.360.cn/index.php | NO_KEY
- 安卓壁纸🅿💡 | http://service.picasso.adesk.com | NO_KEY
- 拷贝漫画 | https://www.mangacopy.com | NO_KEY
- 唯一图库🅿❕ | http://www.mmonly.cc/tag/bs1 | NO_KEY
- 爱看漫画网🔞 | https://jjmhw.cc | RULE_MISMATCH
- 猎奇漫画™❕ 🇰🇷 | https://www.lieqiman.com | NO_KEY
- ACG456-M | http://m.acg456.com | RULE_MISMATCH
- 汉化吧 | http://www.hanhuaba.com | RULE_MISMATCH
- 龙王传说网❕ | https://www.longwangchuanshuo.com | NO_KEY
- 仙漫网💡 | https://www.xianman123.com | RULE_MISMATCH
- 久久漫画网 | http://www.mxshm.top | RULE_MISMATCH
- 漫画皮 | https://m.iimanhuapi.com | RULE_MISMATCH
- 漫小肆韓漫 | https://www.mxs13.cc | RULE_MISMATCH
- 非常爱漫 | http://app.veryim.com | RULE_MISMATCH
- 糖心漫画💡💰 | http://tangxin666.com | RULE_MISMATCH

## T3_其他 (1)
- 再漫画 | https://v4api.zaimanhua.com | OK

## T4_本环境无静态内容(反爬/失效) (70)
- 鬼罗丽漫画 | http://m.ymgjmh.com | HTTP416
- 二次元动漫 | http://www.2animx.com | HTTP403
- SF漫画 | https://mm.sfacg.com | SHELL
- 仙漫网-M | https://m.gaonaojin.com | SHELL
- MangaHasu | http://mangahasu.se | SHELL
- 90漫画 | http://www.90mh.org | SHELL
- 山立漫画 | https://www.setnmh.com | HTTP403
- 90漫画-M | http://m.90mh.org | SHELL
- 梦游漫画 | https://www.mumumh.com | HTTP404
- 漫画人 | http://www.manhuaren.com | HTTP200
- 漫漫漫画-M | https://m.manmanapp.com | HTTP404
- Klmanga | https://klmanga.com | SHELL
- 古风漫画-M | https://m.gufengmh9.com | SHELL
- 韩漫窝 | http://www.hanmanwo.com | HTTP403
- 动漫屋 | https://m.dm5.com | HTTP200
- 韩国漫画网 | https://www.roumh.com | HTTP403
- 漫漫漫画 | https://www.manmanapp.com | HTTP404
- kuku动漫 | http://wap.ikukudm.com | SHELL
- 新漫画-A | https://xapi.xinmanhua.net | HTTP404
- 漫畫狗 | https://dogemanga.com | HTTP400
- 咪咕动漫 | http://m.migudm.cn | SHELL
- 漫画皮 | https://www.manhuapi.com | SHELL
- 一本漫画-A | https://www.yibenmanhua.com | HTTP403
- 漫画台-M | https://m.manhuatai.com | EMPTY
- 看漫画-M | https://m.kanman.com | EMPTY
- 仙漫网 | https://www.gaonaojin.com | SHELL
- 古风漫画 | https://www.gufengmh9.com | SHELL
- 92漫画-M | http://m.92mh.com | SHELL
- 92漫画 | http://www.92mh.com | HTTP403
- 动漫狂 | https://www.cartoonmad.com | SHELL
- 漫客栈-A | http://comic.mkzhan.com | EMPTY
- 無限動漫 | https://www.8comic.com | HTTP403
- 神漫画-M | https://m.taomanhua.com | EMPTY
- 肉漫画网 | https://m.roumh.com | HTTP403
- ACG漫画网 | https://www.acgomh.com | SHELL
- 如漫画 | https://rumanhua.com | HTTP404
- 好国漫 | https://m.haoguoman.net | HTTP403
- 搜动漫📱 | http://m.soudongman.com | HTTP403
- 爱飒漫画📱 | https://m.isamanhua.com | EMPTY
- 爱优漫📱 | https://m.iyouman.com | EMPTY
- 动漫之家v3🅰 | http://v3api.idmzj.com | HTTP404
- 快看漫画📱💰 | http://m.kuaikanmanhua.com | EMPTY
- 神漫画 | https://www.taomanhua.com | EMPTY
- 漫画台™🅰 | http://getcomicinfo-globalapi.yyhao.com | EMPTY
- 大魔兔 | http://www.damotu.com | HTTP200
- 漫画台🅰 | https://getconfig-globalapi.yyhao.com | EMPTY
- 漫画哥📱 | https://m.manhuag.com | SHELL
- 有动漫 | https://www.udm123.com | SHELL
- 快看漫画💰 | https://www.kuaikanmanhua.com | EMPTY
- 动漫之家s₁🅰 | http://sacg.idmzj.com | HTTP404
- 漫画1234 | https://www.ymh1234.com | HTTP530
- G站漫画 | https://www.godamanga.com | HTTP404
- 漫画看 | https://www.mhkan.com | HTTP404
- 飞雪漫画🇰🇷 | https://www.feixuemh.com | SHELL
- 波乐漫画📱🇰🇷 | https://m.bolemanhua.com | SHELL
- 国漫吧 | http://www.guoman8.cc | HTTP403
- 国漫吧 | http://www.guomanba.cc | SHELL
- 黑白漫话📱 | http://m.heibaimanhua.com | HTTP404
- 98漫画网 | https://www.98comic.com | SHELL
- MangaPark🇬🇧 | https://mangapark.org | HTTP403
- 酷爱漫画💡💰 | https://www.kuimh.com | SHELL
- 鸟鸟韩漫 | https://nnhm7.xyz | HTTP404
- 大古漫画-M | https://www.dgmh123.com | SHELL
- vomic漫画-M | http://www.vomicmh.com | HTTP567
- vomic漫画🅰 | http://www.iewoai.com | HTTP567
- 漫画台₂ | http://manhuatai.org | HTTP404
- 8comic🅰💡 | https://m.comicbus.com | HTTP403
- 八极漫画 | http://www.8jj.com | HTTP404
- MangaSum🇬🇧 | https://mangasum.com | SHELL
- TVBS漫画💡 | https://www.tvbsmh.com | HTTP403

## T5_被IP屏蔽待家用实测 (12)
- ☄️ 最次元 | http://www.zcymh.com
- x漫画-M | https://www.xmanhua.com
- x漫画 | https://xmanhua.com
- 漫畫櫃 | https://tw.manhuagui.com
- 新新漫画₁ | https://www.77mh.nl
- 看漫畫 | https://www.k886.net
- 漫画柜 | https://www.manhuagui.com
- Mangabz | https://mangabz.com
- 读漫屋 | https://dumanwu.com
- 拷贝漫画💎 | https://copymanga.site
- 风车漫画 | https://m.qyy158.com
- 如漫画 | http://rumanhua1.com

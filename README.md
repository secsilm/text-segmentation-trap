# Text Segmentation Trap

这里会罗列一些容易被分词工具被分错的句子，详细的测试代码见 [notebook](https://github.com/secsilm/text-segmentation-trap/blob/master/segmentation-test.ipynb)，可以通过 `CTRL` + `F` 来快速查找想要的句子。

> 注：`来源` 列中的 `聊天` 指的是该句来源于日常聊天，包括口头聊天和微信等社交软件聊天记录等。

| 序号| 句子| 来源 |Stanford NLP|Jieba|备注|
| :---: | ---|---|---|---|---|
| 1| 【学术造假爆发】全球40万科学家在假期刊发论文，包括一位诺奖得主！| [【学术造假爆发】全球40万科学家在假期刊发论文，包括一位诺奖得主！](https://mp.weixin.qq.com/s/bu14L15wrBHZ32FNO6sWmA)|【/学术/造假/爆发/】/全球/40万/科学家/在/假期/刊发/论文/，/包括/一/位/诺奖/得主/！|【/学术/造假/爆发/】/全球/40/万/科学家/在/假期/刊发/论文/，/包括/一位/诺/奖得主/！|
| 2| 只有这时候人才是最齐的| 聊天|只有/这时候/人才/是/最/齐/的|只有/这时候/人才/是/最齐/的|
|3|光绪辞世时尚没有陵墓，一直到1913年（民国二年）才葬入中国最后一座帝陵——河北易县清西陵中的崇陵。|[光绪帝 - 维基百科，自由的百科全书](https://zh.wikipedia.org/wiki/%E5%85%89%E7%BB%AA%E5%B8%9D)|光绪/辞世/时尚/没有/陵墓/，/一直/到/1913/年/（/民国/二年/）/才/葬入/中国/最后/一/座/帝陵/——/河北/易县/清/西陵/中/的/崇陵/。|光绪/辞世/时尚/没有/陵墓/，/一直/到/1913/年/（/民国/二年/）/才葬入/中国/最后/一座/帝陵/—/—/河北/易县/清西陵/中/的/崇陵/。|
|4|所以福建人生的反义词是煮。|[无情广东人🤔🤔🤔 - 即刻网页版](http://web.okjike.com/message-detail/5ba1fa508a21ce009370a188/officialMessage)|所以/福建/人生/的/反义词/是/煮/。|所以/福建/人生/的/反义词/是/煮/。|
|5|小米8旗舰系列发货超600万台，米家自动洗手机套装众筹开启|[小米8旗舰系列发货超600万台，米家自动洗手机套装众筹开启](https://mp.weixin.qq.com/s/LHpx21OyJVySlIC9M65a7A)|小/米/8/旗舰/系列/发货/超/600万/台/，/米/家/自动/洗/手机/套装/众/筹/开启|小米/8/旗舰/系列/发货/超/600/万台/，/米家/自动/洗/手机/套装/众筹/开启|可以看到 Stanford NLP 没有将很常见的「小米」分出来，但是如果单独把「小米」或者「小米8」拿出来分的话是可以正确分出「小米」的，但是如果把「小米8旗舰」拿出来分的话就又变成「小 米」了，而 Jieba 则一直保持不变。根据 Stanford NLP [官方的网站的说明](https://nlp.stanford.edu/projects/chinese-nlp.shtml#cws)，其中文分词使用的是 CRF 方法，也结合了词典和 n-grams 等特征；而根据 Jieba 的[说明](https://github.com/fxsjy/jieba#%E7%AE%97%E6%B3%95)，使用的是基于前缀词典实现高效的词图扫描方法和基于动态规划的方法，未登录词使用的是 HMM 模型|
|6|据说她们平时的歌声音质不错，但如果是丧事来临，她们的嗓音就会瞬间尖锐到可以震碎玻璃。|[【玩家分享】万圣节角色原型个人考据](https://mp.weixin.qq.com/s/LYjrfDOEn7CY2JlD__mvuw)|据说/她们/平时/的/歌声/音质/不错/，/但如/果是/丧事/来临/，/她们/的/嗓音/就/会/瞬间/尖锐/到/可以/震/碎玻璃/。|据说/她们/平时/的/歌声/音质/不错/，/但/如果/是/丧事/来临/，/她们/的/嗓音/就/会/瞬间/尖锐/到/可以/震/碎玻璃/。|两者「歌声」和「音质」还是正确地分开了， 但是「震碎玻璃」却没有被正确分开。而且 Stanford NLP 没有将很常见的「但如果是」正确分开|
|7|烧脑残局，火热上线|《欢乐斗地主》广告|烧/脑/残局/，/火热/上线|烧脑/残局/，/火热/上线||
|8|丧幼子，入佛门。笔下江湖，快意恩仇。经历过非常人之痛，书写着世人心中江湖。|微信朋友圈|丧幼子/，/入/佛门/。/笔下/江湖/，/快意/恩仇/。/经历/过/非常/人/之痛/，/书写/着/世人/心/中/江湖/。|丧/幼子/，/入/佛门/。/笔下/江湖/，/快意/恩仇/。/经历/过/非常/人之痛/，/书写/着/世人/心中/江湖/。|这是金庸逝世当天（2018 年 10 月 30 日）我在微信朋友圈看到朋友发的文字。|
|9|要求家具改成龙头，结果收到成龙头|[论断句的重要性 ——dryadb43738 - 即刻App](https://m.okjike.com/officialMessages/5be25e4e83101200923af414?username=31a05283-aaf9-4e32-86df-86e95cef344e&utm_source=wechat_session&share_distinct_id=166528654f5fc0-085d3064ac62f-8383268-2073600-166528654f69ac&share_depth=1)|要求/家具/改成/龙头/，/结果/收到/成/龙头|要求/家具/改成/龙头/，/结果/收到/成/龙头|句子稍有改动，原句为繁体的「要求家具改成龙头，结果收到“成龙”头」|
|10|我也想过过儿过过的生活|[论断句的重要性 - 微博HTML5版](https://m.weibo.cn/detail/4303684843783227)|我/也/想/过过儿/过过/的/生活|我/也/想/过/过儿/过过/的/生活||
|11|下周日你有空吗？|[论断句的重要性 ——dryadb43738 - 即刻App](https://m.okjike.com/officialMessages/5be25e4e83101200923af414?username=31a05283-aaf9-4e32-86df-86e95cef344e&utm_source=comment_card)|下/周日/你/有空/吗/？|下/周日/你/有空/吗/？||
|12|【泪目！解放军战士手牵手趟过中越边境雷场，将安全的土地移交百姓】11月16日，中越边境云南段已扫雷场移交仪式在云南省麻栗坡县猛硐乡老山西侧雷场举行。移交现场，扫雷官兵当着老百姓的面，手牵手趟过雷场，用这种特殊的方式向老百姓说明脚下的每一寸土地都是安全的。致敬！|[新浪军事-微博](https://m.weibo.cn/detail/4308039014228339)|【/泪目/！/解放军/战士/手牵手/趟/过/中越/边境/雷场/，/将/安全/的/土地/移交/百姓/】/11月/16日/，/中/越/边境/云南/段/已/扫雷/场/移交/仪式/在/云南省/麻栗坡县/猛硐/乡老/山西/侧/雷场/举行/。/移交/现场/，/扫雷/官兵/当着/老百姓/的/面/，/手/牵/手/趟/过/雷场/，/用/这/种/特殊/的/方式/向/老百姓/说明/脚下/的/每/一/寸/土地/都/是/安全/的/。/致敬/！|【/泪目/！/解放军/战士/手牵手/趟/过/中越/边境/雷场/，/将/安全/的/土地/移交/百姓/】/11/月/16/日/，/中/越/边境/云南/段/已/扫雷/场/移交/仪式/在/云南省/麻栗坡县/猛/硐/乡/老山/西侧/雷场/举行/。/移交/现场/，/扫雷/官兵/当着/老百姓/的/面/，/手牵手/趟/过/雷场/，/用/这种/特殊/的/方式/向/老百姓/说明/脚下/的/每一寸/土地/都/是/安全/的/。/致敬/！||
|13|笔记本身为X86平台最能带货的品类，Intel和AMD绝不会忽略掉，所以也照例推出了几款KabyLake-G处理器。|[聊聊Intel和AMD的新婚生活 - 笔吧评测室](https://mp.weixin.qq.com/s/kQ_4_3oGm2419xx0wMcauA)|笔记本/身为/X86/平台/最/能/带货/的/品类/，/Intel/和/AMD/绝不/会/忽略/掉/，/所以/也/照例/推出/了/几/款/KabyLake-G/处理器/。|笔记本/身为/X86/平台/最/能带/货/的/品类/，/Intel/和/AMD/绝不会/忽略/掉/，/所以/也/照例/推出/了/几款/KabyLake/-/G/处理器/。|在此例中，Jieba 对特殊名词的识别不太准，例如 KabyLake-G|
|14|人要是行，干一行行一行，一行行行行行；人要是不行，干一行不行一行，一行不行行行不行|[汉语将加入俄罗斯“高考” 看到题目笑出了声！网友：内容引起舒适 - TechWeb](https://mp.weixin.qq.com/s/pES7Z1GfhqyJuMkBcRbLPQ)|人/要是/行/，/干/一行行/一行/，/一行行/行行行/；/人/要是/不行/，/干/一/行/不/行/一行/，/一/行/不/行/行行/不行|人/要是/行/，/干/一行行/一行/，/一行行/行行行/；/人/要是/不行/，/干一行/不行/一行/，/一行/不行/行/行不行||
|15|另外米家台灯 Pro 采用了 DC 调光，无可视频闪，「护眼神教」的教徒们应该心里有数。|[米家又带来了三款新品，有升级版的台灯和耳机-爱范儿](https://www.ifanr.com/1159393)|另外/米/家/台灯/Pro/采用/了/DC/调光/，/无可/视频/闪/，/「/护眼/神教/」/的/教徒们/应该/心里有数/。|另外/米家/台灯/ /Pro/ /采用/了/ /DC/ /调光/，/无可/视频/闪/，/「/护/眼神/教/」/的/教徒/们/应该/心里有数/。||
|16|便宜实惠，方便，快速，日常生活用的东西在京东买比较好，京东方便了生活。看了下实物，质量和超市一样，京东的方便又值，赞。|情感分析数据集|便宜/实惠/，/方便/，/快速/，/日常/生活/用的/东西/在/京东/买/比较/好/，/京东/方便/了/生活/。/看/了/下/实物/，/质量/和/超市/一样/，/京东/的/方便/又/值/，/赞/。|便宜/实惠/，/方便/，/快速/，/日常生活/用/的/东西/在/京东/买/比较/好/，/京东方/便/了/生活/。/看/了/下/实物/，/质量/和/超市/一样/，/京东/的/方便/又值/，/赞/。||
|17|近日本省部分地区即将出现连降暴雪，气温将持续下降，有可能出现百年未遇的低温寒潮和雪灾。|电影[《暴雪将至》](https://movie.douban.com/subject/26775933/)台词|近日/本省/部分/地区/即将/出现/连降/暴雪/，/气温/将/持续/下降/，/有可能/出现/百/年/未/遇/的/低温/寒潮/和/雪灾/。|近日/本省/部分/地区/即将/出现/连降/暴雪/，/气温/将/持续/下降/，/有/可能/出现/百年/未遇/的/低温/寒潮/和/雪灾/。||
|18|在大年三十晚上，如果用户通过中央广播电视总台4K超高清频道（CCTV-4K）收看春晚节目，配置4K超高清图像+5.1环绕声，就能带来更高清晰度、更宽色域、更高动态范围视频和环绕声音频体验，在家就可以享受到影院的视听效果。|[期待！2019年春晚将成为科技盛宴：5G、4K都安排上了 - TechWeb](https://mp.weixin.qq.com/s/1NiugpTW8na-WYVyUsIYEQ)|在/大年三十/晚上/，/如果/用户/通过/中央/广播/电视/总台/4K/超高清/频道/（/CCTV-4K/）/收看/春晚/节目/，/配置/4K/超高清/图像/+/5.1/环绕/声/，/就/能/带来/更高/清晰度/、/更宽/色域/、/更/高/动态/范围/视频/和/环绕/声/音频/体验/，/在家/就/可以/享受/到/影院/的/视听/效果/。|在/大年三十/晚上/，/如果/用户/通过/中央/广播电视/总台/4K/超高/清/频道/（/CCTV/-/4K/）/收看/春晚/节目/，/配置/4K/超高/清/图像/+/5.1/环绕声/，/就/能/带来/更/高清晰度/、/更/宽色域/、/更高/动态/范围/视频/和/环绕声/音频/体验/，/在家/就/可以/享受/到/影院/的/视听/效果/。|本来想看看会不会掉进「环绕声音频体验」这个坑，结果都没掉进去，反倒是Stanford NLP 在「超高清」、「CCTV-4K」这些词上表现较好，整体上来看优于 Jieba|
|19|有个人开发者吗，想投资一些项目|[有个人开发者吗，想投资一些项目 - V2EX](https://www.v2ex.com/t/543062)|有/个人/开发者/吗/，/想/投资/一些/项目|有/个人/开发者/吗/，/想/投资/一些/项目||
|20|8月9日上午，辉县市委书记郭书佩带领市第一观摩组到城关镇开展重点工作集中观摩活动|微信公众号|8/月/9/日/上午/，/辉县/市委书记/郭书佩/带领/市/第一/观摩/组到/城关镇/开展/重点/工作/集中/观摩/活动|8月/9日/上午/，/辉县/市委/书记/郭书佩/带领/市/第一/观摩/组到/城关镇/开展/重点/工作/集中/观摩/活动||

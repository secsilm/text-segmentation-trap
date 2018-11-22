# Text Segmentation Trap

这里会罗列一些容易被分词工具被分错的句子，详细的测试代码见 [notebook](https://github.com/secsilm/text-segmentation-trap/blob/master/segmentation-test.ipynb)，可以通过 `CTRL` + `F` 来快速查找想要的句子。

> 注：`来源` 列中的 `聊天` 指的是该句来源于日常聊天，包括口头聊天和微信等社交软件聊天记录等。

| 序号| 句子| 来源 |Stanford NLP|Jieba|备注|
| :---: | ---|---|---|---|---|
| 1| 【学术造假爆发】全球40万科学家在假期刊发论文，包括一位诺奖得主！| [【学术造假爆发】全球40万科学家在假期刊发论文，包括一位诺奖得主！](https://mp.weixin.qq.com/s/bu14L15wrBHZ32FNO6sWmA)|【 学术 造假 爆发 】 全球 40万 科学家 在 假期 刊发 论文 ， 包括 一 位 诺奖 得主 ！|【 学术 造假 爆发 】 全球 40 万 科学家 在 假期 刊发 论文 ， 包括 一位 诺 奖得主 ！|
| 2| 只有这时候人才是最齐的| 聊天|只有 这时候 人才 是 最 齐 的|只有 这时候 人才 是 最齐 的|
|3|光绪辞世时尚没有陵墓，一直到1913年（民国二年）才葬入中国最后一座帝陵——河北易县清西陵中的崇陵。|[光绪帝 - 维基百科，自由的百科全书](https://zh.wikipedia.org/wiki/%E5%85%89%E7%BB%AA%E5%B8%9D)|光绪 辞世 时尚 没有 陵墓 ， 一直 到 1913 年 （ 民国 二年 ） 才 葬入 中国 最后 一 座 帝陵 —— 河北 易县 清 西陵 中 的 崇陵 。|光绪 辞世 时尚 没有 陵墓 ， 一直 到 1913 年 （ 民国 二年 ） 才葬入 中国 最后 一座 帝陵 — — 河北 易县 清西陵 中 的 崇陵 。|
|4|所以福建人生的反义词是煮。|[无情广东人🤔🤔🤔 - 即刻网页版](http://web.okjike.com/message-detail/5ba1fa508a21ce009370a188/officialMessage)|所以 福建 人生 的 反义词 是 煮 。|所以 福建 人生 的 反义词 是 煮 。|
|5|小米8旗舰系列发货超600万台，米家自动洗手机套装众筹开启|[小米8旗舰系列发货超600万台，米家自动洗手机套装众筹开启](https://mp.weixin.qq.com/s/LHpx21OyJVySlIC9M65a7A)|小 米 8 旗舰 系列 发货 超 600万 台 ， 米 家 自动 洗 手机 套装 众 筹 开启|小米 8 旗舰 系列 发货 超 600 万台 ， 米家 自动 洗 手机 套装 众筹 开启|可以看到 Stanford NLP 没有将很常见的「小米」分出来，但是如果单独把「小米」或者「小米8」拿出来分的话是可以正确分出「小米」的，但是如果把「小米8旗舰」拿出来分的话就又变成「小 米」了，而 Jieba 则一直保持不变。根据 Stanford NLP [官方的网站的说明](https://nlp.stanford.edu/projects/chinese-nlp.shtml#cws)，其中文分词使用的是 CRF 方法，也结合了词典和 n-grams 等特征；而根据 Jieba 的[说明](https://github.com/fxsjy/jieba#%E7%AE%97%E6%B3%95)，使用的是基于前缀词典实现高效的词图扫描方法和基于动态规划的方法，未登录词使用的是 HMM 模型|
|6|据说她们平时的歌声音质不错，但如果是丧事来临，她们的嗓音就会瞬间尖锐到可以震碎玻璃。|[【玩家分享】万圣节角色原型个人考据](https://mp.weixin.qq.com/s/LYjrfDOEn7CY2JlD__mvuw)|据说 她们 平时 的 歌声 音质 不错 ， 但如 果是 丧事 来临 ， 她们 的 嗓音 就 会 瞬间 尖锐 到 可以 震 碎玻璃 。|据说 她们 平时 的 歌声 音质 不错 ， 但 如果 是 丧事 来临 ， 她们 的 嗓音 就 会 瞬间 尖锐 到 可以 震 碎玻璃 。|两者「歌声」和「音质」还是正确地分开了， 但是「震碎玻璃」却没有被正确分开。而且 Stanford NLP 没有将很常见的「但如果是」正确分开|
|7|烧脑残局，火热上线|《欢乐斗地主》广告|烧 脑 残局 ， 火热 上线|烧脑 残局 ， 火热 上线||
|8|丧幼子，入佛门。笔下江湖，快意恩仇。经历过非常人之痛，书写着世人心中江湖。|微信朋友圈|丧幼子 ， 入 佛门 。 笔下 江湖 ， 快意 恩仇 。 经历 过 非常 人 之痛 ， 书写 着 世人 心 中 江湖 。|丧 幼子 ， 入 佛门 。 笔下 江湖 ， 快意 恩仇 。 经历 过 非常 人之痛 ， 书写 着 世人 心中 江湖 。|这是金庸逝世当天（2018 年 10 月 30 日）我在微信朋友圈看到朋友发的文字。|
|9|要求家具改成龙头，结果收到成龙头|[论断句的重要性 ——dryadb43738 - 即刻App](https://m.okjike.com/officialMessages/5be25e4e83101200923af414?username=31a05283-aaf9-4e32-86df-86e95cef344e&utm_source=wechat_session&share_distinct_id=166528654f5fc0-085d3064ac62f-8383268-2073600-166528654f69ac&share_depth=1)|要求 家具 改成 龙头 ， 结果 收到 成 龙头|要求 家具 改成 龙头 ， 结果 收到 成 龙头|句子稍有改动，原句为繁体的「要求家具改成龙头，结果收到“成龙”头」|
|10|我也想过过儿过过的生活|[论断句的重要性 - 微博HTML5版](https://m.weibo.cn/detail/4303684843783227)|我 也 想 过过儿 过过 的 生活|我 也 想 过 过儿 过过 的 生活||
|11|下周日你有空吗？|[论断句的重要性 ——dryadb43738 - 即刻App](https://m.okjike.com/officialMessages/5be25e4e83101200923af414?username=31a05283-aaf9-4e32-86df-86e95cef344e&utm_source=comment_card)|下 周日 你 有空 吗 ？|下 周日 你 有空 吗 ？||
|12|【泪目！解放军战士手牵手趟过中越边境雷场，将安全的土地移交百姓】11月16日，中越边境云南段已扫雷场移交仪式在云南省麻栗坡县猛硐乡老山西侧雷场举行。移交现场，扫雷官兵当着老百姓的面，手牵手趟过雷场，用这种特殊的方式向老百姓说明脚下的每一寸土地都是安全的。致敬！|[新浪军事-微博](https://m.weibo.cn/detail/4308039014228339)|【 泪目 ！ 解放军 战士 手牵手 趟 过 中越 边境 雷场 ， 将 安全 的 土地 移交 百姓 】 11月 16日 ， 中 越 边境 云南 段 已 扫雷 场 移交 仪式 在 云南省 麻栗坡县 猛硐 乡老 山西 侧 雷场 举行 。 移交 现场 ， 扫雷 官兵 当着 老百姓 的 面 ， 手 牵 手 趟 过 雷场 ， 用 这 种 特殊 的 方式 向 老百姓 说明 脚下 的 每 一 寸 土地 都 是 安全 的 。 致敬 ！|【 泪目 ！ 解放军 战士 手牵手 趟 过 中越 边境 雷场 ， 将 安全 的 土地 移交 百姓 】 11 月 16 日 ， 中 越 边境 云南 段 已 扫雷 场 移交 仪式 在 云南省 麻栗坡县 猛 硐 乡 老山 西侧 雷场 举行 。 移交 现场 ， 扫雷 官兵 当着 老百姓 的 面 ， 手牵手 趟 过 雷场 ， 用 这种 特殊 的 方式 向 老百姓 说明 脚下 的 每一寸 土地 都 是 安全 的 。 致敬 ！||
|13|笔记本身为X86平台最能带货的品类，Intel和AMD绝不会忽略掉，所以也照例推出了几款KabyLake-G处理器。|[聊聊Intel和AMD的新婚生活 - 笔吧评测室](https://mp.weixin.qq.com/s/kQ_4_3oGm2419xx0wMcauA)|笔记本 身为 X86 平台 最 能 带货 的 品类 ， Intel 和 AMD 绝不 会 忽略 掉 ， 所以 也 照例 推出 了 几 款 KabyLake-G 处理器 。|笔记本 身为 X86 平台 最 能带 货 的 品类 ， Intel 和 AMD 绝不会 忽略 掉 ， 所以 也 照例 推出 了 几款 KabyLake - G 处理器 。|在此例中，Jieba 对特殊名词的识别不太准，例如 KabyLake-G|

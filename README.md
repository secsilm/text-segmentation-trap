# Text Segmentation Trap

这里会罗列一些容易被分词工具被分错的句子，详细的测试代码见 [notebook](https://github.com/secsilm/text-segmentation-trap/blob/master/segmentation-test.ipynb)。

> 注：`来源` 列中的 `聊天` 指的是该句来源于日常聊天，包括口头聊天和微信等社交软件聊天记录等。

| 序号| 句子| 来源 |Stanford NLP|Jieba|
| :---: | ---|---|---|---|
| 1| 【学术造假爆发】全球40万科学家在假期刊发论文，包括一位诺奖得主！| [【学术造假爆发】全球40万科学家在假期刊发论文，包括一位诺奖得主！](https://mp.weixin.qq.com/s/bu14L15wrBHZ32FNO6sWmA)|【 学术 造假 爆发 】 全球 40万 科学家 在 假期 刊发 论文 ， 包括 一 位 诺奖 得主 ！|【 学术 造假 爆发 】 全球 40 万 科学家 在 假期 刊发 论文 ， 包括 一位 诺 奖得主 ！|
| 2| 只有这时候人才是最齐的| 聊天|只有 这时候 人才 是 最 齐 的|只有 这时候 人才 是 最齐 的|

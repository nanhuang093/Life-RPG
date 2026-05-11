# 🫘 猫猫的 Life RPG

把日常生活变成一场RPG。完成任务,积累经验值,升级,抽扭蛋,收集藏品。

**线上地址:** https://nanhuang093.github.io/Life-RPG

---

## 技术栈

纯HTML+CSS+JS,单文件,无依赖,无构建步骤。
数据存在 `localStorage`,刷新不丢失。
PWA支持,可添加到手机主屏幕。

文件结构:
```
index.html   # 主文件,全部逻辑在这里
manifest.json
sw.js
icon-192.png
icon-512.png
README.md
```

---

## 已完成功能

### 任务系统
三类任务分开存储,独立重置:

**每日任务** (`completedDaily`,每天自动重置):
- 吃早饭/晚饭、牙套、护肤(按星期几自动切换A醛/刷酸/正常)
- 多邻国打卡、学习新内容
- 步行6000步、练背、读书
- 上班打卡(仅工作日)
- 小任务:没有熬夜(50XP/15金)、学唱日语歌、走一万步、修了一个Bug

**每周任务** (`completedWeekly`,每周一自动重置):
- 拼模型三次、side project milestone、和朋友一起玩、约饭
- 力量训练3次、清猫砂盆、大扫除、日语学完一章

**大任务** (`completedWeekly`,和周常一起每周重置):
- 读完一本书、完成在线课程、多邻国日语提升1分
- 拼完大模型、完成完整side project、和朋友旅行、组织聚会

### 等级系统
- 升级公式: `400 + lv * 30` XP (起点高,平滑曲线)
- 每升一级 +20金币
- 每10级自动获得一张稀有扭蛋
- **等级解锁:**
  - Lv.1: 日常任务、扭蛋、成就
  - Lv.3: 每周任务 + 图鉴
  - Lv.5: 奖励大任务 + 高级扭蛋
  - Lv.8: 随机任务掉落
  - Lv.15: 十连抽

### 随机任务
- 完成日常任务 15% 概率掉落,完成周常 30% 概率掉落
- 普通/稀有/史诗三档,周常掉落更好的
- 最多5个同时存在,可完成或忽略
- Lv.8解锁

### 扭蛋系统
- **普通扭蛋** (50金币): 普通60% / 稀有30% / 史诗9% / 传说1%
- **高级扭蛋** (150金币,Lv.5解锁): 普通30% / 稀有40% / 史诗25% / 传说3%
- **十连抽** (450金币,Lv.15解锁)
- 传说稀有度 = 温柔留言,不重复掉落

### 藏品系列
- **🌸 春季限定** (3-5月): 10张,含台词属性
- **🌊 夏季限定** (6-8月): 10张,含台词属性
- 秋季/冬季: 待制作
- **🦐 古生物博物馆**: 10张 emoji风格 (待按年代拆分为6套SVG简笔画)
- **⚔️ 图书馆战争**: 10张角色卡,emoji风格

季节系列按月份自动切换,当季掉落率是其他系列2倍。
图鉴里点击已解锁卡片可放大查看。

### 温柔留言 (传说稀有)
- 🫘 来自黄豆的留言: 10条
- 🐱 来自哥哥的留言: 11条
- 不重复掉落,全部收集后停止

### 成就系统 (递进三档)
8组成就,每组🥉🥈🥇三档,解锁给金币(不给XP):
- 连续打卡 (3/7/30天) — 50/100/200金
- 日常任务 (5/20/50个) — 50/100/200金
- 金币积累 (500/1000/5000) — 50/100/200金
- 等级 (5/10/20级) — 50/100/200金
- 扭蛋次数 (10/50/100次) — 50/100/200金
- 收集完成度 (25/50/100%) — 50/100/200金
- 每周任务 (3/10/30个) — 50/100/200金
- 大任务 (1/3/7个) — 50/100/200金

---

## 已完成 (本次开发)

- [x] 🪸 寒武纪套卡 (10张SVG简笔画): 三叶虫/皮卡虫/马尔虫/奥托亚虫/微网虫/威瓦西虫/怪诞虫/海口鱼/欧巴宾海蝎/奇虾
- [x] SVG卡面支持 — `generateCardSVG` 新增 `svgContent` 字段，有就渲染SVG，否则回退emoji
- [x] 图鉴未收集卡片改为问号占位，不透露卡面设计
- [x] 图鉴从Lv.1解锁（原Lv.3）
- [x] Service worker 改为网络优先，推送新版本后刷新即可生效
- [x] 新增存档导出/导入（成就页底部），解决Safari与PWA localStorage隔离问题
- [x] 新增 `apple-touch-icon`，修复iOS主屏幕图标
- [x] 重设计应用图标：暗底橙猫+青色发光眼

---

## 待做清单

### 藏品系列 (优先级高)

**古生物 SVG 套卡** (每套10张，已有寒武纪)
- [ ] 🪸 奥陶纪/志留纪 — 鹦鹉螺、海蝎、笔石、星甲鱼...
- [ ] 🐟 泥盆纪 — 邓氏鱼、肺鱼、提塔利克鱼、腔棘鱼...
- [ ] 🌿 石炭纪/二叠纪 — 巨脉蜻蜓、引螈、异齿龙、始祖单弓兽...
- [ ] 🦕 中生代 — 三角龙、暴龙、翼龙、鱼龙、沧龙...
- [ ] 🐘 新生代 — 猛犸象、剑齿虎、恐鸟、渡渡鸟...

  > 卡面格式: `{ id, name, rarity, svgContent, color, era, role(拉丁名), quote, stats }`
  > SVG风格参考寒武纪套卡，`currentColor`渲染，坐标系 0 0 280 420，图案居上半部分

**书籍角色卡** (emoji风格，参考图书馆战争)
- [ ] ⚡ 魔道祖师 — 魏无羡/蓝忘机/江澄/温宁/江厌离... (10张)
- [ ] 🌊 万有引力 — 易水歌必须有! (10张)
- [ ] 👾 我在惊悚游戏里封神 — (10张)

**季节限定** (emoji风格)
- [ ] 🍂 秋季限定 9-11月 (10张)
- [ ] ❄️ 冬季限定 12-2月 (10张)

---

### 功能 (优先级中)

- [ ] **完成任务动画** — 打勾时的粒子/光效，升级时更戏剧化的弹窗
- [ ] **好友系统** — 以后再说

---

### 技术债 (低优先级)

- [ ] git config 设置正确的 author name/email（现在每次commit都报警告）
- [ ] SVG filter id 冲突（多卡同页时 `#cglow` 等id重复，目前不影响效果）

---

## 代码结构说明

### state 数据结构
```js
state = {
  xp, gold, goldToday,
  completedDaily: { taskId: true },   // 每天重置
  completedWeekly: { taskId: true },  // 每周重置 (含big类型)
  streak, lastDate, lastWeekStr,
  activeTab,
  randomTasks: [{ id, name, emoji, xp, gold, rarity, done }],
  unlockedAchievements: ['streak_3', 'daily_5', ...],
  stats: {
    tasksCompleted, dailyCompleted, weeklyCompleted,
    bigCompleted, socialCompleted, gachaCount, totalGoldEarned
  },
  collection: {
    spring: ['spring_1', ...],
    summer: ['summer_1', ...],
    fossil: ['fossil_1', ...],
    library: ['lib_1', ...],
    gentleMessages: { huangdou: [0, 2, ...], gege: [1, 3, ...] }
  }
}
```

### 主要函数
- `render()` — 渲染整个UI
- `completeTask(id)` — 完成任务,触发XP/金币/升级/成就/随机任务掉落
- `isTaskDone(task)` / `markTaskDone(task)` — 读写任务完成状态
- `drawGacha(isAdvanced)` — 抽扭蛋
- `drawTenPull()` — 十连抽
- `generateCardSVG(item, collectionName)` — 生成藏品卡面SVG
- `getCurrentSeason()` — 根据月份返回当前季节key
- `checkAchievements()` — 检查并解锁成就
- `rollRandomTask(isWeekly)` — 随机任务掉落

### 藏品数据格式
```js
// emoji风格 (书籍角色卡、季节、现有古生物)
{ id, name, rarity, emoji, color, role, quote, stats: [String, String] }

// SVG简笔画格式 (古生物新套卡,待实现)
// svgContent 是完整的SVG path字符串,在卡面上半部分渲染
{ id, name, rarity, svgContent, color, era, latinName, quote }
```

### 升级曲线
`xpForLevel(lv) = 400 + lv * 30`
- Lv.1→2: 430 XP (~0.7天全日常)
- Lv.10→11: 700 XP (~1.1天)
- Lv.20→21: 1000 XP (~1.6天)

---

## 设计原则

- **不要惩罚机制**: 没有HP掉血,没有断签惩罚,只有奖励
- **温柔优先**: 鼓励语、小惊喜、温柔留言都是为了让猫猫感到被爱
- **从0到1**: 每个完成的任务都是进步,慢慢来
- **书籍角色卡用emoji风格** (不用简笔画,人物简笔画怪怪的)
- **古生物用SVG简笔画** (博物馆插图风格)

---

*由黄豆 🫘 搓的,专属于猫猫 🐱*


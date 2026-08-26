# dsh web 皮肤切换速查

dsh web GUI 的皮肤由 dsh-web-ui 提供，已装 9 款 + 玻璃拟态全局主题。
同一时间只能启用一款皮肤（其余在 patch 里 disabled）。改 ~/.dsh/cordis.patch.yml 后 dsh 配置监视器自动热加载，刷新页面即可，不用重启 dsh web。

## 可用皮肤名

| 名字 | 风格 |
|------|------|
| qq98 | QQ2008 怀旧版（水晶蓝+企鹅） |
| ths | 同花顺风格（炒股红标题栏+实时行情） |
| xp | Windows XP 风格 |
| blue-fantasy | 蓝色幻想（鲸鱼插画+靛蓝） |
| miku | 初音未来（蓝紫品红渐变+毛玻璃） |
| whale-song | 鲸吟（深海蓝发女神+鲸群） |
| trading | 交易终端（顶栏跑马灯行情） |
| dragon-heir | 龙的传人（朱砂龙印） |
| minecraft | 我的世界（像素全景天空盒） |
| official | 恢复官方默认（关掉所有皮肤） |

## 怎么切换

让 AI 帮你切：说"换成 <名字>"，AI 会在 ~/.dsh/cordis.patch.yml 把该名字以外的皮肤全部写 disabled，几秒后热加载生效。

不要自己跑 dsh-skin use <name>：该脚本是为从 GitHub 克隆仓库安装皮肤设计的，默认去 ~/.local/packages/skins/<name> 找源码做软链，而本机皮肤是用 npm 装的（@linxin666/dsh-client-ui-skin-*），目录不存在会报 skin source dir missing。

## 皮肤中心（界面内试穿）

设置 → 插件配置 → Web UI 插件 → 皮肤中心（@linxin666/dsh-client-ui-skin-center）。
卡片里每个皮肤有"试穿"（即时预览，不保存）和"应用"（永久生效）两个按钮。注意："应用"按钮底层也依赖 dsh-skin CLI，本机若没正确布置同样会失败，建议用上面的"让 AI 切"方式。

## 已经装的包

- 全局主题：dsh-client-ui-frosted-glass（玻璃拟态，毛玻璃质感，装上去整站生效，无法在界面里关，只能卸载）
- 皮肤中心：@linxin666/dsh-skins / @linxin666/dsh-client-ui-skin-center
- 9 款皮肤：@linxin666/dsh-client-ui-skin-{qq98,ths,xp,blue-fantasy,miku,whale-song,trading,dragon-heir,minecraft}

## 当前状态

截至记录时：激活 minecraft。其余 8 款 disabled。

# config

此页面介绍config文件夹中的json配置文件。

可在json文件或GUI中更改。

所有配置文件位置：`genshin_assistant\config\*.json`

## 推荐在GUI中修改

目前GUI已经可用。GUI中的设置修改更加稳定准确快速，部分GUI不支持的配置文件才需要手动修改源文件。

## config.json 

位置：config/settings/config.json

| 项目                 | 内容                                                                                                    |
|--------------------|-------------------------------------------------------------------------------------------------------|
| `version`          | 版本号                                                                                                   |
| `teamfile`         | 自动战斗使用的`team.json`文件，可在`config`目录下新建新的`teamjson`文件并设置。                                                |
| `device_torch`     | yolox运算使用的设备，如果安装了cudnn则设为`'gpu'`，否则设为`'cpu'` 。 设置为`auto`时可以自动检测GPU可用性并自动切换。                          |
| `device_paddle`    | paddleocr运算使用的设备，如果安装了cudnn则设为`'gpu'`，否则设为`'cpu'`。 设置为`auto`时，会自动检测GPU可用性，但不会自动切换GPU，需要根据是否可用的提示手动切换。 |
| `debug`            | 是否启用debug模式                                                                                           |
| `env_floder_path`  | envirenment文件夹位置                                                                                      |
| `corr_degree`      | 秘境内视角校准时的辅助参数。若在秘境内视角偏左则增大该值，反之亦然。                                                                    |
| `ChromelessWindow` | 如果是无边框窗口或全屏，设置为true。                                                                                  |

## auto_domain.json

设置自动秘境辅助。

| 项目              | 内容                                               |
|-----------------|--------------------------------------------------|
| `domain_times`  | 刷秘境的次数                                           |      
| `isLiYueDomain` | 挑战部分石化古树被墙壁阻挡视野的秘境(大多位于璃月)时，设置为`true`，否则为`false` |
| `resin`         | 领取奖励时选择的原萃树脂模式，`20`代表小树脂，`40`代表浓缩                |
| `fast_mode`     | 如果无法正常开启挑战，将此项设为false                            |

## keymap.json

可以自定义按键。详情如下：

| 项目           | 内容               |
|--------------|------------------|
| `startstop`  | 在GUI中设置的功能的启停按键。 |
| `autoCombat` | 开关自动战斗的按键        |
| `autoDomain` | 开关自动秘境的按键        |

## character_dist.json

角色名称对照表，每个角色的首项即为该角色名称，其余为角色别名，如：

`["albedo","Albedo","阿贝多","アルベド"]`中，角色名称为`albedo`，其他为别名。

## team.json

默认出战队伍配置文件，在第一次使用前需要根据自己情况更改，或按文件中的配置更改自己的队伍，注意出战顺序要相符。

如配置文件与实际出战队伍角色不符或顺序不符，会造成角色乱放技能、乱切换等问题。

原始文件中的队伍配置为：宵宫，钟离，班尼特，云堇

| 设置项               | 介绍                                                                                                                 |
|:------------------|--------------------------------------------------------------------------------------------------------------------|
| `name`            | 根据`character_dist.json`填写角色名称                                                                                      |
| `priority`        | 出战优先级，从小到大依次降低，0为最高优先级。优先级可以同级                                                                                     |
| `n`               | 角色在队伍中的位置（1~4），不可重复，不可为0                                                                                           |
| `trigger`         | 触发器，触发器条件成立时，允许切换至该角色                                                                                              |
| `autofill`        | 自动填充，在`character.json`文件中有一些已经配置好的角色,此时在`team.json`文件中只需要将`autofill`设置为`true`,并配置`name`,`priority`,`n`,`trigger`即可 |
| `Elast_time`      | E技能持续时间，没有则为0                                                                                                      |
| `Qlast_time`      | Q技能持续时间，没有则为0                                                                                                      |
| `E_short_cd_time` | 短Ecd时间，不能为0                                                                                                        |
| `E_long_cd_time`  | 长Ecd时间，没有则为0                                                                                                       |
| `Ecd_float_time`  | 在E技能冷却还有x秒前即切换至该角色，可以为0，建议设置的值比预计值偏小一点                                                                             |
| `Ecd_press_time`  | 按E技能的时间                                                                                                            |
| `Qcd_time`        | Q技能冷却时间                                                                                                            |
| `tastic_group`    | 策略组，配置角色战斗策略，详细说明见[combat_assi.md](./combat_assi.md)                                                               |

关于参数配置的填写说明见[combat_assi.md](./combat_assi.md)

## tastic.json

暂无用途

## character.json

包含了一些预设的角色策略组参数，`verify`属性可以查看该角色操作是否被验证通过。

## auto_aim

自动瞄准配置文件。

| 设置项                         | 介绍              |
|-----------------------------|-----------------|
| `auto_distan`               | 自动保持距离，默认为false |
| `auto_move`                 | 自动移动视角，默认为true  |
| `fps`                       | 识别频率，默认为20      |
| `max_number_of_enemy_loops` | 最大索敌次数，默认为50    |
| `reset_time`                | 索敌失败后冷却时间，默认为40 |

## auto_pickup

自动拾取配置文件。

| 设置项         | 介绍        |
|-------------|-----------|
| `blacklist` | 拾取物品黑名单列表 |
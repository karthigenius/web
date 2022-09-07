---
title: ApplyAnimation
description: 将动画应用于玩家。
tags: []
---

## 描述

将动画应用于玩家。

| 参数名     | 说明                                                                                                                                                                                              |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --- |
| playerid   | 要应用动画的玩家的 ID。                                                                                                                                                                           |     |
| animlib[]  | 要应用动画的动画库的名称。                                                                                                                                                                        |
| animname[] | 在指定的库中，要应用的动画的名称。                                                                                                                                                                |
| fDelta     | 播放动画的速度（默认使用 4.1）。                                                                                                                                                                  |
| loop       | 如果设置为 1，动画将循环播放。如果设置为 0，动画将播放一次。                                                                                                                                      |
| lockx      | 如果设置为 0，一旦动画完成，玩家就会返回到他们原来的 X 坐标（对于会移动玩家位置的动画，如行走）。1 将不会返回到他们的旧位置。                                                                     |
| locky      | 与上述相同，但对 Y 轴而言。应保持与前面的参数相同。                                                                                                                                               |
| freeze     | 设置为 1 会在动画结束时定住玩家。0 则不会。                                                                                                                                                       |
| time       | 计时器，单位是毫秒。对于永远要循环的动画，应传入 0。                                                                                                                                              |
| forcesync  | 设置为 1 可以使服务器与流半径内的所有其他玩家同步动画（可选）。2 的作用与 1 相同，但只对流入的玩家应用动画，而不是对实际被动画的应用的玩家应用（当玩家被流入时，对 npc 动画和持久性动画很有用）。 |

## 返回值

这个函数总是返回 1，即使指定的玩家不存在，或者任何参数无效（例如无效的库）。

## 案例

```c
ApplyAnimation(playerid, "PED", "WALK_DRUNK", 4.1, 1, 1, 1, 1, 1, 1);
```

## 要点

:::tip

'forcesync' 为可选参数，默认为 0，在大多数情况下不需要传入，因为其他玩家会自动同步动画。'forcesync' 参数可以强制所有可以看到'playerid'的玩家播放动画，而不管该玩家是否正在执行该动画。这在其他玩家不能自动同步动画的情况下很有用。例如，他们可能暂停了游戏而导致没接收到该动画。

:::

:::warning

无效的动画库将使玩家的游戏崩溃。

:::

## 相关函数

- [ClearAnimations](ClearAnimations): 清除玩家正在执行的任何动画。
- [SetPlayerSpecialAction](SetPlayerSpecialAction): 设置玩家的特殊动作。
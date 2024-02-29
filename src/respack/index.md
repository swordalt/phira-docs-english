# Resource Packs

Phira offers the option to customize your gameplay visuals using Resource Packs(Respacks).  Think of them as Minecraft resource packs; they don't change the actual gameplay, only the visual experience.

## File Structure

A respack consists of multiple resource files packaged into one zip file.  Some are required, some are not.

### Files

The following resources are required:

- `click.png` and `click_mh.png`：The skin of the tap note (including simuul.)
- `drag.png`and `drag_mh.png`：The skin of the drag note (including simul.)
- `flick.png` and `flick_mh.png`：The skin of the flick note (including simul.)
- `hold.png` and `hold_mh.png`：The skin of the hold note (including simul.)
- `hit_fx.png`：Hit effect images.

The following resources are optional but recommended:

- `click.ogg`, `drag.ogg` and `flick.ogg`：The hitsounds of the specified notes. (Tap and Hold notes use the same sfx.)
- `ending.mp3`：The results screen background music.

### 配置文件

配置文件采用 yml，其中必填项如下（以默认资源包为例）：

```yml
name: Default
author: "Mivik & MisaLiu"
hitFx: [5, 6]
holdAtlas: [50, 50]
holdAtlasMH: [50, 110]
```

- `name`：资源包的名字；
- `author`：资源包的作者；
- `description`：资源包介绍；
- `hitFx`：打击特效宽、高的帧数。打击特效是将多帧动画存储在一张图中的，因此需要指定这张图中横竖各有几帧，例如，在 [此图](image/hit_fx.jpg) 中横、竖的帧数分别为 5 与 6（最后一行不太看得见，但是是存在的）（图片为了便于辨识使用了黑色背景，但在制作资源包时应当使用透明背景）；
- `holdAtlas`：Hold 贴图的尾、头高度。Hold 的皮肤是 **一张图片**，从上到下分别为 Hold 的尾部、中间和头部。而 `holdAtlas` 的两个数字则分别指定了图片中尾部和头部的高度。例如，在 [此图](image/hold.png) 中，尾部和头部高度均为 50 像素。
- `holdAtlasMH`：意义与上一条类似，指定多押 Hold 的相关信息。

此外还有选填项：

- `hitFxDuration`（小数，默认 `0.5`）：打击特效的持续时间，以秒为单位；
- `hitFxScale`（小数，默认 `1.0`）：打击特效缩放比例；
- `hitFxRotate`（布尔值，默认 `false`）：打击特效是否随 Note 旋转；
- `hitFxTinted`（布尔值，默认 `true`）：打击特效是否依照判定线颜色着色；
- `hideParticles`（布尔值，默认 `false`）：打击时是否隐藏方形粒子效果；
- `holdKeepHead`（布尔值，默认 `false`）：Hold 触线后是否还显示头部；
- `holdRepeat`（布尔值，默认 `false`）：Hold 的中间部分是否采用重复式拉伸。[这里的三张图](image/hold_repeat.jpg) 从左到右依次是 Hold 资源图、不启用 `holdRepeat` 时的长条和启用 `holdRepeat` 时的长条；
- `holdCompact`（布尔值，默认 `false`）：是否把 Hold 的头部和尾部与 Hold 中间重叠。还是用上面的 [示例](image/hold_repeat.jpg)，如果不开启 `holdCompact`，效果就会是左边第一张图，Hold 的头尾是和中间隔开的；而右边两张图都是开启了 `holdCompact` 的效果；
- `colorPerfect`（十六进制颜色代码，默认 `0xe1ffec9f`）：AP（全 Perfect）情况下的判定线颜色；
- `colorGood`（十六进制颜色代码，默认 `0xebb4e1ff`）：FC（全连）情况下的判定线颜色。

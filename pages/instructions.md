# 播放指令

点击左侧的「指令」按钮，即可切换至播放指令界面。

您可以将此界面当作一个简化的 WebGAL 播放器，您可以输入一行行指令，切换 Live2D 模型的动作与表情，张嘴说话等。

![播放指令界面](../images/instructions/preview.png)

配合[输出舞台画面](settings.md#输出舞台画面)功能，您可以录制一些视频以便后期使用。

![输出舞台画面](../images/instructions/obs-spout.png)

> 输出的画面是实时的，透明底的（需要隐藏背景图片）。

## 语法

播放指令的语法模仿了 WebGAL 的脚本语法，都是四段式指令：

<div class="ws-code-bg">
  <span class="ws-command">命令类型</span><!--
  --><span class="ws-operator">:</span><!--
  --><span class="ws-default">主要内容</span><!--
  --><span class="ws-operator"> -</span><!--
  --><span class="ws-arg-key">参数名1</span><!--
  --><span class="ws-operator">=</span><!--
  --><span class="ws-arg-value">参数值1</span><!--
  --><span class="ws-operator"> -</span><!--
  --><span class="ws-arg-key">参数名2</span><!--
  --><span class="ws-operator">=</span><!--
  --><span class="ws-arg-value">参数值2</span><!--
  --><span class="ws-comment">; 行内注释</span>
</div>

<div class="ws-code-bg" style="margin-top: 8px;">
  <span class="ws-command">setFigure</span><!--
  --><span class="ws-operator">:</span><!--
  --><span class="ws-default">anon</span><!--
  --><span class="ws-operator"> -</span><!--
  --><span class="ws-arg-key">motion</span><!--
  --><span class="ws-operator">=</span><!--
  --><span class="ws-arg-value">anon/nf01</span><!--
  --><span class="ws-operator"> -</span><!--
  --><span class="ws-arg-key">expression</span><!--
  --><span class="ws-operator">=</span><!--
  --><span class="ws-arg-value">anon/smile01</span><!--
  --><span class="ws-comment">;</span>
</div>

> 需要注意的是，默认情况下，每条指令都不会等待，类似每个指令都会有一个隐形的「-next」参数。
如果需要执行完指令后等待一段时间，请使用 `wait` 命令。

## 脚本参考

### say

让指定的 Live2D 立绘说话。

<div class="ws-code-bg" style="margin-top: 8px;">
  <span class="ws-command">say</span><!--
  --><span class="ws-operator">:</span><!--
  --><span class="ws-default">随便说几句</span><!--
  --><span class="ws-operator"> -</span><!--
  --><span class="ws-arg-key">target</span><!--
  --><span class="ws-operator">=</span><!--
  --><span class="ws-arg-value">anon</span><!--
  --><span class="ws-operator"> -</span><!--
  --><span class="ws-arg-key">wait</span><!--
  --><span class="ws-comment">;</span>
</div>

- **target**
  
  指定说话的 Live2D 角色名称。

- **wait**

  根据说话内容自动计算说话时间，等待说话结束后再执行下一条指令。如果您对自动生成的等待时间不满意，可以使用 `wait` 命令自定义等待时间。

### wait

等待指定的时间（以毫秒为单位）。

<div class="ws-code-bg" style="display: flex; flex-direction: column;">
  <span>
    <span class="ws-command">say</span><!--
    --><span class="ws-operator">:</span><!--
    --><span class="ws-default">随便说几句</span><!--
    --><span class="ws-operator"> -</span><!--
    --><span class="ws-arg-key">target</span><!--
    --><span class="ws-operator">=</span><!--
    --><span class="ws-arg-value">anon</span><!--
    --><span class="ws-comment">;</span>
  </span>
  <span>
    <span class="ws-command">wait</span><!--
    --><span class="ws-operator">:</span><!--
    --><span class="ws-default">2500</span><!--
    --><span class="ws-comment">;</span>
  </span>
</div>

### shutup

让指定的 Live2D 立绘停止说话。

如果 say 指令不使用 -wait 参数，而是用 wait 指令等待，原来的 say 指令仍然会按照自动生成的时长驱动立绘张嘴。

如果您设置的 wait 指令时长远小于 say 自动生成的张嘴时间，此时您需要手动使用 shutup 指令停止立绘说话。

<div class="ws-code-bg" style="display: flex; flex-direction: column;">
  <span>
    <span class="ws-command">say</span><!--
    --><span class="ws-operator">:</span><!--
    --><span class="ws-default">随便说几句</span><!--
    --><span class="ws-operator"> -</span><!--
    --><span class="ws-arg-key">target</span><!--
    --><span class="ws-operator">=</span><!--
    --><span class="ws-arg-value">anon</span><!--
    --><span class="ws-comment">;</span>
  </span>
  <span>
    <span class="ws-command">wait</span><!--
    --><span class="ws-operator">:</span><!--
    --><span class="ws-default">500</span><!--
    --><span class="ws-comment">;</span>
  </span>
  <span>
    <span class="ws-command">shutup</span><!--
    --><span class="ws-operator">:</span><!--
    --><span class="ws-operator"> -</span><!--
    --><span class="ws-arg-key">target</span><!--
    --><span class="ws-operator">=</span><!--
    --><span class="ws-arg-value">anon</span><!--
    --><span class="ws-comment">;</span>
  </span>
</div>

- **target**
  
  指定闭嘴的 Live2D 角色名称。

### setFigure

设置指定 Live2D 立绘的动作与表情。

语句内容填写 Live2D 立绘的名称。

<div class="ws-code-bg" style="margin-top: 8px;">
  <span class="ws-command">setFigure</span><!--
  --><span class="ws-operator">:</span><!--
  --><span class="ws-default">anon</span><!--
  --><span class="ws-operator"> -</span><!--
  --><span class="ws-arg-key">motion</span><!--
  --><span class="ws-operator">=</span><!--
  --><span class="ws-arg-value">anon/nf01</span><!--
  --><span class="ws-operator"> -</span><!--
  --><span class="ws-arg-key">expression</span><!--
  --><span class="ws-operator">=</span><!--
  --><span class="ws-arg-value">anon/smile01</span><!--
  --><span class="ws-comment">;</span>
</div>

- **motion**
  
  指定 Live2D 立绘的动作名称。

- **expression**

  指定 Live2D 立绘的表情名称。

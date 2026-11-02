# UniXNU-sm8150-common

Qualcomm SM8150（骁龙 855/860）SoC 的 UniXNU 共享支持仓库：SoC 身份、
硬件 `dtsi`、通用内核配置片段、SoC 补丁序列与 SM8150 级组件表。

## 内容

| 路径 | 用途 |
| --- | --- |
| `soc.toml` | 格式 2 SoC 身份；选定共享组件并记录已审阅的硬件参考源 |
| `components.toml` | SM8150 级组件 pin（ArmCpu、NativeUfs、NabuAdreno、AdrenoMetal、metal2vulkan） |
| `dts/sm8150.dtsi` | CPU、PSCI、GIC、UFS + SMMU、A640 GPU/GMU/GPU SMMU 与时钟控制器窗口 |
| `configs/sm8150.config` | SoC 内核配置片段（`XNU_NATIVE_ADRENO`） |
| `patches/xnu/series` | SoC XNU 补丁顺序（当前为空，见注释） |
| `kits/` | 预留给 SoC 级 kit 代码 |

## 用法

设备仓库在 `feeds.toml` 中 pin 本源：

```toml
[[source]]
name = "sm8150"
kind = "soc"
git = "https://github.com/zzweiqing/UniXNU-sm8150-common"
commit = "<40 位提交号>"
```

并在 `board.toml` 中以 `board.soc_source = "sm8150"` 选用。

## 状态

面向 Xiaomi Pad 5（nabu）的 UniXNU 设备目录收录，进行中。
`dts/sm8150.dtsi` 中的硬件数值来自 nabu 固件设备树与 pin 定的
linux-xiaomi-nabu 参考源。XNU、固件与 TrustZone 之间的寄存器归属随板子
而异——在其他 SM8150 板上复用前请先核对设备记录。

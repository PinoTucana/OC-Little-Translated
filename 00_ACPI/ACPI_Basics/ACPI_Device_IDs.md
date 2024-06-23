# ACPI Device IDs

Plug and Play ID | Description
-----------------|------------
`PNP0C08` | **ACPI**. Not declared in ACPI as a device. This ID is used by OSPM for the hardware resources consumed by the ACPI fixed register spaces, and the operation regions used by AML code. It represents the core ACPI hardware itself.
 | | **ACPI**。未在 ACPI 中声明为设备。该 ID 由 OSPM 用于 ACPI 固定寄存器空间消耗的硬件资源，以及供 AML 代码使用的操作区域。它代表核心 ACPI 硬件本身。
`PNP0A05` | **Generic Container Device**. A device whose settings are totally controlled by its ACPI resource information, and otherwise needs no device or bus-specific driver support. This was originally known as Generic ISA Bus Device. This ID should only be used for containers that do not produce resources for consumption by child devices. Any system resources claimed by a PNP0A05 device’s `_CRS` object must be consumed by the container itself.
 | | **通用容器设备**。此设备的设置完全由其 ACPI 资源信息控制，除此之外无需设备或总线专用驱动程序支持。最初称为 "通用 ISA 总线设备"。该 ID 只应用于不产生资源供子设备使用的容器。PNP0A05 设备的 `_CRS` 对象占用的任何系统资源必须由容器本身消耗。
`PNP0A06`| **Generic Container Device**. This device behaves exactly the same as the PNP0A05 device. This was originally known as Extended I/O Bus. This ID should only be used for containers that do not produce resources for consumption by child devices. Any system resources claimed by a PNP0A06 device’s `_CRS` object must be consumed by the container itself.
 | | **通用容器设备**。该设备的行为与 PNP0A05 设备完全相同。最初称为扩展 I/O 总线。该 ID 只应用于不产生资源供子设备使用的容器。PNP0A06 设备的 `_CRS` 对象占用的任何系统资源必须由容器本身消耗。
`PNP0C09`| **Embedded Controller Device**. A host embedded controller controlled through an ACPI-aware driver.
 | | **嵌入式控制器设备**。通过 ACPI 感知驱动程序控制的主机嵌入式控制器。
`PNP0C0A` | **Control Method Battery**. A device that solely implements the ACPI Control Method Battery functions. A device that has some other primary function would use its normal device ID. This ID is used when the devices primary function is that of a battery.
 | | **控制方法电池**。仅实现 ACPI 控制方法电池功能的设备。具有其他主要功能的设备将使用其正常设备 ID。当设备的主要功能是作为电池时，将使用此 ID。
`PNP0C0B` | **Fan**. A device that causes cooling when “on” (D0 device state).
 | | **风扇**。当 "启用"（D0 设备状态）时产生冷却效果的设备。
`PNP0C0C` | **Power Button Device******. A device controlled through an ACPI-aware driver that provides power button functionality. This device is only needed if the power button is not supported using the fixed register space.
 | | **电源按钮设备**。通过 ACPI 感知驱动程序控制，提供电源按钮功能的设备。只有在固定寄存器空间不支持电源按钮时，才需要该设备。
`PNP0C0D`| **Lid Device**. A device controlled through an ACPI-aware driver that provides lid status functionality. This device is only needed if the lid state is not supported using the fixed register space.
 | | **合盖设备**。通过 ACPI 感知驱动程序控制，提供合盖状态功能的设备。只有在固定寄存器空间不支持合盖状态时，才需要该设备。
`PNP0C0E`| **Sleep Button Device**. A device controlled through an ACPI-aware driver that provides power button functionality. This device is optional.
 | | **睡眠按钮设备**。通过 ACPI 感知驱动程序控制，提供睡眠按钮功能的设备。该设备为可选设备。
`PNP0C0F`| **PCI Interrupt Link Device**. A device that allocates an interrupt connected to a PCI interrupt pin. See Section 6.2.13 for more details.
 | | **PCI 中断链接设备**。分配连接到 PCI 中断引脚的中断的设备。详见第 6.2.13 节。
`PNP0C80`| **Memory Device.** This device is a memory subsystem.
 | | **内存设备**。该设备是一个内存子系统。
`ACPI0001`| **SMBus 1.0 Host Controller.** An SMBus host controller (SMB-HC) compatible with the embedded controller-based SMB-HC interface (see Section 12.9), and implementing the SMBus 1.0 Specification.
 | | **SMBus 1.0 主机控制器。** 与基于嵌入式控制器的 SMB-HC 接口（见第 12.9 节）兼容并实施 SMBus 1.0 规范的 SMBus 主机控制器 (SMB-HC)。
`ACPI0002`|Smart Battery Subsystem. The Smart battery Subsystem specified in Section 10, “Power Source Devices.”
 | | **智能电池子系统**。第 10 节 "电源设备 "中详细说明的智能电池子系统。
`ACPI0003`|**Power Source Device.** The Power Source device specified in Section 10, “Power Source Devices.” This can represent either an AC Adapter (on mobile platforms) or a fixed Power Supply.
 | | **电源设备**。第 10 节 "电源设备 "中详细说明的电源设备。可代表交流适配器（移动平台）或固定电源。
`ACPI0004`| **Module Device**. This device is a container object that acts as a bus node in a namespace. A Module Device without any of the `_CRS`, _PRS and `_SRS` methods behaves the same way as the Generic Container Devices (PNP0A05 or PNP0A06). If the Module Device contains a `_CRS` method, only these resources described in the `_CRS` are available for consumption by its child devices. Also, the Module Device can support `_PRS` and `_SRS` methods if `_CRS` is supported.
 | | **模块设备**。该设备是一个容器对象，在命名空间中充当总线节点。模块设备不包含任何 `_CRS`、_PRS 和 `_SRS`方法，其行为与通用容器设备（PNP0A05 或 PNP0A06）相同。如果模块设备包含 `_CRS`方法，则其子设备只能使用 `_CRS`中描述的这些资源。此外，如果支持 `_CRS`，则模块设备可支持 `_PRS` 和 `_SRS` 方法。
`ACPI0005`| **SMBus 2.0 Host Controller**. An SMBus host controller (SMB-HC compatible with the embedded controller-based SMB-HC interface (see Section 12.9), and implementing the SMBus 2.0 Specification.
 | | **SMBus 2.0 主机控制器**。与基于嵌入式控制器的 SMB-HC 接口（见第 12.9 节）兼容的 SMBus 主控制器（SMB-HC），并实施 SMBus 2.0 规范。
`ACPI0006`|**GPE Block Device**. This device allows a system designer to describe GPE blocks beyond the two that are described in the FADT.
 | | **GPE 块设备**。该设备允许系统设计人员对 FADT 中描述的两个 GPE 块之外的 GPE 块进行描述。
`ACPI0007`|**Processor Device**. This device provides an alternative to declaring processors using the processor ASL statement. See Section 8.4 for more details.
 | | **处理器设备**。该设备提供了使用处理器 ASL 语句声明处理器的替代方法。详见第 8.4 节。
`ACPI0008`|Ambient Light Sensor Device. This device is an ambient light sensor. See Section 9.3.
 | | **环境光传感器设备**。该设备是环境光传感器。参见第 9.3 节。
`ACPI0009`| **I/OxAPIC Device**. This device is an I/O unit that complies with both the APIC and SAPIC interrupt models.
 | | **I/OxAPIC 设备**。该设备是同时符合 APIC 和 SAPIC 中断模型的 I/O 设备。
`ACPI000A`|**I/O APIC Device**. This device is an I/O unit that complies with the APIC interrupt model.
 | | **I/O APIC 设备**。该设备是符合 APIC 中断模型的 I/O 设备。
`ACPI000B`|**I/O SAPIC Device**. This device is an I/O unit that complies with the SAPIC interrupt model.
 | | **I/O SAPIC 设备**。该设备是符合 SAPIC 中断模型的 I/O 设备。
`ACPI000C`|**Processor Aggregator Device**. This device provides a control point for all processors in the platform. See Section 8.5.
 | | **处理器聚合器设备**。该设备为平台中的所有处理器提供控制点。参见第 8.5 节。
`ACPI000D`|**Power Meter Device**. This device is a power meter. See Section 10.4.
 | | **功率计设备**。该设备是功率计。参见第 10.4 节。
`ACPI000E`|**Time and Alarm Device**. This device is a control method-based real-time clock and wake alarm. See Section 9.17.
 | | **时钟和闹钟设备**. 该设备是基于控制方法的实时时钟和唤醒闹钟。参见第 9.17 节。
`ACPI000F`|**User Presence Detection Device**. This device senses user presence (proximity). See Section 9.15)
 | | **感知用户检测设备**。该设备可感知用户的存在（接近感知）。参见第 9.15 节）
`ACPI0010`|**Processor container device**. Used to declare hierarchical processor topologies (see Section 8.4.2, and Section 8.4.2.1).
 | | **处理器容器设备**。用于声明分层处理器拓扑结构（参见第 8.4.2 节和第 8.4.2.1 节）。
`ACPI0011`|**Generic Buttons Device**. This device reports button events corresponding to Human Interface Device (HID) control descriptors (see Section 9.18).
 | | **通用按钮设备**。该设备报告与人机接口设备 (HID) 控制描述符（参见第 9.18 节）相对应的按钮事件。
`ACPI0012`|**NVDIMM Root Device.** This device contains the NVDIMM devices. See Section 9.19 and Table 5.126.
 | | **NVDIMM 根设备**。该设备包含 NVDIMM 设备。请参见第 9.19 节和表 5.126。
`ACPI0013`|**Generic Event Device**. This device maps Interrupt-signaled events. See Section 5.6.9.
 | | **通用事件设备**。该设备映射中断信号事件。参见第 5.6.9 节。
`ACPI0014`|**Wireless Power Calibration Device**. This device uses user presence and notification.
 | | **无线功率校准设备**。该设备使用用户感知和通知。
`ACPI0015`| **USB4 host interface device**. See Links to ACPI-Related Documents under the heading “USB4 Host Interface Specification”
 | | **USB4 主机接口设备**。请参阅 "USB4 主机接口规范" 标题下的 ACPI 相关的文件链接
`ACPI0016`| **Compute Express Link Host Bridge**. This device is a Compute Express Link Host bridge.
 | | **Compute Express Link 主机桥**。该设备是 Compute Express Link 主机桥接器。
`ACPI0017`| **Compute Express Link Root Object**. This device represents the root of a CXL capable device hierarchy. It shall be present whenever the platform allows OSPM to dynamically assign CXL endpoints to a platform address space.
 | | **Compute Express Link 根对象**。此设备代表具有 CXL 功能层次结构的根设备。只要平台允许 OSPM 将 CXL 端点动态分配到平台地址空间，它就会出现。
`ACPI0018` | **Audio Composition Device**. This is an ACPI-enumerated device that describes audio component logical connection information within a system.
 | | **音频合成设备**。这是一个 ACPI 枚举设备，用于描述系统内音频组件逻辑连接信息。

**SOURCE**: [**ACPI Specs**](https://uefi.org/specifications), **Chpt. 5.6.7**: "Device Class-Specific Objects"

**来源**： [**ACPI 规格**](https://uefi.org/specifications)，**章 5.6.7**： "设备类特定对象

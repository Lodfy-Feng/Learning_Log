**20250109_Chinese_homebrew**
 /bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)" 中文安装brew 确实好用
**20250111_WSL2_paste**
Because WSL2(Debian) is using the conhost.exe instead of Windows terminal, so I need to turn on the CRTL-shift-v button function manually by the property selection of title bar and click on the Option tab, then find and tick this function
down the page, then we can get this shorcut working
As for the browser function, I learned about tab group which is especially useful when I use it to do the purpose-aimed browsing activity.
**20260106_安装常用中文字体**
Because debian doesn't support the default Chinese, so u need to install the fonts.
```
sudo apt update
sudo apt install fonts-wqy-zenhei fonts-wqy-microhei
**20260120_About_DLP**
深信服,亿赛通(CDG),逻辑/存储芯片制造体系
**20260120_Semiconductor**
这是一个非常关键的问题，涉及现代电子制造的核心工艺。虽然**芯片（如CPU、RAM）确实依赖光刻机在硅片上制造**，但不同类型的存储设备（RAM、SSD、HDD）在**材料、结构和制造流程**上有显著差异。下面分别说明它们的制造原理与过程：

---

### 一、RAM（随机存取存储器）—— 属于**半导体存储器**
#### ✅ 类型：DRAM（动态RAM）、SRAM（静态RAM）
#### 🏭 制造方式：**完全基于硅基集成电路工艺，使用光刻机**

1. **基底**：高纯度单晶硅晶圆（Wafer）。
2. **核心工艺**：
   - 通过**光刻（Photolithography）** 定义晶体管和电容图案；
   - **刻蚀（Etching）**、**离子注入（Ion Implantation）**、**化学气相沉积（CVD）** 等步骤构建三维结构；
   - DRAM 需要制造**深沟槽电容**或**堆叠电容**来存储电荷；
   - SRAM 由 6 个晶体管组成一个存储单元，无需电容，速度更快但面积更大。
3. **后道工序**：
   - 晶圆切割（Dicing）→ 封装（Packaging）→ 测试。

> 🔍 **关键点**：RAM 是**纯半导体器件**，制造完全依赖光刻机（如 EUV 光刻机用于先进制程），与 CPU 同属逻辑/存储芯片制造体系。

---

### 二、SSD（固态硬盘）—— 核心是 **NAND Flash 闪存芯片**
#### ✅ 存储介质：NAND Flash（一种非易失性半导体存储器）
#### 🏭 制造方式：**同样基于硅晶圆 + 光刻，但结构更复杂**

1. **基底**：硅晶圆。
2. **核心结构**：
   - 每个存储单元是一个**浮栅晶体管（Floating Gate Transistor）** 或 **电荷捕获型（Charge Trap，如 3D NAND）**；
   - 数据通过向浮栅注入/释放电子来表示 0/1。
3. **3D NAND 技术**（现代 SSD 主流）：
   - 不再仅在平面扩展，而是**垂直堆叠数十至数百层存储单元**；
   - 使用**深孔刻蚀（High-aspect-ratio etching）** 和**原子层沉积（ALD）** 构建多层结构；
   - 仍需多次光刻步骤对齐各层。
4. **封装**：
   - 多颗 NAND 芯片 + 控制器芯片（也是硅基 ASIC）封装成 BGA 或 M.2 模块。

> 🔍 **关键点**：SSD 的“存储颗粒”本质是**特殊结构的半导体芯片**，制造高度依赖先进光刻与刻蚀设备，但**控制器和固件**也至关重要。

---

### 三、HDD（机械硬盘）—— **非半导体存储，机电混合系统**
#### ✅ 存储原理：**磁记录（Magnetic Recording）**
#### 🏭 制造方式：**精密机械 + 磁性薄膜工艺，几乎不用光刻机**

HDD **不依赖硅基集成电路进行数据存储**，其核心组件包括：

| 组件 | 制造技术 |
|------|--------|
| **盘片（Platter）** | 铝合金或玻璃基板 → 溅射沉积多层薄膜（磁性层、保护层）→ 表面抛光至原子级光滑 |
| **磁头（Read/Write Head）** | 微机电系统（MEMS）工艺，使用**薄膜沉积、光刻（微米级，非先进制程）** 制作巨磁阻（GMR）或隧道磁阻（TMR）传感器 |
| **音圈电机 & 主轴** | 精密机械加工、轴承、伺服控制 |
| **控制电路板** | 普通 PCB + 半导体芯片（用于接口和缓存），这部分才用到传统 IC |

> 🔍 **关键点**：HDD 的**数据存储本身发生在磁性盘片上**，靠磁头改变微小区域的磁化方向。其制造属于**精密机械+磁学薄膜工程**，与 CPU/RAM 的纳米级光刻无关。磁头制造虽用光刻，但精度要求远低于逻辑芯片（微米级 vs 纳米级）。

---

### 四、对比总结

| 存储类型 | 存储原理       | 是否用光刻机（先进制程） | 核心材料     | 是否半导体 |
|----------|----------------|--------------------------|--------------|------------|
| **RAM**  | 电荷（电容/触发器） | ✅ 是（EUV/DUV）         | 硅           | ✅ 是       |
| **SSD**  | 浮栅/电荷捕获    | ✅ 是（3D NAND 需多层光刻）| 硅 + 介电材料 | ✅ 是       |
| **HDD**  | 磁化方向        | ❌ 否（仅磁头用微米光刻） | 铝/玻璃 + 磁性合金 | ❌ 否（机电系统） |

---

### 附加说明：为什么 HDD 还没被淘汰？
- **成本低**：每 GB 价格远低于 SSD；
- **容量大**：单盘可达 20–30 TB；
- **适合冷数据**：长期存储、备份等场景。

但 HDD **无法做到 RAM/SSD 的高速随机访问**，且怕震动、功耗高。

---

✅ **结论**：  
- **RAM 和 SSD 的存储单元都是半导体芯片，制造高度依赖光刻机**；  
- **HDD 是机电设备，靠磁记录存储数据，制造以精密机械和磁性薄膜为主，基本不依赖先进光刻**。

如果你正在开发嵌入式系统（如使用 Buildroot），理解这些差异有助于选择合适的存储方案（如 eMMC vs SATA SSD vs SPI NOR Flash）。需要进一步了解某类存储的细节（如 NAND 页/块管理、DRAM 刷新机制等），可继续提问。

麦克风上那个看似简单的“毛绒外壳”，实际上是一个同时解决 流体力学问题 和 静电学问题 的优雅设计：

对空气流：它作为一个 “湍流粉碎器”和“缓冲器”，将破坏性的集中气流转化为无害的均匀流动。

对声波：它作为一个 “高通透性过滤器”，允许声音信号几乎无损耗地通过。

对静电场：它作为一个 “绝缘间距增加器”和“电荷缓和消散器”，防止了剧烈的静电放电，保护了灵敏的电路并消除了爆音。

因此，它不仅是保护罩，更是保证麦克风能清晰、安静地拾取到纯净声波振动信号的关键部件。这正是一个从物理原理出发，完美解决实际工程需求的典范。

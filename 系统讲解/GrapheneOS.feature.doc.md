# [功能概述](https://grapheneos.org/features#features)

GrapheneOS 是一款私密安全的移动操作系统，功能强大，易用性出色。它以[Android 开源项目 (AOSP)](https://source.android.com/)的强大基础为基石，并致力于避免增加攻击面或损害其强大的安全模型。GrapheneOS 通过一系列精心设计的功能，显著提升了隐私性和安全性，这些功能旨在抵御真正的攻击者。该项目非常重视易用性和应用兼容性，因此我们所有功能的开发都充分考虑了这些因素。

GrapheneOS 注重实质内容，而非品牌和营销。它不会像传统做法那样，堆积一堆不安全的功能，让对手浑然不知，从而降低实际的隐私/安全性。这是一个技术性极强的项目，旨在将隐私和安全功能融入操作系统，而不是添加各种无用的装饰或捆绑主观的第三方应用选择。

GrapheneOS 也在努力弥补未将 Google 应用和服务捆绑到操作系统中造成的缺陷。我们并不反对用户使用 Google 服务，但 Google 服务不应以侵入性的方式集成到操作系统中。GrapheneOS 不会走捷径，简单地将非常不完整且安全性较差的第三方 Google 服务重新实现捆绑到操作系统中。那样用户永远无法信赖。如果只注重让系统正常运行，而不注重其稳健性和安全性，那么它只会不断追求目标，提供的安全性也会比真正的系统更差。

本页面概述了目前已实现的、与 AOSP 不同的 GrapheneOS 功能。本页面未记录我们许多由于各种原因而不再包含的历史功能。我们的许多功能已在 AOSP、Linux、[LLVM](https://llvm.org/)以及 GrapheneOS 所基于的其他项目中实现，因此未在此处列出。在许多情况下，我们参与了这些功能在核心基础设施项目中的实现。

## [目录](https://grapheneos.org/features#table-of-contents)

- [石墨烯操作系统](https://grapheneos.org/features#grapheneos)
  - [防御未知漏洞的利用](https://grapheneos.org/features#exploit-protection)
    - [攻击面减少](https://grapheneos.org/features#attack-surface-reduction)
      - [USB-C 端口和 pogo 针控制](https://grapheneos.org/features#usb-c-port-and-pogo-pins-control)
    - [漏洞缓解措施](https://grapheneos.org/features#exploit-mitigations)
    - [改进的沙盒](https://grapheneos.org/features#improved-sandboxing)
    - [反持久性/检测](https://grapheneos.org/features#anti-persistence)
  - [更完整的修补](https://grapheneos.org/features#more-complete-patching)
  - [沙盒化的 Google Play](https://grapheneos.org/features#sandboxed-google-play)
  - [Android Auto](https://grapheneos.org/features#android-auto)
  - [网络权限切换](https://grapheneos.org/features#network-permission-toggle)
  - [传感器权限切换](https://grapheneos.org/features#sensors-permission-toggle)
  - [存储范围](https://grapheneos.org/features#storage-scopes)
  - [联系范围](https://grapheneos.org/features#contact-scopes)
  - [广泛的运营商支持，无需侵入运营商访问](https://grapheneos.org/features#broad-carrier-support)
  - [仅 LTE 模式](https://grapheneos.org/features#lte-only-mode)
  - [Wi-Fi隐私](https://grapheneos.org/features#wifi-privacy)
  - [网络位置](https://grapheneos.org/features#network-location)
  - [私人截图](https://grapheneos.org/features#private-screenshots)
  - [封闭式设备标识符泄漏](https://grapheneos.org/features#closed-device-identifier-leaks)
  - [默认隐私](https://grapheneos.org/features#privacy-by-default)
  - [PIN 码扰码](https://grapheneos.org/features#pin-scrambling)
  - [双因素指纹解锁](https://grapheneos.org/features#two-factor-fingerprint-unlock)
  - [支持更长的密码](https://grapheneos.org/features#supports-longer-passwords)
  - [自动重启](https://grapheneos.org/features#auto-reboot)
  - [清除内存中的敏感数据](https://grapheneos.org/features#clearing-sensitive-data-from-memory)
  - [胁迫 PIN/密码](https://grapheneos.org/features#duress)
  - [指纹解锁更安全](https://grapheneos.org/features#more-secure-fingerprint-unlock)
  - [改进的用户配置文件](https://grapheneos.org/features#improved-user-profiles)
    - [更多用户资料](https://grapheneos.org/features#more-user-profiles)
    - [结束会话](https://grapheneos.org/features#end-session)
    - [禁用应用程序安装](https://grapheneos.org/features#disabling-app-installation)
    - [安装可用的应用程序](https://grapheneos.org/features#install-available-apps)
    - [通知转发](https://grapheneos.org/features#notification-forwarding)
  - [GrapheneOS 应用程序存储库](https://grapheneos.org/features#grapheneos-app-repository)
  - [Vanadium：强化的 WebView 和默认浏览器](https://grapheneos.org/features#vanadium)
  - [审计员应用程序和鉴证服务](https://grapheneos.org/features#auditor)
  - [GrapheneOS相机](https://grapheneos.org/features#grapheneos-camera)
  - [GrapheneOS PDF 查看器](https://grapheneos.org/features#grapheneos-pdf-viewer)
  - [GrapheneOS 安装向导](https://grapheneos.org/features#setup-wizard)
  - [加密备份](https://grapheneos.org/features#encrypted-backups)
  - [位置数据访问指示器](https://grapheneos.org/features#location-data-access-indicator)
  - [可以禁用用户安装的应用程序](https://grapheneos.org/features#user-installed-apps-can-be-disabled)
  - [改进了 VPN 泄漏阻止功能](https://grapheneos.org/features#improved-vpn-leak-blocking)
  - [日志查看器和面向用户的崩溃报告](https://grapheneos.org/features#log-viewer-and-crash-reporting)
  - [其他功能](https://grapheneos.org/features#other-features)
- [服务](https://grapheneos.org/features#services)
- [项目](https://grapheneos.org/features#project)

## [石墨烯操作系统](https://grapheneos.org/features#grapheneos)

这些是 GrapheneOS 的功能，超越了 Android 开源项目 16 版的功能。它仅涵盖我们对 AOSP 的改进，而不包含基础功能。本节不列出标准应用沙盒、启动验证、漏洞缓解措施（ASLR、SSP、影子调用堆栈、控制流完整性等）、权限系统（仅限前台和一次性权限授予、作用域文件访问控制等）等功能，而仅列出我们对现代 Android 的改进。我们计划提供一个单独的页面来列出我们为 Android 做出的改进，因为这些功能虽然占据了我们整个历史工作的很大一部分，但并未在此处列出。

### [防御未知漏洞的利用](https://grapheneos.org/features#exploit-protection)

GrapheneOS 高度重视保护用户免受攻击者利用未知（0 day）漏洞的攻击。在供应商知晓漏洞并开发和发布补丁之前，修补漏洞并不能保护用户。

未知（0 day）漏洞的使用范围远超大多数人的想象，它们不仅在定向攻击中利用用户漏洞，还在广泛的部署中利用用户漏洞。Project Zero 维护着[一个电子表格](https://docs.google.com/spreadsheets/d/1lkNJ0uQwbeC1ZTRrxdtuPLCIl7mlUreoKfSIgajnSyY/view#gid=0)，用于追踪在野外检测到的零日漏洞利用情况。由于它只记录了攻击者被发现利用用户的案例，因此这只是对现状的一个概览，这通常是因为这些攻击并非定向攻击，而是部署在公共网站上等。

第一道防线是减少攻击面。删除不必要的代码或暴露的攻击面可以彻底消除许多漏洞。GrapheneOS 避免移除任何对最终用户有用的功能，但我们仍然可以默认禁用许多功能，并要求用户选择启用，从而为大多数用户消除这些功能。我们在 Android 上游实现的一个例子是默认禁止使用内核的分析支持，因为它过去是、现在仍然是 Linux 内核漏洞的主要来源。现在，只有启用开发者工具、启用 Android 调试桥 (ADB)，并通过 ADB 使用分析工具的开发者应用才能使用分析功能。而且，该功能仅在下次启动前启用。由于这是我们在 Android 系统中实现的功能之一，因此下面没有列出此功能。

下一道防线是阻止攻击者利用漏洞，方法是使其无法利用、不可靠，或至少显著提高漏洞利用难度。绝大多数漏洞都是众所周知的 bug，可以通过使用语言/工具规避这些 bug，或使用强大的漏洞缓解措施来阻止利用。在许多情况下，漏洞类别可以被完全清除，而在许多其他情况下，至少可以显著提高漏洞利用难度。Android 在这方面做了大量工作，而 GrapheneOS 则在 Android 和 Linux 内核中推动了这一进程。开发针对这些问题的根本性修复需要耗费大量资源，而且部署这些修复通常会带来很高的性能、内存或兼容性成本。主流操作系统通常不会将安全性置于其他方面之上。GrapheneOS 愿意更进一步，因此我们为用户提供了切换开关，让他们选择自己喜欢的妥协方案，而不是强制用户接受。与此同时，即使漏洞缓解措施较弱或不够完善，只要基于清晰的威胁模型开发，仍然可以提供有效的防御攻击的屏障。 GrapheneOS 在开发这些保护措施的许多领域投入了大量资金：开发/部署内存安全语言/库、静态/动态分析工具和多种缓解措施。

最后一道防线是通过不同级别的沙盒进行遏制：围绕特定上下文的细粒度沙盒（例如每个站点的浏览器渲染器）、围绕特定组件的沙盒（例如 Android 的媒体编解码器沙盒）以及应用/工作区沙盒（例如用于对每个应用进行沙盒保护的 Android 应用沙盒，它也是用户/工作配置文件的基础）。GrapheneOS 通过强化内核和其他基础操作系统组件以及改进沙盒策略来改进所有这些沙盒。

防止攻击者通过验证启动来持续控制组件或操作系统/固件并避免对持久状态的信任也有助于减轻发生攻击后的损害。

远程代码执行漏洞最为严重，攻击者可以利用这些漏洞在设备上立足，甚至远程控制设备。本地代码执行漏洞允许攻击者远程入侵应用/浏览器渲染器、入侵应用的供应链或诱使用户安装恶意应用，从而突破沙盒（包括应用沙盒或浏览器渲染器沙盒）。虽然还存在许多其他类型的漏洞，但我们正在防范的漏洞大多属于这两大类。

绝大多数本地和远程代码执行漏洞都是由内存不安全语言或内存安全语言中罕见的低级不安全代码引起的内存损坏漏洞。其余大多数问题是由动态代码执行/加载功能引起的。我们的主要重点是预防或提高利用内存损坏漏洞的难度，然后限制动态代码执行，这既是为了使内存损坏漏洞升级变得更加困难，也是为了直接缓解由动态代码加载/生成/执行（例如 JIT 编译器漏洞或插件加载漏洞）引起的漏洞。

#### [攻击面减少](https://grapheneos.org/features#attack-surface-reduction)

- 通过删除不必要的代码，使更多功能可选，并在屏幕锁定时（USB、USB-C、pogo pins、摄像头访问）以及超时后（蓝牙、Wi-Fi）默认禁用可选功能（NFC、蓝牙、UWB 等），大大减少了远程、本地和基于接近度的攻击面。
- 所有捆绑应用的原生调试 (ptrace) 访问均被屏蔽，以减少本地攻击面。为了兼容，用户安装的应用默认允许访问 ptrace，并提供默认屏蔽选项。在这两种情况下，都可以根据每个应用手动屏蔽或允许 ptrace 访问。当被屏蔽访问 ptrace 的应用尝试使用 ptrace 时，GrapheneOS 会显示一条通知，链接至每个应用的原生调试设置屏幕。

##### [USB-C 端口和 pogo 针控制](https://grapheneos.org/features#usb-c-port-and-pogo-pins-control)

我们的**USB-C 端口和弹簧针**设置可在操作系统启动时防止通过 USB-C 或弹簧针发起的攻击。对于大多数不带弹簧针的设备，该设置标记为**“USB-C 端口”**。

该功能有五种模式：

- 离开
- 仅充电
- 锁定时仅充电
- 锁定时仅充电，首次解锁前除外
- 在

默认设置**为锁定时仅充电**，这显著减少了设备锁定时的攻击面。锁定后，它会立即阻止任何通过 USB-C 和 pogo pin 的新 USB 连接，这在硬件层面上是通过配置 USB 控制器实现的，在内核的操作系统层面上也同样如此，从而提供第二层防御。一旦现有连接终止，它会立即在硬件层面禁用数据线（如果没有 USB 连接，则会立即终止）。它还会在操作系统和硬件层面禁用 USB-C 备用模式（包括 DisplayPort）。

我们的实现比 Android 设备管理应用可用的标准 USB HAL 切换开关安全得多。标准功能仅禁用操作系统中的高级 USB 处理。它不会阻止新的 USB 连接，也不会在硬件级别禁用数据线。它还会在操作系统中启用 USB-C 和 pogo pin 协议的处理，并且不会禁用 USB-C 备用模式。标准功能也会在高级级别阻止或不阻止 USB，但无法阻止新连接，并且仅在现有连接结束后禁用 USB。其他操作系统尝试通过标准切换开关实现类似的功能，最终会继续允许操作系统中的新 USB 连接，直到所有连接都结束，而不是像我们针对两种锁定时仅充电模式所采用的两阶段方法。

最高安全性的**关机**模式除了禁用数据外，还会禁用充电，从而消除了 USB 控制器和支持充电（包括 USB-PD 协议）的操作系统的剩余攻击面。由于设备在关机、启动至基于固件的快速启动模式或充电、恢复和快速启动模式下，整体功能均不适用，因此不存在设备无法充电的风险。

#### [漏洞缓解措施](https://grapheneos.org/features#exploit-mitigations)

- 强化应用程序运行时
- [安全的应用程序生成系统](https://grapheneos.org/usage#exec-spawning)避免跨应用程序共享地址空间布局和其他机密
- [强化的 libc](https://github.com/GrapheneOS/platform_bionic)可防御最常见的漏洞类型（内存损坏）
- 我们自主研发的[强化 malloc（内存分配器）](https://github.com/GrapheneOS/hardened_malloc)利用现代硬件功能，有效防御最常见的漏洞类别（例如堆内存损坏），并缩短敏感数据在内存中的生存期。hardened_malloc[的 README 文件](https://github.com/GrapheneOS/hardened_malloc/blob/main/README.md)包含详尽的文档。hardened_malloc 项目可移植到其他基于 Linux 的操作系统，并且正在被 Secureblue 等其他注重安全的操作系统采用。我们的分配器也极大地影响了[下一代 musl malloc 实现](https://www.openwall.com/lists/musl/2020/05/13/1)的设计，该实现比 musl 之前的 malloc 提供了显著更高的安全性，同时仍保持了最小的内存占用和代码大小。
  - 完全离线元数据，具有损坏保护，排除了传统分配器的利用
  - 为元数据、大型分配和每个 slab 分配大小类划分单独的内存区域，使用高熵随机基数，并且不同区域之间不重复使用地址空间
  - 确定性检测任何无效的免费
  - 通过检查内存在再次释放之前是否仍为零来检测释放后写入操作，从而实现零释放
  - 通过确定性和随机性隔离的组合来延迟地址空间和内存分配的重用，以缓解释放后使用漏洞
  - 细粒度随机化
  - 积极的一致性检查
  - 围绕大于 16k 的分配设置内存保护防护区域，并对 128k 及以上的防护区域大小进行随机化
  - 小于 16k 的分配在包含分配的每个 slab 周围都有保护区域（例如，16 字节的分配位于 4096 字节的 slab 中，其前后都有 4096 字节的保护区域）
  - 在这些较小的分配中添加以零开头的随机金丝雀，以阻止 C 字符串溢出，吸收小溢出，并在检查金丝雀值时检测线性溢出或其他堆损坏（主要在空闲时）
  - 针对 slab 分配（128k 及以下）的硬件内存标记，提供对所有释放后使用和对象间溢出的概率检测，以及对所有小/线性溢出和释放后使用进行确定性检测，直到它被重复使用一次并经过两次隔离
- 在 ARMv9 上，我们构建的用户空间操作系统代码（而非特定应用程序）都启用了分支目标识别 (BTI) 和指针验证代码 (PAC) 返回地址保护
- 对于禁用自动溢出检查的代码，C 和 C++ 中对有符号整数溢出进行了明确定义
- 强化内核
  - arm64 上启用了 4 级页表，以提供更大的地址空间（48 位而不是 39 位），并且熵值明显更高地址空间布局随机化（33 位而不是 24 位）。
  - 主内核内存分配器（slab、page_alloc、不可执行的 vmalloc）中使用基本硬件内存标记，以提供所有使用后释放和对象间溢出的概率检测，以及使用后释放的确定性检测，直到再次分配内存（我们计划添加对 hardened_malloc 等小型/线性溢出的确定性检测）
  - 以零为前导的随机金丝雀被添加到内核堆（slub）中，以阻止 C 字符串溢出、吸收小溢出并在检查金丝雀值时检测线性溢出或其他堆损坏（空闲、复制到/从用户空间复制等）。
  - 内存在低级内核页面分配器和高级内核堆分配器 (slub) 中释放后会立即被擦除（清零）。这大大缩短了敏感数据在内存中的生存期，缓解了 UAF 漏洞，并使大多数未初始化数据使用漏洞变得无害。如果不进行改进，已释放的内存将无限期地保留数据，直到被分配用于其他用途并被新数据部分或全部覆盖。
  - 在早期启动过程中，所有操作系统未使用的内存都会被清零，以清除上次启动留下的数据，以防零释放功能在干净重启/关机过程中无法清除这些数据。我们支持的所有设备都具备重置攻击防护功能。我们建议将内存清零用于基于固件的启动模式，但我们需要自行为操作系统启动模式添加此功能，以完成这项工作。完全加密的 RAM 以及每次启动时循环的密钥最终将取代这些功能，使其不再适用于较新的设备。
  - 内核堆栈分配被清零，以使大多数未初始化数据使用漏洞无害。
  - 通过禁用功能或设置基础设施以根据需要动态启用/禁用它们（perf，ptrace）来减少各种攻击面。
  - 已启用各种上游强化功能，其中包括许多我们作为 Linux 强化项目的一部分参与开发和实现上游的功能（我们打算将其恢复为一个更加活跃的项目）。
  - 使用每个构建的 RSA 4096 / SHA256 密钥强制内核模块签名并将锁定模式设置为强制保密模式有助于在内核和用户空间之间强制执行低级边界，即使 SELinux 策略出现错误或用户空间受到严重损害。
  - 对经常针对的内核数据结构启用额外的一致性/完整性检查。
  - 在 ARMv9 上，除了基于 Clang 类型的控制流完整性 (CFI) 之外，还启用了分支目标识别 (BTI)，以覆盖基于类型的 CFI 中排除的功能
  - 在 ARMv9 上，除了指针认证码 (PAC) 返回地址保护外，还启用了 ShadowCallStack (SCS)，而不是仅在 PAC 不可用时启用 SCS
- Android 运行时即时 (JIT) 编译/性能分析已完全禁用，并替换为完全提前 (AOT) 编译。基础操作系统中唯一的 JIT 编译是 V8 JavaScript JIT，它在支持按站点异常的 Vanadium 浏览器中默认处于禁用状态。
- 几乎整个基础操作系统都会阻止原生代码或 Java/Kotlin 类的动态代码加载。此功能与验证启动功能协同工作，以防止基础操作系统进程运行攻击者控制的原生代码或 Java/Kotlin 代码。基础操作系统策略的唯一例外是允许媒体 DRM 沙盒的内存代码加载和 Vanadium JIT 编译器。Vanadium 默认对所有网站和使用 WebView 的应用禁用 JIT 编译，但我们的 PDF 查看器应用除外。Vanadium 默认禁用 JIT 编译器，并为每个网站和每个应用提供 JIT 编译器切换开关，并根据每个网站/每个应用的 JIT 编译器切换开关，使用 seccomp-bpf 在每个进程上强制阻止动态代码加载。
- 您可以通过三个漏洞保护开关为用户安装的应用禁用原生代码或 Java/Kotlin 类的动态代码加载：从内存动态加载代码、从存储动态加载代码和 WebView JIT。此功能还可用于为我们的 PDF 查看器选择退出 WebView JIT，以及为 Vanadium 浏览器选择从内存动态加载代码，以禁用对每个站点选择加入 JIT 编译的支持。为了使动态代码加载开关更易于使用，当应用的从内存或存储动态加载代码被阻止时，我们会向用户显示通知，包括在从存储阻止时显示的文件路径。这允许用户为所有应用禁用此功能，然后为需要此功能的应用启用此功能。
- 文件系统访问强化

#### [改进的沙盒](https://grapheneos.org/features#improved-sandboxing)

GrapheneOS 通过强化 SELinux 策略和 seccomp-bpf 策略，以及强化内核等实现应用沙盒的组件，为攻击者（如果能够利用这些组件）提供逃逸路径，从而改进了应用沙盒。我们主要关注应用沙盒，但也改进了其他沙盒，包括直接改进 Web 浏览器渲染器沙盒。该沙盒用于操作系统提供的默认浏览器和 WebView 渲染引擎，并被从专用浏览器到即时通讯应用等大量其他应用所使用。

#### [反持久性/检测](https://grapheneos.org/features#anti-persistence)

- 增强的[验证启动，](https://source.android.com/docs/security/features/verifiedboot)具有更好的安全性和减少的攻击面
- GrapheneOS 完成了操作系统中软件包 (APK) 带外更新的验证启动功能尚未完全实现。我们强制要求在安装时和启动时对系统应用更新的 fs-verity 元数据进行可信密钥签名。这提供了持续验证，每次读取带外 APK 更新都会进行验证，就像每次读取固件、操作系统映像或 APEX 更新一样。强制使用签名密钥和版本是为了防止降级或其他攻击，例如用来自其他支持 GrapheneOS 的设备中的相同软件包变体替换软件包。我们禁用了持久性软件包解析缓存，以防止通过这种原本高度持久的状态绕过元数据检查。由于无法获取先前启动的数据，这只会对启动时间产生非常小的负面影响（通常少于 1 秒）。
- GrapheneOS 弥补了一个漏洞，即当系统组件作为操作系统的一部分进行更新时，由于 versionCode 不会递增，作为操作系统一部分构建的基于应用的系统组件可能会被降级到旧版本。我们在软件包安装和启动时都强制执行了这一操作。
- 增强的基于硬件的证明，具有更精确的版本信息
- [通过我们的审计应用程序和证明服务](https://grapheneos.org/features#auditor)进行基于硬件的安全验证和监控[](https://grapheneos.org/features#auditor)
- 压缩 APEX 模块支持被禁用，因为它对 GrapheneOS 没有用，使用了额外的不必要的存储空间并增加了更多经过验证的启动攻击面。

### [更完整的修补](https://grapheneos.org/features#more-complete-patching)

GrapheneOS 修复了大量 Android 中尚未修复的漏洞。

我们能够快速安全地将最新的 Linux 内核 LTS 版本发布到支持 GKI（通用内核映像）的设备（包括第六代和第七代 Pixel 手机）上。截至 2023 年 11 月 6 日撰写本文时，GrapheneOS 正在为第六代和第七代 Pixel 手机使用最新的 Linux 5.10 GKI LTS 版本 (5.10.199)。自 2022 年 12 月 2 日起，Pixel OS 的原生版本运行在 Linux 5.10.157 上，并反向移植了少量额外的补丁。这意味着 GrapheneOS 提供了数百个相关的内核补丁，其中包括许多原生 OS 中尚未包含的安全补丁。由于他们采用在经过长时间的冻结和测试后，每季度才发布新 LTS 版本的方式，我们得以领先数月。

我们经常自己发现新的漏洞并将其报告给上游。我们已经报告了数十个针对通用 Android 代码库和 Pixel 的漏洞。我们还经常发现一些本应包含但最终被遗漏的补丁，尤其是在存在部分共享但不同设备的代码库彼此独立的设备专用组件的情况下。

我们的总体方法是专注于系统隐私和安全改进，但修复个别漏洞仍然非常重要。

### [沙盒化的 Google Play](https://grapheneos.org/features#sandboxed-google-play)

GrapheneOS 具有兼容层，允许在标准应用沙盒中安装和使用 Google Play 的官方版本。与绕过应用沙盒并获得大量高权限访问权限不同，Google Play 在 GrapheneOS 上绝对不会获得任何特殊访问权限或特权。相反，兼容层会教会 GrapheneOS 如何在完整的应用沙盒中工作。它也不会像在其他地方那样用作操作系统服务的后端，因为即使安装了 GrapheneOS，它也不会使用 Google Play。

由于 Google Play 应用只是 GrapheneOS 上的常规应用，因此您需要将它们安装在特定的用户或工作配置文件中，并且它们仅在该配置文件内可用。只有同一配置文件内的应用才能使用它，并且需要它们明确选择使用。它的工作方式与任何其他应用相同，并且没有特殊功能。与任何其他应用一样，它无法访问其他应用的数据，并且需要用户明确同意才能访问配置文件数据或获得标准权限。同一配置文件内的应用可以在相互同意的情况下进行通信，沙盒 Google Play 也是如此。

沙盒化的 Google Play 功能已接近全面，并与依赖 Google Play 的应用生态系统几乎完全兼容。只有一小部分特权功能（我们尚未将其移植到兼容层的其他方法）不可用。某些功能本质上是特权功能，无法作为兼容层的一部分提供。

绝大多数 Play 服务功能均运行良好，包括动态下载/更新模块（Dynamite 模块）以及模块化应用组件（例如 Google Play 游戏）提供的功能。默认情况下，位置请求会被重新路由到 GrapheneOS 提供的 Play 地理位置服务的重新实现。如果您需要 Google 网络位置服务及相关功能，可以禁用重新路由并使用标准的 Play 服务地理位置服务。

我们的兼容层全面支持 Play Store。P​​lay Store 服务全面可用，包括应用内购买、Play Asset Delivery、Play Feature Delivery 以及应用/内容许可检查。它可以采用标准方式安装、更新和卸载应用，但需要用户授权其作为应用源并同意每项操作。它将使用 Android 12+ 标准的无人值守更新功能，对上次安装的应用进行自动更新。

有关说明，请参阅[沙盒 Google Play 上的使用指南部分。](https://grapheneos.org/usage#sandboxed-google-play-installation)

### [Android Auto](https://grapheneos.org/features#android-auto)

GrapheneOS 提供了安装和使用 Android Auto 官方版本的选项。

Android Auto 需要特权访问才能运行。GrapheneOS 使用沙盒 Google Play 兼容层的扩展，使 Android Auto 能够在较低的权限级别下运行。

有关更多详细信息，请参阅[Android Auto 的使用指南部分](https://grapheneos.org/usage#android-auto)。

### [网络权限切换](https://grapheneos.org/features#network-permission-toggle)

GrapheneOS 添加了网络权限切换开关，用于禁止直接或间接访问任何可用网络。设备本地网络 (localhost) 也受此权限保护，这对于防止应用使用该网络在配置文件之间进行通信至关重要。与基于防火墙的实现不同，网络权限切换开关可阻止应用通过操作系统或同一配置文件中其他应用提供的 API 使用网络（只要这些应用已正确标记）。

作为网络权限切换基础的标准 INTERNET 权限通过第二层强制执行和对根据每个配置文件授予/撤销权限的适当支持得到增强。

为了避免破坏与 Android 应用的兼容性，新增的权限切换开关默认处于启用状态。不过，操作系统的应用安装界面已扩展，在安装确认页面中显示该切换开关，以便用户在安装应用时将其禁用。

当网络权限被禁用时，GrapheneOS 会假装网络已关闭。它会在各种 API 中显示网络已关闭，返回网络连接问题而非权限被撤销的错误，并避免运行依赖于网络的计划任务。这使得应用程序能够像网络已关闭一样处理网络问题，而不是崩溃或显示因尝试使用网络而无法使用的错误。

### [传感器权限切换](https://grapheneos.org/features#sensors-permission-toggle)

传感器权限切换：禁止访问所有其他现有 Android 权限未涵盖的传感器（摄像头、麦克风、身体传感器、活动识别），包括加速度计、陀螺仪、指南针、气压计、温度计以及给定设备上的任何其他传感器。禁用访问权限后，应用在检查传感器值时会收到归零数据，并且不会接收事件。当应用尝试访问因权限被拒绝而受阻的传感器时，GrapheneOS 会创建一个易于禁用的通知。这使得该功能更加实用，因为用户可以判断应用是否正在尝试访问此功能。

为避免破坏与 Android 应用的兼容性，新增的权限默认启用。当应用尝试访问传感器并因被拒绝而收到归零数据时，GrapheneOS 会创建一条可轻松禁用的通知。用户可在**“设置”  > “安全和隐私”  > “更多安全和隐私”**中，将已安装应用的传感器权限设置为默认禁用。

### [存储范围](https://grapheneos.org/features#storage-scopes)

GrapheneOS 提供存储范围，作为与标准 Android 存储权限完全兼容的替代方案。用户无需授予存储权限，只需启用存储范围，即可让应用假定其已拥有所请求的所有存储权限。在 Android 上，即使应用没有任何存储权限，仍然可以创建文件和目录，并访问其创建的文件。用户可以选择将文件和目录添加为存储范围，以允许应用访问其他应用创建的文件。

有关更多详细信息，请参阅[有关存储访问的使用指南部分](https://grapheneos.org/usage#storage-access)。

### [联系范围](https://grapheneos.org/features#contact-scopes)

GrapheneOS 提供了联系人范围作为授予联系人权限的替代方案。默认情况下，它就像联系人列表为空一样，用户可以向特定联系人或联系人组授予不同类型的访问权限。

有关更多详细信息，请参阅[联系人范围的使用指南部分](https://grapheneos.org/usage#contact-scopes)。

### [广泛的运营商支持，无需侵入运营商访问](https://grapheneos.org/features#broad-carrier-support)

GrapheneOS 比 AOSP 拥有更广泛的运营商支持，并且基本与 Pixel 上的原生操作系统一致，而无需做出相同的牺牲。我们利用 CarrierConfig2 项目和脚本，将其 APN、运营商配置、彩信和可视语音邮件数据库转换为 AOSP 使用的格式。我们删除了那些需要进行网络共享、禁止禁用 2G 网络等反用户配置。我们不包含侵入式的运营商专属应用和对开放移动联盟设备管理 (OMA DM) 的支持，因此我们也删除了依赖这些应用的配置。

请参阅有关[运营商功能的使用指南部分](https://grapheneos.org/usage#carrier-functionality)以了解更多详细信息。

### [仅 LTE 模式](https://grapheneos.org/features#lte-only-mode)

[仅 LTE 模式](https://grapheneos.org/usage#lte-only-mode)通过禁用大量传统代码（2G、3G）和前沿代码（5G）来减少蜂窝无线电攻击面。

### [Wi-Fi隐私](https://grapheneos.org/features#wifi-privacy)

GrapheneOS 支持每个连接的 MAC 地址随机化，并默认启用。与现代 Android 使用的标准持久化每个网络随机 MAC 地址相比，这是一种更加私密的方法。

当使用 GrapheneOS 添加的每个连接 MAC 随机化时，DHCP 客户端状态会在重新连接到网络之前刷新，以避免显示它可能与之前是同一设备。

GrapheneOS 还修复了 Linux 内核 IPv6 隐私地址实现中的严重缺陷，使其不仅可以用作同一网络的连接标识符，还可以用作跨网络连接的标识符。我们无需将这些更改应用于 Pixel 6 及更高版本，因为此问题已在 Linux 内核上游版本中修复，但尚未反向移植到早期的内核 LTS 分支，因此我们仍需在此版本中处理。

请参阅我们的[Wi-Fi 隐私使用指南部分以获取更多一般信息，](https://grapheneos.org/usage#wifi-privacy)而不仅仅是我们对标准 Wi-Fi 隐私方法的改进。

### [网络位置](https://grapheneos.org/features#network-location)

GrapheneOS 在我们自主研发的实现中提供了基于网络的定位功能，作为一项可选功能。与 Apple 和 Google 提供的服务类似，它提供基于附近网络的位置检测，而非仅仅依赖于基于卫星的定位 (GNSS)，并结合了 A-GNSS 等技术来加速定位。这使得在室内和高楼林立的城市中获取位置信息的速度更快，甚至成为可能，而这在 GNSS 无法实现的情况下是无法实现的。某些应用程序也期望基于网络的定位可用，并且没有考虑获取基于 GNSS 的估算所需的时间或无法在所有位置获取位置，因此此功能可以提高应用程序的兼容性。

与 Google 的服务不同而与 Apple 的服务类似，我们的功能基于从服务中检索附近网络的位置数据来提供本地位置估算。它会将服务信息从上次使用时起在内存中缓存长达 15 分钟，以便在获取初始数据后可以离线运行。它只需要为想要用于位置估算的每个网络发送一个网络标识符。Google 的服务进行服务器端位置估算，这需要在每次位置估算更新时反复向服务发送每个网络的距离估算值。我们使用的方法不需要在附近网络已缓存或发送距离估算值后向服务提供任何信息。该服务还为其提供额外的数据，这些数据覆盖从初始位置开始的相当大的区域，具有合理的网络密度，因此即使互联网连接丢失，它也能继续运行。

我们基于网络的定位功能主要基于 Wi-Fi 接入点 (AP)。当 Wi-Fi 定位无法获取任何位置估计时，我们会使用手机信号塔作为备用方案。Apple 和 Google 也使用蓝牙信标，但这项功能非常小众，仅适用于某些商场、商店等，这些场所通常 Wi-Fi 覆盖范围足够广，能够提供不错的位置估计，因此我们不会优先添加对蓝牙信标的支持。

用户目前可以选择使用我们的代理访问 Apple 服务，或直接使用 Apple 服务。我们正在基于包括 Apple 服务在内的多个来源的数据构建自己的数据库和服务。与 Apple 和 Google 的服务不同，我们的服务将基于数据库下载支持完全离线使用，而无需向服务发送网络标识符来获取数据。

有关如何使用网络定位功能的详细信息，请参阅[使用部分](https://grapheneos.org/usage#network-location)。

### [私人截图](https://grapheneos.org/features#private-screenshots)

GrapheneOS 禁止在屏幕截图中包含敏感元数据。

在 Android 上，每张屏幕截图都包含一个 EXIF 软件标签，其中包含详细的操作系统版本/版本信息 ( )。该标签与**“设置”**  **>** **“关于设备”**  **>** **“版本号”**`android.os.Build.DISPLAY`中显示的值相同。这会泄露操作系统、操作系统版本，通常还会泄露设备系列/型号，因为版本特定于某个设备系列。GrapheneOS 完全禁用了此标签。

在 Android 上，每张屏幕截图还包含 EXIF 标签，其中包含本地日期、时间和时区偏移量。GrapheneOS 默认禁用此功能，以避免通过用户不可见的元数据泄露时间和准位置信息。日期和时间已包含在屏幕截图的文件名中，用户完全可见，并且可以轻松修改，无需第三方工具。GrapheneOS 在**“设置”  > “安全和隐私”  > “更多安全和隐私”**中包含一个开关，用于重新启用此元数据，因为有些用户可能会觉得它很有用。

### [封闭式设备标识符泄漏](https://grapheneos.org/features#closed-device-identifier-leaks)

GrapheneOS 修复了几个突出的设备标识符泄漏问题，绕过了 Android 避免应用无法唯一识别设备的机制。更多常规信息，请参阅我们关于[硬件标识符](https://grapheneos.org/faq#hardware-identifiers)和[非硬件标识符的常见问题解答部分。](https://grapheneos.org/faq#non-hardware-identifiers)

我们的[安全应用程序生成系统](https://grapheneos.org/usage#exec-spawning)主要是为了显著提升对漏洞利用的防护。然而，它也能提升隐私保护。在没有启用我们安全应用程序生成系统的设备上，用于 ASLR 等概率漏洞缓解措施的密钥可用作设备标识符，并持续到设备重启。这是一种轻松识别不同配置文件中应用的设备的方法。这只是该功能的一个小小优势，尽管仍然存在大量跨应用识别设备的侧信道攻击，但它修复了大多数已知的直接标识符泄漏问题。

我们还消除了阻止应用程序访问硬件标识符的几个漏洞，包括加强针对旧版 Android 平台版本的应用程序的限制。

### [默认隐私](https://grapheneos.org/features#privacy-by-default)

GrapheneOS 默认不包含或使用 Google 应用和服务，并避免包含任何与我们的隐私和安全重点不符的应用/服务。Google 应用和服务可以在 GrapheneOS 上作为常规沙盒应用使用，无需通过我们的[沙盒 Google Play](https://grapheneos.org/features#sandboxed-google-play)功能获得任何特殊访问权限或特权，但我们默认不包含这些应用，以便用户明确选择是否使用这些应用以及在哪些配置文件中使用。

我们更改了默认设置，将隐私置于小便利之上：默认情况下禁用基于收集输入历史记录的个性化键盘建议，默认情况下在锁定屏幕上隐藏敏感通知，默认情况下在输入时隐藏密码。

[我们为减少攻击面而](https://grapheneos.org/features#attack-surface-reduction)做出的一些改变还可以通过默认不暴露不必要的无线电等来默认提高隐私性，避免硬件潜在的隐私漏洞的影响。

默认情况下，我们还使用 GrapheneOS 服务器代替 Google 服务器来提供以下服务：

- 连接检查
- 证明密钥配置
- 适用于 Broadcom 和 Qualcomm (XTRA) 的 GNSS 年历下载 (PSDS)
- 安全用户平面定位 (SUPL)
- 网络时间
- 钒（铬）成分更新

我们提供了一个切换开关，用于切换回 Google 服务器进行连接检查、认证密钥配置和 GNSS 星历下载，并添加了禁用网络时间连接的适当支持。此功能与其他切换开关结合使用，可使 GrapheneOS 设备看起来像是 AOSP 设备。此功能仅对连接检查尤为重要，因为其他连接需要通过 VPN 进行路由，而 VPN 实际上是在本地网络中进行融合所必需的。

除了改进 SUPL 隐私功能外，我们还默认将 SUPL 服务器覆盖为我们的代理。我们还添加了一个开关，方便用户切换到其运营商的标准 SUPL 服务器（通常是 supl.google.com）或完全禁用它。

请参阅我们的[默认连接常见问题解答条目以获取更多详细信息](https://grapheneos.org/faq#default-connections)。

### [PIN 码扰码](https://grapheneos.org/features#pin-scrambling)

GrapheneOS 添加了启用 PIN 码加密的开关，以提高因物理距离或侧信道攻击而破解用户输入 PIN 码的难度。PIN 码加密功能适用于锁屏和 SIM 卡 PIN/PUK 码。

### [双因素指纹解锁](https://grapheneos.org/features#two-factor-fingerprint-unlock)

GrapheneOS 新增了在锁屏指纹成功验证后，需要输入第二重 PIN 码才能完成设备解锁的选项。由于 Android/iOS 系统为了方便起见，使用生物识别解锁作为辅助解锁机制，因此用户可以使用强密码作为主要解锁方式，同时使用指纹和短 PIN 码进行辅助解锁。如果 PIN 码输入错误，则计入标准尝试次数限制。

### [支持更长的密码](https://grapheneos.org/features#supports-longer-passwords)

GrapheneOS 支持默认设置更长的密码：128 个字符，而不是 16 个字符。这样就无需使用设备管理器来启用此功能。

如果用户不想依赖安全元件的安全性，此功能允许用户使用骰子密码，该安全元件提供了非常积极的限制，即使对于随机的 6 位 PIN 也能提供高级别的安全性。

### [自动重启](https://grapheneos.org/features#auto-reboot)

GrapheneOS 提供自动重启功能，可在设定的时间段后重启锁定的设备，以恢复数据。每次设备锁定时都会启动倒计时器，如果在计时器归零之前未成功解锁，设备将重启。解锁任何配置文件都会取消计时器，而不仅仅是所有者配置文件。

计时器默认设置为 18 小时，但可以设置为 10 分钟到 72 小时之间的值，或者关闭。

当设备处于“首次解锁前”状态时，此功能不适用，这意味着它不会导致设备不断重启，因为数据已经处于静止状态。

该功能在 init 进程中实现，防止它通过系统进程崩溃而被绕过，因为 init 崩溃会导致内核崩溃，从而导致重新启动。

### [清除内存中的敏感数据](https://grapheneos.org/features#clearing-sensitive-data-from-memory)

[正如我们在有关添加的漏洞缓解措施](https://grapheneos.org/features#exploit-mitigations)的部分中所述，GrapheneOS 为标准用户空间和内核分配器添加了将释放的内存归零的功能。除了防御漏洞之外，这些功能还有第二个好处，那就是尽快从内存中清除敏感数据。Android 会定期压缩冻结的缓存应用程序和当前在后台运行的应用程序，方法是触发完整的压缩垃圾收集 (GC)，然后请求 malloc 释放尽可能多的内存返回给操作系统。这与归零功能完美结合，使得 Java/Kotlin 以及它们使用的 C、C++ 和 Rust 库可以更快地清除释放的数据，在这些库中，低级分配器会一直保留，直到高级对象被释放。

当设备锁定时，我们会触发 SystemUI 和 system_server 进程的完全压缩垃圾回收 (GC)，将所有不再使用的内存释放回操作系统。由于 GrapheneOS 启用了内核页面分配器清零功能，这会导致对象中所有不再引用的数据被清除。我们的方法基于 Android 的标准方法，即在设备解锁后对这两个进程运行完全压缩的 GC，以清除用户 PIN/密码及其派生密钥的残留。这是一种在锁定后立即清除部分数据的好方法，之后我们的[自动重启](https://grapheneos.org/features#auto-reboot)功能才会启动，清除所有操作系统内存。

GrapheneOS 修改了设备重启的一些方式，以继续正常的重启过程，其中内存由 GrapheneOS 启用的内核页面和 slab 分配器归零功能释放和清除。

### [胁迫 PIN/密码](https://grapheneos.org/features#duress)

GrapheneOS 为用户提供了设置胁迫 PIN/密码的功能，一旦进入任何需要设备凭证的地方（在锁屏上，以及操作系统中的任何此类提示），该 PIN/密码将不可逆地擦除设备（以及任何已安装的 eSIM）。

擦除操作无需重启，也无法中断。您可以在机主配置文件中的**“设置”  > “安全和隐私”  > “设备解锁”  > “胁迫密码”**中进行设置。胁迫 PIN 码仅用于输入 PIN 码，胁迫密码仅用于输入密码。胁迫 PIN 码和密码均为必填项，以便启用此功能，以适应可能具有不同解锁方法的不同配置文件。当胁迫 PIN 码作为[双因素指纹解锁 PIN 码](https://grapheneos.org/features#two-factor-fingerprint-unlock)输入时，设备也会被擦除，但目前作为 SIM 卡 PIN 码输入时不会擦除。

请注意，如果胁迫 PIN/密码与实际解锁方法相同，则实际解锁方法始终优先，因此不会发生擦除。

### [指纹解锁更安全](https://grapheneos.org/features#more-secure-fingerprint-unlock)

GrapheneOS 提高了指纹解锁功能的安全性，它只允许总共 5 次尝试，而不是在总共 20 次尝试的情况下，每 5 次失败之间设置 30 秒的延迟。这不仅减少了潜在的尝试次数，而且还可以通过故意用不同的手指解锁 5 次失败来轻松禁用指纹解锁。

GrapheneOS 还增加了仅使用指纹扫描仪进行应用程序身份验证的支持，并通过关闭解锁支持来解锁硬件密钥库密钥。此功能已存在于 Android 标准人脸解锁功能中。

### [改进的用户配置文件](https://grapheneos.org/features#improved-user-profiles)

Android 的用户配置文件是独立的工作区，拥有各自的应用实例、应用数据和配置文件数据（联系人、媒体商店、主目录等）。应用无法访问其他用户配置文件中的应用，并且只能与同一用户配置文件中的应用进行通信（需与其他应用相互同意）。每个用户配置文件都拥有基于其锁定方法的加密密钥。这些配置文件非常适合 GrapheneOS，但仍有很大的改进空间。

GrapheneOS 对用户配置文件功能进行了改进，并正在进一步改进，以使它们之间的切换和监控其他配置文件更加方便。

#### [更多用户资料](https://grapheneos.org/features#more-user-profiles)

GrapheneOS 将二级用户配置文件的数量限制从 4 个（3 个 + 来宾）提高到 32 个（31 个 + 来宾），以使此功能更加灵活。

#### [结束会话](https://grapheneos.org/features#end-session)

GrapheneOS 还支持注销用户配置文件，无需设备管理器控制设备即可使用此功能。注销会使配置文件处于非活动状态，因此其中安装的任何应用程序都无法运行。它还会从内存和硬件寄存器中清除磁盘加密密钥，使用户配置文件恢复到静止状态。

#### [禁用应用程序安装](https://grapheneos.org/features#disabling-app-installation)

GrapheneOS 在用户管理设置中添加了一个开关，用于禁用辅助用户应用的安装。您可以安装希望辅助用户使用的应用，然后在所有者配置文件中禁用以该用户身份安装更多应用的功能。Android 支持此功能作为标准设备管理功能，但不支持拥有自己设备的用户使用。

#### [改进了安装可用应用程序](https://grapheneos.org/features#install-available-apps)

GrapheneOS 启用了标准安装可用应用功能，该功能在 AOSP 或原生 Pixel OS 中尚未启用，允许所有者用户安装其他用户可用的软件包。这允许在次要用户中安装已在所有者用户中安装的应用，而无需再次下载。这对于使用新增的禁用次要用户安装应用的开关非常有帮助。

#### [通知转发](https://grapheneos.org/features#notification-forwarding)

GrapheneOS 支持将后台运行用户的通知转发给当前活跃用户。默认情况下，将通知转发给其他用户是禁用的，但可以在每个需要转发到当前活跃用户配置文件的用户配置文件中启用此功能。从其他配置文件转发的通知默认显示在标准的本地通知频道中。

### [GrapheneOS 应用程序存储库](https://grapheneos.org/features#grapheneos-app-repository)

GrapheneOS 包含我们自主研发的、注重安全性、极简主义和易用性的应用仓库客户端，用于使用我们的第一方应用仓库。我们的应用仓库目前用于分发我们自己的应用，以及 Google Play 的镜像，用于沙盒化的 Google Play 功能。未来，它将用于分发基于外部开发的开源应用的第一方 GrapheneOS 版本，并进行强化。

### [Vanadium：强化的 WebView 和默认浏览器](https://grapheneos.org/features#vanadium)

GrapheneOS 包含我们的 Vanadium 浏览器，作为操作系统提供的 WebView 实现和默认浏览器。Vanadium 是 Chromium 的强化版本，提供增强的隐私和安全性，类似于 GrapheneOS 与 AOSP 的比较。Vanadium 浏览器目前尚未添加太多功能，但长期来看，我们计划进行大量增强。

与标准移动版 Chromium 相比，新增的一些功能：

- 为主分配器启用硬件内存标记 (MTE)
- 基于类型的控制流完整性 (CFI)
- 强力堆栈保护器
- 自动零初始化变量
- 明确定义的有符号溢出
- 严格的站点隔离和沙盒 iframe
- JavaScript JIT 默认禁用，每个站点可通过下拉权限菜单进行切换
- 作为 seccomp-bpf 沙盒的扩展，未启用 JavaScript JIT 的进程会阻止动态代码执行
- 原生 Android 自动填充实现，避免需要沙盒 Google Play 来支持自动填充
- 原生 Android 凭证管理器支持密钥，避免需要沙盒 Google Play 来支持密钥
- 禁用 WebGPU 以减少攻击面
- WebRTC IP 处理策略切换以控制点对点 WebRTC 模式
- 使用 EasyList + EasyPrivacy 的高性能内容过滤引擎，通过下拉权限菜单进行每个站点的切换
- 更完整的状态划分，无需选择退出原产地审判
- 提前为 WebView 启用标准 Android 16 用户代理缩减，以使用标准占位符值替换主要操作系统版本、设备型号和浏览器次要/构建/补丁版本
- 高熵客户端提示被替换为 Chromium 精简用户代理中用于浏览器和 WebView 的标准占位符值，以堵住漏洞，即 Chromium 仍然与任何通过客户端提示请求的服务器共享主要操作系统版本、设备型号和浏览器次要/构建/补丁版本
- 电池 API 始终显示电池正在充电且容量为 100%
- 禁用琐碎子域名隐藏
- 无需使用功能标志和基于种子的试用，即可在用户之间实现一致的浏览器行为
- 几乎所有远程服务都默认禁用或移除。默认仅连接到 GrapheneOS 服务器。默认服务仅有 2 个：组件更新（例如证书颁发机构和证书吊销更新）以及启用后的 DNS-over-HTTPS 连接检查
- 网络搜索和全局搜索意图取代了对操作系统搜索应用程序的需求
- 可选择在隐身模式下始终打开来自其他应用、自定义标签、搜索意图和共享意图的链接
- 减少或禁用在打开链接时发送跨源引用信息共享的选项
- 默认启用混合后量子加密，以匹配桌面版 Chromium 的行为，因为我们支持的设备速度足够快

更好的默认设置，包括非面向用户的标志：

- 默认减少 Accept-Language 标头（仅通过 chrome://flags 可用）
- 默认禁用第三方 Cookie
- 默认禁用支付支持
- 网站后台同步默认禁用
- 默认情况下禁用传感器访问
- 受保护媒体 (DRM) 默认禁用
- 超链接审核默认禁用
- 默认启用“不跟踪”，主要是为了避免用户通过启用该功能来区分自己和其他人，因为它没有实际价值
- WebRTC IP 处理策略默认设置为最私密值，而不是最不私密值（由 Vanadium 转变为面向用户的选项）

影响兼容性的功能（例如内容过滤）通常需要提供切换开关，但这些功能通常仅适用于浏览器本身，而不适用于 WebView 库。用户安装的应用中的 WebView 默认启用 JavaScript JIT，可以使用全局切换开关将默认设置更改为禁用，也可以使用每个应用的切换开关覆盖默认设置。

由于与站点隔离和反指纹识别功能存在冲突，因此不计划提供扩展支持。我们计划在浏览器中实现更多功能，重点关注隐私和安全改进，这些改进可以默认启用，而不是选择启用。改进通常将基于每个站点选择停用，而不是选择启用，以默认提供隐私和安全功能，并避免用户通过选择启用隐私和安全功能而更容易被识别。默认禁用的 JS JIT 和默认启用的内容过滤是我们计划扩展的这种方法的早期示例。

我们计划添加更多与减少攻击面相关的站点设置切换开关，例如 WebGL、WebGPU、WebRTC 和其他通常始终启用的功能的站点设置切换开关。这将有助于提高安全性并增强对指纹识别的防御能力。

反指纹识别依赖于拥有庞大的用户群，这些用户群使用相同的浏览器、扩展程序、内容过滤器和其他面向 Web 的配置。一旦 Vanadium 拥有更多功能，它将在 GrapheneOS 之外提供，以扩大用户群。我们减少攻击面的方法除了消除漏洞攻击面外，还消除了指纹识别方法，这将是我们通过首先不公开 WebGL、WebGPU 和 WebRTC 等功能来防止指纹识别的关键部分。良好的默认设置以及避免用户更改面向 Web 的配置是其中的重要部分。内容过滤器将保持用户标准，并作为 Vanadium 配置应用程序的一部分一起更新。我们将通过基于浏览器语言配置启用以语言为中心的过滤器来满足这些需求。一旦 Vanadium 在 GrapheneOS 之外可用，基于硬件差异的指纹识别将变得更加重要，因为 GrapheneOS 始终支持一小部分高度安全的设备。

状态分区仍需完全实现。剩下的主要障碍是提供完整的 Cookie 分区。具有此功能的主流浏览器依赖于启发式算法来绕过 Cookie 分区，而这种算法很容易被滥用来绕过该功能。我们尝试默认部署完整的 Cookie 分区，但不得不回滚，并且需要考虑如何处理这个问题，尤其是在我们的目标是让大多数 Vanadium 用户使用几乎相同的配置的情况下。

我们计划在未来迁移到更强大的内容引擎，支持更高级的过滤规则和美化过滤。标准过滤器的扩展取决于是否支持 uBlock Origin、AdGuard 和其他过滤器所使用的扩展程序。

目前，大多数浏览器数据不包含在操作系统备份中，一旦 GrapheneOS 包含更好的备份服务，这种情况可能会有所改变。此外，还计划支持书签的导出/导入以及类似的数据导出/导入功能。除了操作系统备份服务支持之外的同步功能，最终将提供每个应用的备份和恢复功能，包括跨设备和通过同步服务进行备份和恢复，目前尚未计划。

更多信息请参阅[我们的使用指南的网页浏览部分](https://grapheneos.org/usage#web-browsing)。

### [审计员应用程序和鉴证服务](https://grapheneos.org/features#auditor)

我们的[审计应用程序](https://github.com/GrapheneOS/Auditor/releases)和[认证服务](https://attestation.app/)提供基于硬件的强大验证，以验证设备上固件/软件的真实性和完整性。我们采用基于配对的强方法，该方法还会根据每次配对生成的硬件支持密钥来验证设备的身份。软件检查位于顶层，并通过与硬件建立安全的信任链。更多详情，请参阅“[关于”](https://attestation.app/about)和[“教程”](https://attestation.app/tutorial)页面。

### [GrapheneOS相机](https://grapheneos.org/features#grapheneos-camera)

[GrapheneOS 相机](https://grapheneos.org/usage#grapheneos-camera-app)是一款现代化的相机应用，拥有出色的用户界面，并注重隐私和安全。更多详情，请参阅[我们使用指南的相机部分](https://grapheneos.org/usage#camera)。

### [GrapheneOS PDF 查看器](https://grapheneos.org/features#grapheneos-pdf-viewer)

[GrapheneOS PDF Viewer](https://github.com/GrapheneOS/PdfViewer)是一个沙盒化的、强化的 PDF 查看器，使用 HiDPI 渲染，具有捏合缩放、文本选择、查看加密 PDF 等功能。

### [安装向导](https://grapheneos.org/features#setup-wizard)

我们有自己的设置向导，用于设备的初始设置和用户配置文件。它与原生 Pixel OS 中的设置向导非常相似，但更注重安全性。它会在设备启动时检测到未解锁的引导加载程序，并通过一个按钮警告用户，该按钮用于重新启动至快速启动模式以锁定设备。跳过警告需要等待一个计时器，以防止快速跳过警告而错过重要信息。我们的设置向导还会在设置过程结束时默认禁用 OEM 解锁，并提供一个开关来选择退出禁用，这虽然略微有效，但可以减少攻击面。我们计划在设置向导中加入对锁定方法选项的改进，包括双因素指纹身份验证以及自动生成随机骰子密码和 PIN。

### [加密备份](https://grapheneos.org/features#encrypted-backups)

通过集成[Seedvault 应用程序](https://github.com/GrapheneOS/platform_external_seedvault)进行加密备份，支持本地备份和任何带有存储提供商应用程序的云存储提供商。

Seedvault 是由 GrapheneOS 社区成员创建的，旨在纳入我们的操作系统。由于该项目已被另一群与我们目标或方法不同的人接管，我们计划用新的实现来替换它。目前，这是最佳选择，因此我们将其纳入，以便为用户提供加密备份支持。我们已修复了多项安全问题，以解决该项目的上游问题。

### [位置数据访问指示器](https://grapheneos.org/features#location-data-access-indicator)

除了标准的 Android 摄像头和麦克风指示器外，GrapheneOS 还启用了位置数据访问隐私指示器。当用户授权访问位置信息的应用请求位置数据时，该指示器会显示。我们还解决了此功能目前在 AOSP 中存在的各种用户体验问题，使其达到高度可用的状态。

Android 13 提供了位置隐私指示器作为开发者选项，但其工作方式与 GrapheneOS 不同。GrapheneOS 会为所有通过 API 访问的位置数据显示位置隐私指示器。通常情况下，原生操作系统仅在 GNSS 位置请求（也称为高功率位置请求）中显示位置隐私指示器，而通常不会在网络位置请求和其他受位置权限/全局阻止开关控制的 API 中显示位置隐私指示器。

该指示器的工作方式与摄像头和麦克风指示器相同，当位置访问发生时，会显示一个亮绿色图标；当快速设置托盘当前未打开时，该图标会最小化为一个亮绿色的​​小点。Android 12 已在隐私仪表板中包含位置权限以及其他标准运行时权限，用于查看历史记录。

### [可以禁用用户安装的应用程序](https://grapheneos.org/features#user-installed-apps-can-be-disabled)

GrapheneOS 新增了禁用用户安装应用的功能，而不再仅限于禁用系统应用。这使得用户可以完全阻止已安装的某个应用运行，而无需强制卸载该应用并丢失应用数据。这项功能比标准的强制停止功能更为严格，后者只能阻止应用自行启动，一旦其他应用尝试打开其提供的活动或服务，该应用就会重新启动。

### [改进了 VPN 泄漏阻止功能](https://grapheneos.org/features#improved-vpn-leak-blocking)

GrapheneOS 极大地提高了 Android 对 VPN 泄漏的保护，包括内置 VPN 支持和启用标准“阻止不使用 VPN 的连接”切换的 VPN 应用程序。

当 VPN 应用因竞争条件而宕机时，Android 允许来自系统解析器的 DNS 查询泄漏到网络提供的 DNS 服务器。同样，它还允许在 VPN 隧道之外连接 VPN DNS 服务器。GrapheneOS 通过将泄漏阻止功能扩展到系统解析器的这一部分，完全阻止了这两种情况，从而完全防止了单播 DNS 泄漏。

无论 VPN 是否处于连接状态，Android 都允许包括应用在内的进程完全绕过 VPN，方法是直接发送多播数据包，或通过标准多播组管理系统调用让内核代为发送数据包。GrapheneOS 扩展了 Android 的标准 eBPF 过滤功能，全面支持阻止所有形式的多播数据包绕过。此外，在启用 VPN 锁定的情况下，我们还禁止使用系统网络服务发现管理器 (NSD) 连接到基于 mDNS 的服务。

Android VPN 配置针对每个配置文件单独设置，这意味着工作配置文件、私人空间和次要用户都有各自的 VPN 配置，这是一个非常实用的隐私功能。Android 有一个标准限制，禁止进程使用当前配置文件无法访问的网络。然而，这并没有考虑到多播数据包，而且可以通过属于不同配置文件的 VPN 隧道发送多播数据包。GrapheneOS 通过在标准 netfilter 配置中添加多播防火墙来解决这个问题，该防火墙可以防止进程通过无法访问的 VPN 隧道发送数据包。

GrapheneOS 修补了 Android 基于 eBPF 的防火墙系统中的一个漏洞，该漏洞可以通过使用特殊系统调用指定特定接口来绕过 VPN。

查找和解决所有形式的 VPN 泄漏是我们目前的首要任务之一，由于我们发现了不太严重的其他问题，我们目前不认为这是一个完整的功能。

### [日志查看器和面向用户的崩溃报告](https://grapheneos.org/features#log-viewer-and-crash-reporting)

GrapheneOS 在 Android 标准内存日志系统的“设置”应用中添加了一个面向用户的日志查看器。该功能可替代自动崩溃报告功能（出于隐私原因，GrapheneOS 并未实现该功能）。用户可以自行控制捕获和共享的内容。我们的日志查看器支持根据日志级别、日志缓冲区和文本搜索过滤输出。用户可以将当前显示的日志复制、共享或保存到文件中。还可以添加描述来记录捕获日志的原因。

**您可以在“设置”  > “系统”  > “查看日志”**中访问整体系统日志。您可以在**“设置”  > “应用”  > “应用名称”  > “查看日志”**中访问每个应用的日志。

我们实现了与操作系统和应用崩溃日志查看器绑定的面向用户的崩溃报告功能，从而显著改进了 Android 中目前非常有限的面向用户的崩溃报告功能。这可以帮助用户向操作系统或应用开发者报告崩溃，而无需使用侵入式的自动崩溃报告机制，因为用户无法控制发送给开发者的数据。

我们面向用户的崩溃报告功能特别支持 hardened_malloc 捕获的内存损坏，并支持硬件内存标记，告知用户检测到了内存损坏。如果用户认为这不是漏洞利用，而是需要解决的应用错误，他们可以自行选择如何继续操作，以及是否需要启用应用的兼容性开关。我们需要在不鼓励用户禁用保护用户安装应用免受漏洞利用的安全功能与轻松解决应用错误之间取得平衡。我们不允许为基础操作系统（包括基础操作系统应用）禁用这些漏洞利用保护功能，但太多用户安装的应用存在潜在的内存损坏错误，我们需要提供解决这些问题的选项。

用户可以通过**“设置”  > “安全与隐私”  > “更多安全与隐私”  > “系统进程崩溃通知”**启用更多系统崩溃报告功能。由于我们无法对导致崩溃的每一个 Android 操作系统错误进行分类和调查，因此默认情况下我们不会启用所有内核或系统进程崩溃的报告功能。我们专注于通过硬件内存标记捕获的内存损坏崩溃，因此这些崩溃始终会被报告。我们无法指望自己修复所有 Android 错误，因此我们将资源集中在改进过程中发现的、更有可能成为安全错误的错误上。

### [其他功能](https://grapheneos.org/features#other-features)

这是其他 GrapheneOS 功能的不完整列表。

- 每个配置文件的加密文件名填充长度已从 16 字节增加到 32 字节，以减少因文件名长度而泄露的信息。有关现代 Android 和 GrapheneOS 使用的[基于文件系统的全盘加密的](https://grapheneos.org/faq#encryption)更多信息，请参阅常见问题解答部分。
- 通过版本和配置验证以及报告不一致情况和启用调试功能，提高了用户对持久固件安全性的可见性。
- 通过第一方服务器对网络时间更新进行经过身份验证的加密，以防止攻击者更改时间并基于绕过证书/密钥过期等方式发起攻击。
- 适当支持禁用网络时间更新，而不仅仅是不使用结果
- 强化本地构建/签名基础设施
- [无缝自动操作系统更新系统](https://grapheneos.org/usage#updates)可在后台运行且不会中断设备使用，并且完全支持在更新操作系统首次启动失败时进行标准自动回滚
- 需要解锁才能通过快捷磁贴访问敏感功能
- [最小化捆绑应用和服务](https://grapheneos.org/faq#bundled-apps)。仅集成必要的应用到操作系统中。我们不会与应用和服务合作，将其捆绑到操作系统中。一款应用今天可能是最佳选择，但未来可能就很糟糕，反之亦然。我们的方法是在初始设置时推荐某些应用，而不是将它们硬编码到操作系统中。
- 无线警报完全是可选的，因为 GrapheneOS 增加了一个开关，用于切换原本强制启用的总统警报类型。这在加拿大尤其有用，因为加拿大政府滥用系统，将各种警报都当作总统警报发送，以阻止用户选择不接收天气和安珀警报。
- 删除 TrustCor 根证书颁发机构作为受信任的系统 CA。
- 默认安全的 Android 12 PendingIntent 安全检查（FLAG_IMMUTABLE）而不是默认崩溃，提高了旧应用程序的兼容性和安全性。
- 修复了官方发布版本中启用 UART 调试的警告。
- 工程/原型（“EVT”、“PVT”或“DVT”）设备警告，因为这些设备通常对开发的安全控制比较宽松，主要是未将安全启动状态属性`ro.boot.secure_boot`设置为`PRODUCTION`。
- 启用引导加载程序、无线电和引导分区版本/指纹检查。
- 删除自动向系统浏览器授予位置权限的代码。
- 没有任何存储权限的应用无法读取所有用户创建的目录列表（Android 系统允许读取）。在 Android 和 GrapheneOS 系统中，此类应用无法查看文件列表。
- **可以使用“设置”**  **>** **“声音和振动”**中的**“点击并单击声音”**选项来切换屏幕截图快门声音，同时仍然遵循将设备置于振动/静音模式的标准方法以关闭屏幕截图快门声音。
- 通过将系统时钟更新阈值从 2000 毫秒降低到 50 毫秒，并将系统时钟漂移警告从 2000 毫秒降低到 250 毫秒，实现更精确的系统时钟。这对于基于时间的协议（例如 TOTP）非常有用。
- 拨号器应用程序中的通话录音功能使用现代 Android 存储，录音存储在录音/通话录音中，并且不受地区或播放录音音等特殊情况的限制（用户仍有责任遵守当地法律）。
- 将标准 Android 软件包安装程序行为更改为在更新软件包后保留被禁用的软件包，而不是重新启用它们。
- 默认启用 VPN 的“始终开启 VPN”和“阻止没有 VPN 的连接”切换。
- 权限提示和 Android 调试桥 USB 授权提示的允许操作默认处于禁用状态，延迟 1 秒后才会生效。这可以防止意外按下，尤其是在应用可能诱骗用户按下按钮并弹出系统对话框的情况下。

## [服务](https://grapheneos.org/features#services)

服务基础设施特点：

- 对我们的基础设施实施严格的隐私和安全措施
- 避免不必要的日志记录，并在 4 天（操作系统使用的网络服务）至 10 天后自动清除日志
- 服务完全通过我们自己的专用服务器和 OVH 虚拟机（以及用于镜像的 BuyVM）托管，无需任何额外的 CDN、SaaS 平台、镜像或其他服务方
- 我们的服务采用开放技术栈构建，以避免被锁定在任何特定的托管服务提供商或供应商
- 开放我们基础设施的文档，包括列出我们所有的服务、进行类似设置的指南、为我们的每个 Web 服务发布的配置等。
- 无专有服务
- 我们所有服务均采用经过认证的加密
- 我们所有服务（SSH、TLS 等）均采用强密码配置，且仅使用现代 AEAD 密码提供前向保密性
- 我们的网站不包含任何第三方内容，并通过严格的内容安全策略规则完全禁止此类内容
- 我们的网站禁用引荐来源标头以最大程度地保护隐私
- 我们的网站完全启用跨源隔离并禁用嵌入其他内容
- [为我们所有的域实施DNSSEC](https://internet.nl/faqs/dnssec/)，为域/服务器配置的加密和身份验证提供信任根
- 我们所有域名的 DNS 证书颁发机构授权 (CAA) 记录仅允许 Let's Encrypt 颁发证书，并提供完全集成的支持，`accounturi`并将`validationmethods`我们的 Let's Encrypt 帐户固定为唯一允许颁发证书的帐户
- DANE TLSA 记录用于固定我们所有 TLS 服务的密钥
- 我们的邮件服务器强制使用 DNSSEC/DANE 来提供经过身份验证的加密，以发送邮件（包括来自认证服务的警报消息）
- 跨所有域的 SSHFP 用于固定 SSH 密钥
- 在 Auditor 等应用程序中为我们的服务提供静态密钥固定
- 除了登录会话之外，没有持久性 cookie 或类似的客户端状态，这些会话是使用、、`SameSite=Strict`和标志安全设置的，前缀为和具有服务器端会话跟踪功能，可以注销其他会话`Secure``HttpOnly``Path=/``__Host`
- 基于 scrypt 的密码哈希算法（当可用的实现更加成熟时，可能是 Argon2）

## [项目](https://grapheneos.org/features#project)

除了操作系统的技术特性之外：

- 具有[非常活跃的社区](https://grapheneos.org/contact#community)和贡献者的协作[开源项目](https://grapheneos.org/source)[](https://grapheneos.org/contact#community)
- 您可以自行构建并进行所需的更改，因此您不会被上游项目做出的决定所束缚
- 非营利项目通过与商业化保持距离来避免利益冲突。项目由企业支持，[而非项目服务于特定企业的需求。](https://grapheneos.org/faq#company)
- [](https://grapheneos.org/faq#privacy-policy)我们的所有软件和服务均采用[严格的隐私政策](https://grapheneos.org/faq#privacy-policy)
- [团队有良好的记录，](https://grapheneos.org/history/)敢于抵制损害项目完整性并将其置于个人利益之上的企图

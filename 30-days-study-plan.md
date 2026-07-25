---
title: 雲端網路與資安工程師課程｜30 天預習完整學習手冊
aliases:
  - 雲端網路資安預習
  - 9月14日開課預習
tags:
  - networking
  - linux
  - vmware
  - windows-server
  - security
  - devops
  - aws
status: planned
course_start: 2026-09-14
daily_limit: 3 hours
budget: TWD 0-500
---

# 雲端網路與資安工程師課程｜30 天預習完整學習手冊

> 執行方式：依 Day 01～Day 30 順序進行，不綁定日曆日期  
> 正式開課：2026-09-14  
> 每日上限：3 小時  
> 學習比例：約 90 分鐘理論＋90 分鐘實作  
> 起點：以完全零基礎設計；遇到已會內容視為複習  
> AWS 比例：只在相關章節補充，不另設大量 AWS 課程  
> 暫定職涯主線：AWS 雲端架構師  
> 預算：本計畫必要教材與軟體皆可免費完成，預計花費 NT$0

---

## 0. 本手冊的定位

這不是一個月考完 CCNA、LPIC、Security+ 或 AWS 證照的衝刺表，也不是把 498 小時正式課程壓縮成 90 小時。

本手冊只有一個主要目標：

> 讓你在 9 月 14 日正式上課時，已經理解最常造成卡關的底層概念，能跟上老師的速度，並知道自己不懂的問題該如何定位。

課程內容依使用者提供的《雲端網路與資安工程師就業養成班（第 5 梯次）》簡章重新分組。正式課綱包含區域網路、Cisco 路由交換、Windows Server、AD、Linux、Git／Ansible、VMware、Azure、資訊安全與整合專題。本手冊不僵硬照講師章節順序，而把具有相依關係的內容放在一起。

### 完成後應具備的可驗證成果

- 能從 OSI／TCP-IP、ARP、IP、Route、DNS、Port、Service 分層定位基本故障。
- 能在 Packet Tracer 建立 VLAN、Trunk、Static Route、DHCP、NAT、ACL 基礎拓樸。
- 能建立 Ubuntu Server VM，管理檔案、權限、Process、Service、Log、SSH 與 Firewall。
- 能說明 VMware 虛擬化、NAT／Bridged／Host-only 與 Snapshot。
- 能理解 Windows Server、DNS、DHCP、AD／GPO 的基本目的。
- 能用 Git 保存實驗，並用 Ansible 完成一次可重複部署。
- 能完成一個小型企業混合架構專題，留下設計、驗證與 Debug 紀錄。
- 能用實作 Memo 初步判斷自己對 AWS 架構、DevOps、SRE、SI、MIS 哪些工作內容較有興趣。

---

## 1. AWS 證照與「沒有實務經驗」的現實定位

### 先修正正式名稱

- **AWS Certified Solutions Architect – Associate：SAA-C03**
- **AWS Certified Solutions Architect – Professional：SAP-C02**
- AWS 沒有名為「SAA Pro」的正式證照；口語上可能把 Solutions Architect Professional 混稱成 SAA Pro。

### 證照是否完全沒用？

不是。證照可以：

- 證明你讀過一套範圍。
- 幫助履歷通過部分關鍵字篩選。
- 增加初階 Cloud Support、Cloud Engineer、SI 雲端職位願意面試你的機會。

但證照不能單獨證明你能：

- 從模糊需求整理架構。
- 判斷成本、可用性、安全與維運取捨。
- 建置、除錯、回復與交接。
- 面對事故或客戶問題。

AWS 官方對 SAP-C02 的目標考生描述為：具有 **2 年以上使用 AWS 服務設計與實作雲端解決方案的經驗**。這是建議的目標經驗，不是報考時要提交年資證明的強制門檻；但它也說明 Professional 證照的題目假設你已見過複雜情境。

因此不能斷言「完全沒有公司會用」，但較合理的預期是：

> 沒有實務經驗的人，即使先拿到 SAP-C02，也較可能先從 Cloud Support、Junior Cloud Engineer、SI／MSP 雲端工程師、System Engineer 或 DevOps 初階工作累積交付經驗，而不是直接以能獨立負責大型架構的資深 AWS Architect 身分入職。

本月的 GitHub Lab、Troubleshooting Report 與整合專題，就是把「只有考試知識」開始轉成「可檢查的實作證據」。

---

## 2. 職務地圖：先知道各職位大致在解決什麼問題

| 職位 | 主要解決的問題 | 常見技能 | 與輪班／on-call 的關係 |
|---|---|---|---|
| AWS Solutions Architect / Cloud Architect | 把業務需求轉成安全、可靠、可擴充、成本合理的雲端架構 | 網路、Linux/Windows、IAM、安全、HA/DR、資料庫、成本、文件與溝通 | 顧問／專案型不一定輪班；重大上線或事故可能支援。職缺差異很大 |
| Cloud Engineer | 建置與維護實際雲端資源 | VPC、EC2、IAM、監控、IaC、Linux、網路 | 可能有 on-call；是否輪班依團隊 |
| DevOps Engineer | 提升軟體從開發、測試到部署與維運的速度、穩定性與可重複性 | Git、CI/CD、Linux、容器、IaC、Cloud、監控、Script | 生產系統常有 on-call；不等於一定 24/7 輪班 |
| SRE | 把維運問題當成軟體與可靠性工程問題，管理可用性、延遲、容量與事故 | Coding、Linux、Cloud、Observability、SLO、Incident、Automation | on-call 很常見；成熟團隊多為排班待命，不等於三班制，但必須逐職缺確認 |
| SI 系統整合工程師 | 為不同客戶規劃、安裝、遷移、整合與維護多家產品 | 網路、Server、VMware、Storage、Security、文件、客戶溝通 | 常需到客戶現場；可能專案加班或 on-call。長期駐點與輪班要另問 |
| MIS / Internal IT | 維持單一公司的員工電腦、帳號、AD、網路、伺服器、備份與供應商服務 | Windows、AD、網路、端點、資產、Help Desk、基本資安 | 多數為日班，但單人 MIS 可能隨時被找；輪班、駐點通常依產業與規模 |
| Network / Security Engineer | 建置與維護 Switch、Router、Firewall、VPN、WAF、ADC 等 | CCNA、Routing、Switching、Firewall、Packet、Security | 專案、維護合約可能 on-call；SOC／NOC 類職缺較可能輪班 |

### 你的工作型態篩選條件

目前手冊採用以下條件，不替你推測其他動機：

1. 有發展性。
2. 工作包含分析、規劃與動腦。
3. 可以接受遠端 on-call。
4. 不希望是輪班工作。
5. 駐點與客戶現場需要在面試逐項確認；目前最重要的排除條件是輪班。

### 面試時直接問的六個問題

1. 這個職缺是固定日班，還是需要 24/7 輪班？
2. on-call 多久輪一次？可否遠端？平均每月實際被叫醒幾次？
3. on-call 是否有津貼、加班費或補休？事故後隔日如何安排？
4. 是否長期駐點？還是只在建置、維護、故障時到客戶現場？
5. 工作時間中，專案規劃／建置、例行維護、工單客服各約占多少？
6. 公有雲、VMware／機房、網路資安各占多少？一年後希望新人能獨立做什麼？

---

## 3. 工程師職稱與技能對照

| 英文職稱 | 主要工作內容 | 本手冊相關技能 | 工作型態提醒 |
|---|---|---|---|
| Network Engineer | 規劃與維護 LAN、WAN、VPN、Wi-Fi、Router、Switch、Firewall | OSI、Subnetting、VLAN、STP、Routing、ACL、Wireshark | ISP、企業、SI 的技術深度與責任範圍差異很大 |
| NOC Engineer | 持續監控網路與服務、初步排障、升級通報 | Routing、監控、告警、Linux 基礎、Incident | 24/7 服務環境常輪班，但不是所有 NOC 都一定輪班 |
| System Administrator | 管理 Windows/Linux Server、AD、DNS、DHCP、備份、虛擬化 | Windows Server、AD、Linux、VMware | 發展上限取決於是否延伸到自動化、雲端與資安 |
| SI Engineer / System Integration Engineer | 為客戶做 PoC、建置、移轉、整合、文件與教育訓練 | Network、Server、VMware、Security、Cloud、Troubleshooting | 常有客戶現場與專案時程；需確認是否長期駐點 |
| Cloud Engineer | 建置與維護雲端資源、監控、網路與自動化 | Linux、Network、Git、Ansible、AWS 對照 | 可能有 on-call；是否輪班依團隊 |
| Cloud Solutions Architect | 將需求轉成可靠、安全、可擴充、成本合理的架構 | Network、Security、HA/DR、文件、需求分析 | 多數職缺期待跨領域與專案經驗 |
| DevOps Engineer | 建立 CI/CD、自動化部署、IaC、監控與開發維運流程 | Git、Linux、YAML、Ansible、GitHub Actions | 生產系統常有 on-call，不等於固定輪班 |
| SRE | 以軟體工程改善可靠性、SLO、監控、事故與自動化 | Linux、Coding、Observability、Incident、Automation | on-call 常見；台灣部分職缺可能只是維運工程師改名 |
| MIS / Internal IT | 維護單一公司的帳號、端點、AD、網路、Server 與供應商 | Windows、AD、Network、Help Desk、Security | 多數日班，但單人 MIS 可能有非正式待命 |

## 4. 工具、成本與安全界線

### 必要工具：全部免費

| 工具 | 用途 | 備註 |
|---|---|---|
| Cisco Packet Tracer | Cisco 網路模擬 | 透過 Cisco Networking Academy / Skills for All 帳號下載 |
| Wireshark | 封包擷取與分析 | 只擷取自己有權限的設備與網路 |
| VMware Workstation Pro | 建立 Ubuntu／Windows Server VM | Broadcom 已提供 Desktop Hypervisor 免費使用；下載需帳號與完整基本資料 |
| Ubuntu Server LTS | Linux Lab | 免費 |
| Windows Server 2025 Evaluation | Windows Server／AD Lab | Microsoft 評估版；注意啟用與評估限制 |
| Git + GitHub | 版本控制與作品紀錄 | 不得上傳密碼、Token、Private Key、ISO、VM Disk |
| Obsidian 或 VS Code | Markdown 筆記 | 任選其一 |
| diagrams.net | 架構圖 | 可在瀏覽器使用 |

### 電腦資源原則

- 16 GB RAM：一次只開 1 台 Windows Server 或 1–2 台輕量 Linux VM。
- 32 GB RAM：可較舒服地同時開 Windows Server、Client 與 Ubuntu。
- 磁碟至少預留 80 GB；若不足，Windows AD Lab 改為架構理解與單機示範。
- 不知道你的實際可用 RAM／磁碟，因此本手冊不假設能同時執行多台 VM。

### 安全界線

- 所有掃描、封包擷取、ACL、防火牆、帳號與權限 Lab，只在自己的 VM、Packet Tracer 或明確授權環境內進行。
- 不下載或使用聲稱為「實際外流題庫／Dump」的 CCNA 題目。本手冊使用 Cisco 官方 Exam Topics 與自行設計的情境題，重點是理解錯誤選項為何錯。
- AWS Lab 本月不要求建立付費資源，避免因 Free Tier 規則、區域與服務變動產生費用。

---

## 5. 每日固定節奏

| 時間 | 內容 |
|---|---|
| 00:00–00:10 | 回想昨日內容，不看筆記寫 3 點 |
| 00:10–01:30 | 理論與手算／畫圖 |
| 01:30–01:40 | 休息 |
| 01:40–02:50 | Lab + Debug Lab |
| 02:50–03:00 | Git Commit、驗收、可選填 Memo |

### AI / Codex 使用規則

你在 Codex 的其他工作紀錄不會自動出現在這份對話中。遇到錯誤時，保存：

1. 原始錯誤訊息。
2. 你原本想達成什麼。
3. 你已經測過什麼。
4. 實際環境與版本。
5. 最後怎麼驗證修好。

建議提示詞：

```text
你是我的故障排除教練。不要直接給答案。
一次只問我一個能縮小範圍的問題。
每次我回答後，先說明這個證據排除了哪些可能性，再問下一題。
```

---

# 6. 30 天每日計畫


## Day 01｜建立學習環境與「一個請求如何走到伺服器」

### 今日驗收目標

> `README.md`、工具安裝截圖、第一張網路拓樸圖、第一次故障紀錄。

### 理論 90 分鐘

- 認識電腦、作業系統、應用程式、伺服器、用戶端、網路設備之間的差別。
- 先建立整體流程：瀏覽器輸入網址 → DNS 找 IP → 封包經交換器與路由器 → 伺服器回應。
- 認識本月工具的角色：Packet Tracer 模擬網路、Wireshark 看封包、VMware Workstation 跑虛擬機、Git 保存變更。

### Lab 90 分鐘

- 建立 GitHub 或本機 Git 儲存庫 `cloud-network-security-prestudy`。
- 建立資料夾：`notes/`、`labs/`、`screenshots/`、`troubleshooting/`、`career-memos/`。
- 安裝 Packet Tracer、Wireshark、Git；VMware Workstation Pro 先下載，今天不必建立 VM。
- 在 Packet Tracer 放置 2 台 PC 與 1 台 Switch，連線後設定同網段 IP，完成第一次 ping。

### Debug Lab

故意把其中一台 PC 的 IP 改到不同網段但不設 Gateway，記錄 ping 失敗訊息；不要立刻改回，先寫出三個可能原因。

### ⚠️ 最容易卡住的地方

初學者常把「網路設備連了線」誤認為「一定能通」。實體／鏈路連線只是第一步，IP、遮罩、路由與服務都可能造成失敗。

### AWS 對照（補充，不延伸成獨立課程）

EC2 是雲端虛擬伺服器；VPC 是邏輯隔離的雲端網路。今天只建立名詞對照，不開 AWS 資源。

### 職務／公司技能備註

所有職位都會用到整體架構圖。AWS 架構師尤其必須能把使用者、DNS、網路、安全控制與運算資源畫成一條完整路徑。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 02｜位元、位元組、二進位與十六進位

### 今日驗收目標

> 二進位速查表與 10 題轉換紀錄。

### 理論 90 分鐘

- bit、Byte、Kb、KB、Mb、MB 的差異；網路速率通常用 bit，檔案容量常用 Byte。
- 二進位為何適合表示 IP、遮罩、權限；十六進位為何常出現在 MAC、IPv6、封包內容。
- 練習十進位 0–255 與 8 位元二進位互換，先理解 128、64、32、16、8、4、2、1。

### Lab 90 分鐘

- 手算並核對：10、64、127、128、192、224、240、248、252、254、255 的二進位。
- 在 Windows PowerShell 使用 `Format-Hex` 查看一個文字檔；在 Wireshark 找到十六進位封包窗格。
- 建立 `notes/number-systems.md`，用自己的話解釋為什麼 IPv4 每段最大是 255。

### Debug Lab

故意把 1 MB 當成 1 Mb 計算傳輸時間，找出結果差八倍的原因。

### ⚠️ 最容易卡住的地方

子網路真正的門檻通常不是公式，而是看到 192、224、240 等數字時無法立即聯想到前幾個 bit 是 1。

### AWS 對照（補充，不延伸成獨立課程）

雲端計價與效能常同時出現 GB、GiB、Gbps、IOPS；單位讀錯會造成架構估算錯誤。

### 職務／公司技能備註

SI、MIS、雲端架構師都要能看懂頻寬與容量；售前或架構規劃更需要避免單位誤判。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 03｜OSI、TCP/IP、封裝與 Wireshark

### 今日驗收目標

> `labs/day03-packet-walkthrough.md`，至少三張有註解的封包截圖。

### 理論 90 分鐘

- OSI 七層不是背誦比賽；重點是故障發生時能把問題縮小到哪一層。
- 理解資料在傳送端逐層加上 Header／Trailer，接收端逐層拆除。
- 分清 Ethernet Frame、IP Packet、TCP Segment、UDP Datagram；日常口語常混用，但除錯時要知道差別。
- TCP 與 UDP 的目的；Port 是交給主機上的哪個程式，不是另一種 IP。

### Lab 90 分鐘

- 開啟 Wireshark，只擷取自己電腦的流量；依序執行 `ping 1.1.1.1`、`nslookup example.com`、開啟一個 HTTPS 網站。
- 使用顯示過濾器 `icmp`、`dns`、`tcp`；各截一張圖並標註來源／目的 IP、Protocol、Port。
- 畫出一次 DNS 查詢和一次 HTTPS 連線在哪些層運作。

### Debug Lab

把 Wireshark 的 Capture Filter 與 Display Filter 故意混用，記錄錯誤，再說明兩者差異。

### ⚠️ 最容易卡住的地方

最常卡住的是把『第幾層』當成唯一答案。真實服務常跨多層；OSI 的價值是定位，不是把技術硬塞進單一格。

### AWS 對照（補充，不延伸成獨立課程）

Security Group 規則會用到 Protocol 與 Port；VPC Flow Logs 類似從網路層觀察允許／拒絕的流量，但看不到完整應用內容。

### 職務／公司技能備註

VMware Technical Support、Network Security Engineer、SI Engineer都常以 OSI 分層排錯；AWS Support／Cloud Engineer 也一樣。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 04｜Ethernet、MAC、ARP 與交換器學習

### 今日驗收目標

> ARP 流程圖與 MAC Table 變化紀錄。

### 理論 90 分鐘

- MAC 位址用於同一個 Layer 2 廣播域內的傳遞；IP 用於跨網路的邏輯定位。
- 交換器透過來源 MAC 學習 MAC Address Table，再依目的 MAC 轉送、Flood 或 Filter。
- ARP 的問題是『這個 IPv4 在本地網段對應哪個 MAC？』；ARP 不會替遠端網站找到最終伺服器 MAC。
- 廣播、未知單播與已知單播的差異。

### Lab 90 分鐘

- Packet Tracer 建立 3 PC + 1 Switch；清空或觀察 MAC Table，依序 ping，使用 `show mac address-table`。
- 在 Windows 執行 `arp -d *`（需系統權限時可改用查看而不清除）與 `arp -a`，觀察 ping 前後差異。
- 用 Simulation Mode 追蹤 ARP Request、ARP Reply、ICMP Echo。

### Debug Lab

把兩台 PC 設成相同 IP，觀察異常；恢復前先寫出『IP 衝突』與『MAC Table 問題』如何區分。

### ⚠️ 最容易卡住的地方

封包要去遠端網路時，Ethernet 目的 MAC 是 Default Gateway 的 MAC，不是遠端伺服器的 MAC。這是 CCNA 常見卡點。

### AWS 對照（補充，不延伸成獨立課程）

在 AWS 中你通常不直接管理實體交換器或 ARP 細節，但理解二層行為有助於知道雲端網路抽象化了什麼。

### 職務／公司技能備註

Network Security 與 SI 基礎架構專案都會用到 L2 基礎；AWS 架構師則需要理解哪些傳統機房概念在 VPC 中被隱藏。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 05｜IPv4、子網路遮罩與同網段判斷

### 今日驗收目標

> 15 題同網段判斷與答案理由。

### 理論 90 分鐘

- IPv4 位址由 Network Portion 與 Host Portion 組成，分界由 Prefix Length／Subnet Mask 決定。
- 同網段主機直接 ARP；不同網段主機把 Frame 交給 Default Gateway。
- Network Address、Broadcast Address、可用主機範圍。
- 不要只背 Class A/B/C；現代路由以 CIDR Prefix 為主。

### Lab 90 分鐘

- 手算並驗證：192.168.10.34/24、/27、/28 的 Network、Broadcast、Host Range。
- Packet Tracer 建立兩台同網段 PC，再將一台遮罩改錯，觀察單向或雙向異常。
- 用 PowerShell `Get-NetIPConfiguration`、`ipconfig /all` 找出本機 IP、Mask、Gateway、DNS。

### Debug Lab

設定 IP 看起來相近但遮罩不同的兩台主機，例如 /24 與 /25，預測雙方各自認為對方在本地還是遠端。

### ⚠️ 最容易卡住的地方

兩台主機可能因遮罩不一致而對『對方是否在本地』做出不同判斷，造成看似奇怪的不對稱問題。

### AWS 對照（補充，不延伸成獨立課程）

VPC 與 Subnet 都以 CIDR 表示；設計時若 CIDR 重疊，未來 VPN、Peering、Transit Gateway 整合會受限。

### 職務／公司技能備註

AWS 架構師、網路工程師與 SI 都必須能在圖上快速判斷 CIDR 是否重疊。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 06｜子網路切割深度練習：不靠死背

### 今日驗收目標

> 一份有計算過程的 VLSM 規劃表。

### 理論 90 分鐘

- 從需求反推 Prefix：需要幾個子網？每個子網需要幾個位址？
- Block Size = 256 − 遮罩最後一個非 255 的 Octet；理解它為何成立。
- /25 到 /30 的常見範圍；/31、/32 先知道用途，不要求熟練。
- VLSM 的核心是先分配最大需求，再逐步切小。

### Lab 90 分鐘

- 將 192.168.100.0/24 分給 100、50、20、10 台主機，做一份 VLSM 表。
- 用 Packet Tracer 建立其中兩個子網與一台 Router，先只完成 IP 規劃，不設定路由。
- 限時 20 分鐘做 10 題 Prefix／Host 數轉換；錯題必須寫錯因。

### Debug Lab

故意把 Broadcast Address 配給主機，觀察模擬器反應；再說明為何不能使用。

### ⚠️ 最容易卡住的地方

常見錯誤是先照子網數量平均切割，忽略不同部門主機需求；VLSM 要先排需求大小。

### AWS 對照（補充，不延伸成獨立課程）

AWS 每個 Subnet 會保留部分 IP，不能把傳統可用主機數直接當成 AWS 可用數；本月只記住『雲端另有保留規則』。

### 職務／公司技能備註

AWS 架構設計、企業網路規劃與Network Engineer／SI Engineer的客戶方案都會用到位址規劃。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 07｜第 1 週整合：從封包判斷故障層

### 今日驗收目標

> 第 1 週測驗、故障報告、弱點清單。

### 理論 90 分鐘

- 複習：二進位 → Mask → 同網段判斷 → ARP → Switch → Gateway → DNS／TCP。
- 建立固定排錯順序：需求 → 現象 → 範圍 → 假設 → 測試 → 結論 → 復原。
- 學會區分『ping IP 不通』、『ping IP 通但網域不通』、『連線建立但應用錯誤』。

### Lab 90 分鐘

- 完成本文件第 1 週測驗，不查答案先作答。
- Packet Tracer 故障挑戰：錯 IP、錯 Mask、線路關閉、重複 IP 四種問題混合，逐一排除。
- 整理第一週所有錯誤到 `troubleshooting/week1.md`。

### Debug Lab

請 AI 只扮演提示者：每次只能問你一個診斷問題，不得直接給設定答案。

### ⚠️ 最容易卡住的地方

排錯不是一次猜中，而是每個命令都要排除一組可能性。沒有寫下假設，就容易反覆亂改設定。

### AWS 對照（補充，不延伸成獨立課程）

AWS 架構師也要以相同方法排查：DNS、路由、Security Group、NACL、服務健康狀態分層檢查。

### 職務／公司技能備註

這種有紀錄的排錯能力比『我有看過 CCNA』更能支持技術客服、SI、Cloud Support、DevOps 面試。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 08｜Cisco IOS CLI 與設備管理基本功

### 今日驗收目標

> CLI 操作紀錄與介面狀態判讀表。

### 理論 90 分鐘

- User EXEC、Privileged EXEC、Global Configuration、Interface Configuration 模式。
- Running-config 與 Startup-config；重新啟動後設定為何可能消失。
- 管理介面、Console、SSH 的概念；設備名稱與描述是維運資訊，不只是美觀。
- 常用 show 命令優先於亂改設定。

### Lab 90 分鐘

- 在 Packet Tracer Router／Switch 設定 hostname、enable secret、console password、banner。
- 練習 `show running-config`、`show startup-config`、`show ip interface brief`、`copy running-config startup-config`。
- 建立自己的 Cisco CLI Cheat Sheet，只收錄今天實際使用過的命令。

### Debug Lab

設定介面 IP 但忘記 `no shutdown`，用 `show ip interface brief` 判斷 administratively down 與 down 的差別。

### ⚠️ 最容易卡住的地方

介面狀態要分成 Status 與 Protocol；看到 down/down、up/down、administratively down 時，排查方向不同。

### AWS 對照（補充，不延伸成獨立課程）

AWS 沒有 Cisco IOS，但 AWS CLI 同樣需要理解『查詢目前狀態』與『變更設定』是兩種操作。

### 職務／公司技能備註

Network Security Engineer 與多數 SI 網路職缺直接使用；Infrastructure SI技術人員也需讀懂客戶網路。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 09｜VLAN、Access Port、Trunk 與 Native VLAN

### 今日驗收目標

> VLAN 拓樸、Port 對照表、兩種故障紀錄。

### 理論 90 分鐘

- VLAN 把一台實體 Switch 切成多個邏輯 Broadcast Domain。
- Access Port 通常承載單一 VLAN；802.1Q Trunk 可承載多個 VLAN。
- Tag 在哪裡加上與移除；Native VLAN 的 Untagged 行為。
- 不同 VLAN 即使接在同一台交換器，也需要 Layer 3 Routing 才能互通。

### Lab 90 分鐘

- 建立兩台 Switch、四台 PC；建立 VLAN 10/20，設定 Access Port 與 Trunk。
- 使用 `show vlan brief`、`show interfaces trunk` 驗證，不只用 ping。
- 故意只在其中一台 Switch 建 VLAN 20，觀察跨交換器的結果。

### Debug Lab

製造 Native VLAN mismatch 或 Allowed VLAN 缺漏，使用 show 命令找原因。

### ⚠️ 最容易卡住的地方

Trunk 不是『讓所有 VLAN 自動互通』；它只是把多個 VLAN 延伸到另一台設備。

### AWS 對照（補充，不延伸成獨立課程）

AWS Subnet 不是 VLAN 的同義詞，但都用於隔離與分段。VPC 中跨 Subnet 通常由隱含路由器處理，再受路由與安全規則控制。

### 職務／公司技能備註

Network Engineer、Wireless Engineer 與 SI 網路建置直接使用；AWS 架構師可藉此理解網路分段需求。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 10｜Layer 2 Loop、STP 與 EtherChannel

### 今日驗收目標

> 一張 STP Port Role 推導圖與 EtherChannel 故障紀錄。

### 理論 90 分鐘

- 交換器網路若有 Loop，Broadcast Frame 沒有 TTL，可能形成 Broadcast Storm。
- STP 的目標是保留備援但阻擋迴圈；理解 Root Bridge、Root Port、Designated Port、Blocked／Alternate。
- Root Bridge 選舉先比 Bridge ID；不要只背『最低 MAC』。
- EtherChannel 把多條實體連線組成邏輯連線；兩端參數要一致。

### Lab 90 分鐘

- Packet Tracer 建立三台 Switch 三角形，使用 `show spanning-tree` 找 Root Bridge 與被阻擋 Port。
- 改變 Bridge Priority，預測再驗證 Root 變化。
- 建立簡單 EtherChannel，使用 `show etherchannel summary` 驗證。

### Debug Lab

故意讓 EtherChannel 兩端模式或 VLAN 設定不一致，觀察 Channel 未形成。

### ⚠️ 最容易卡住的地方

STP 題目先找 Root Bridge，再從非 Root Switch 找最短 Root Path，最後才判斷剩餘 Port；跳步最容易錯。

### AWS 對照（補充，不延伸成獨立課程）

公有雲網路通常不讓使用者操作 STP，但高可用設計仍然要避免單點與不受控的循環依賴。

### 職務／公司技能備註

Network SI 最直接；VMware／vSAN 專案也需要穩定的交換網路作底層。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 11｜Routing Table、Longest Prefix Match、Static／Default Route

### 今日驗收目標

> Routing Table 逐條解讀與三種失敗原因。

### 理論 90 分鐘

- Router 依目的 IP 查 Routing Table，不會以來源 IP 決定一般轉送路徑。
- Connected、Local、Static、Dynamic Route 的來源。
- Longest Prefix Match：匹配最精確的路由，而不是看表格上下順序。
- Default Route 是最後才使用的 0.0.0.0/0，不代表永遠優先。

### Lab 90 分鐘

- 建立三台 Router 串接三個 LAN，先設定介面 IP，再用 Static Route 完成端到端 ping。
- 使用 `show ip route`，逐條說出 Prefix、Next Hop／Exit Interface、來源。
- 加入一條更精確路由與一條 Default Route，設計封包會走哪裡的預測題。

### Debug Lab

故意設定錯誤 Next Hop 或缺少回程路由，觀察『去得了但回不來』。

### ⚠️ 最容易卡住的地方

Ping 成功需要雙向路徑。只看來源端的去程路由，是初學 Routing 最常見錯誤。

### AWS 對照（補充，不延伸成獨立課程）

VPC Route Table 也使用最長前綴匹配；Local Route、Internet Gateway、NAT Gateway、VPN／Transit Gateway 都可成為目標。

### 職務／公司技能備註

AWS 架構師核心技能；Network Security Engineer、SI Network Engineer同樣直接使用。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 12｜ICMP、TTL、Ping 與 Traceroute

### 今日驗收目標

> 一次真實 traceroute 的逐跳解釋。

### 理論 90 分鐘

- Ping 主要使用 ICMP Echo Request／Reply，但 Ping 不通不等於所有服務都不通。
- TTL 每經過一台 Layer 3 Router 減一，用來避免無限路由迴圈。
- Traceroute 利用 TTL 到期與 ICMP 回覆逐跳觀察路徑；不同 OS 實作可能不同。
- 常見 ICMP 訊息：Destination Unreachable、Time Exceeded。

### Lab 90 分鐘

- 在本機執行 `ping`、`tracert`／`traceroute`；在 Wireshark 觀察 ICMP。
- Packet Tracer 中先建立完整路由，再移除中間路由，觀察 ICMP 回應。
- 用 `show ip route` 配合 traceroute 說明每一跳。

### Debug Lab

關閉終點主機回覆或在路徑中製造問題，區分 timeout 與 unreachable。

### ⚠️ 最容易卡住的地方

中間設備不回 ICMP，不一定代表流量無法通過；Traceroute 的星號不能直接解讀成那一跳故障。

### AWS 對照（補充，不延伸成獨立課程）

雲端中 ICMP 也受 Security Group／NACL 規則影響；服務健康檢查常不只看 Ping。

### 職務／公司技能備註

技術客服、NOC、SI、Cloud Support 都會用；SRE 更關心端到端服務可用性，不只主機是否回 Ping。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 13｜DHCP、DNS 與 NAT：最常混在一起的三項服務

### 今日驗收目標

> DHCP／DNS／NAT 三者責任邊界表。

### 理論 90 分鐘

- DHCP DORA 流程與 Lease；169.254.x.x 通常表示未取得 IPv4 DHCP 租約而使用 APIPA。
- DNS 把名稱解析成資料，不負責傳送網頁；A、AAAA、CNAME、MX、PTR 的用途。
- NAT／PAT 轉換位址與 Port；Private IP 為何能共享 Public IP。
- 先問『IP 是否取得』，再問『名稱是否解析』，最後問『服務 Port 是否可達』。

### Lab 90 分鐘

- Packet Tracer 設定 Router DHCP Pool，讓兩台 PC 自動取得位址。
- 使用 `ipconfig /release`、`ipconfig /renew`、`nslookup`、`ipconfig /displaydns`。
- 建立簡單 NAT/PAT 拓樸，使用 `show ip nat translations`。
- Wireshark 觀察一筆 DNS Query／Response。

### Debug Lab

製造三種故障：DHCP Gateway 錯、DNS Server 錯、NAT Inside／Outside 漏設；逐一用不同證據定位。

### ⚠️ 最容易卡住的地方

DNS 解析成功不代表 TCP 服務可連；能 Ping IP 但不能開網站，也不能立刻判定 DNS 正常或異常。

### AWS 對照（補充，不延伸成獨立課程）

Route 53 對應 DNS；VPC DHCP Options 提供 DNS 等資訊；NAT Gateway 讓私有 Subnet 主機主動連外但不直接接受外部連入。

### 職務／公司技能備註

AWS 架構師必備；Network／ADC 產品、SI、MIS、DevOps 都頻繁使用。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 14｜IPv6 基礎與第 2 週 CCNA 整合

### 今日驗收目標

> 第 2 週測驗、整體封包流程圖、CCNA 弱點排名。

### 理論 90 分鐘

- IPv6 128 位元、十六進位表示、縮寫規則；一個位址只能使用一次 `::`。
- Global Unicast、Link-local、Multicast、Loopback；IPv6 不使用 Broadcast。
- SLAAC、DHCPv6 先建立概念；Neighbor Discovery 與 IPv4 ARP 的關係。
- 回顧 CCNA 最難主線：VLAN／Trunk → STP → Routing → DHCP/DNS/NAT。

### Lab 90 分鐘

- 在 Packet Tracer 兩個 LAN 設定 IPv6 Global Unicast 與 Link-local，完成 IPv6 ping。
- 完成第 2 週測驗；Subnetting 題限時 15 分鐘。
- 用一張圖畫出 PC 開啟網站時，ARP/ND、DNS、Routing、NAT、TCP 的先後關係。

### Debug Lab

製造錯誤 IPv6 Prefix 或漏開 IPv6 Routing，使用 `show ipv6 interface brief`、`show ipv6 route`。

### ⚠️ 最容易卡住的地方

IPv6 不能只把 IPv4 數字加長；ND、SLAAC、Link-local 與 Multicast 的行為有自己的邏輯。

### AWS 對照（補充，不延伸成獨立課程）

AWS VPC 支援 IPv6；IPv6 通常是 Global Unicast，不需要以 NAT 當作基本連外方式，但仍需防火牆與路由控制。

### 職務／公司技能備註

CCNA、網路資安與雲端架構都會逐漸遇到；目前目標是能看懂與基本排錯。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 15｜Linux 檔案系統與命令列

### 今日驗收目標

> Ubuntu VM Snapshot `clean-install` 與 Linux 指令實作筆記。

### 理論 90 分鐘

- Linux 目錄樹：`/`、`/home`、`/etc`、`/var`、`/tmp`、`/usr`、`/proc`。
- 絕對路徑與相對路徑；目前工作目錄；檔名大小寫。
- 標準輸入、標準輸出、標準錯誤；Pipe 與 Redirect 的目的。
- 先讀錯誤訊息，再決定命令。

### Lab 90 分鐘

- 在 VMware Workstation 建立 Ubuntu Server VM；建議 2 vCPU、2–4 GB RAM、25 GB Disk，依電腦資源調整。
- 練習 `pwd ls cd mkdir touch cp mv rm cat less head tail grep find`。
- 使用 `>`、`>>`、`2>`、`|` 建立與過濾紀錄。
- 把每個命令的實際輸出貼入 `labs/day15-linux-basics.md`，不要只列語法。

### Debug Lab

建立有空白的檔名、錯誤大小寫與不存在路徑，處理 `No such file or directory`。

### ⚠️ 最容易卡住的地方

Linux 不是靠記大量命令，而是理解『資料在哪裡、命令讀什麼、輸出到哪裡』。

### AWS 對照（補充，不延伸成獨立課程）

多數 EC2 與容器工作負載以 Linux 為主；AWS 架構師不一定每日管理主機，但必須能與維運人員溝通。

### 職務／公司技能備註

DevOps Engineer、Cloud Engineer、SRE 最直接；Infrastructure SI也把 Linux 視為基礎或加分。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 16｜Linux 使用者、群組、權限與 sudo

### 今日驗收目標

> 權限矩陣與三個 Permission denied 案例。

### 理論 90 分鐘

- Owner、Group、Other；read/write/execute 對檔案與目錄的含義不同。
- `rwx` 與八進位 4/2/1；例如 755、640 要能推導，不死背。
- `chmod`、`chown`、`umask`；最小權限原則。
- root 與 sudo；不要為了省事長期用 root。

### Lab 90 分鐘

- 建立兩個使用者與一個群組，建立共享目錄。
- 分別設定 755、750、640，切換使用者驗證哪些操作被允許。
- 使用 `id`、`groups`、`ls -l`、`stat` 查看權限資訊。
- 把每次 Permission denied 的原因寫成『誰、對哪個物件、缺哪一個權限』。

### Debug Lab

故意移除目錄的 execute 權限，觀察即使檔案有 read 權限仍可能無法存取。

### ⚠️ 最容易卡住的地方

目錄的 `x` 代表能進入／Traverse，不是執行目錄；這是 LPIC 與實務常見卡點。

### AWS 對照（補充，不延伸成獨立課程）

Linux 權限控制主機內部；AWS IAM 控制 AWS API 與資源。兩者層級不同，不能互相取代。

### 職務／公司技能備註

DevOps、SRE、Cloud Engineer、SI Linux 工程師都直接使用；Security+ 也重視最小權限。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 17｜Process、Service、Package 與 Log

### 今日驗收目標

> Nginx 生命週期與一份 Log-based 故障報告。

### 理論 90 分鐘

- Program 是靜態檔案，Process 是執行中的實例，Service 通常是長時間背景程序。
- PID、Parent Process、前景／背景；CPU／Memory 只是觀察指標，不等於故障原因。
- `systemd`、Unit、啟動／停止／開機自動啟動。
- Log 是建立時間線與證據，不是最後才看。

### Lab 90 分鐘

- 使用 `ps aux`、`top` 或 `htop`、`pgrep`、`kill`。
- 安裝 Nginx：`apt update`、`apt install nginx`；使用 `systemctl status/start/stop/enable nginx`。
- 使用 `journalctl -u nginx` 與 `/var/log/` 查找紀錄。
- Git commit：`Install nginx and document service lifecycle`。

### Debug Lab

停止 Nginx 後測試連線，再啟動；另外故意設定錯誤設定檔並使用 `nginx -t` 驗證。

### ⚠️ 最容易卡住的地方

服務連不上時不要直接重裝；先確認 Process、Listening Port、Firewall、設定檔與 Log。

### AWS 對照（補充，不延伸成獨立課程）

EC2 上的應用仍有 Process、Port、Log；CloudWatch 可集中指標與日誌。

### 職務／公司技能備註

DevOps／SRE、AWS 維運與 Cloud-native 專案直接使用；MIS 也常管理內部服務。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 18｜Linux 網路、SSH、Port 與本機防火牆

### 今日驗收目標

> SSH 連線流程、三種錯誤比較表。

### 理論 90 分鐘

- 網路介面、IP、Route、DNS Resolver；Linux 查詢工具的責任邊界。
- Listening Port 代表程式正在等待連線；Established 代表連線已建立。
- SSH 的用途與金鑰概念；密碼、私鑰、公鑰的角色。
- Host Firewall 與 Network Firewall 可以同時存在。

### Lab 90 分鐘

- 使用 `ip addr`、`ip route`、`resolvectl status`、`ping`、`ss -tulpn`、`curl`。
- 啟用 OpenSSH Server；從 Host SSH 到 Ubuntu VM。
- 使用 UFW 僅允許 SSH 與 HTTP，驗證 Nginx。
- VMware NAT 模式下記錄 Host 與 VM 的 IP、Gateway、DNS。

### Debug Lab

關閉 SSH Service、封鎖 Port 22、改錯 IP 三種故障分別測試，記錄錯誤訊息有何不同。

### ⚠️ 最容易卡住的地方

Connection refused 通常表示能到主機但該 Port 沒服務或被主動拒絕；Timeout 更可能是路徑、防火牆或無回應。不是絕對，但可作初步線索。

### AWS 對照（補充，不延伸成獨立課程）

EC2 Security Group、Subnet Route、NACL、Host Firewall 可能同時影響 SSH；排錯要逐層檢查。

### 職務／公司技能備註

AWS Cloud Support／架構師、DevOps、SRE 與 SI 都會遇到；這也是遠端 on-call 排錯的基本功。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 19｜VMware 虛擬化：Hypervisor、VM Network 與 Snapshot

### 今日驗收目標

> VMware 網路模式比較表與 Snapshot 實驗。

### 理論 90 分鐘

- Type 1 與 Type 2 Hypervisor；Workstation 與 ESXi／vSphere 的差別。
- VM 是虛擬硬體集合；Guest OS 不知道所有底層細節。
- NAT、Bridged、Host-only 的連線範圍與風險。
- Snapshot 不是完整備份；了解 Snapshot Chain 與長期保留風險。

### Lab 90 分鐘

- 為 Ubuntu VM 分別切換 NAT 與 Host-only，記錄 IP、能否連網、Host 能否連 VM。
- 建立 Snapshot、修改 Nginx 首頁、還原 Snapshot，觀察結果。
- 畫出 Host、Virtual Switch、VM、實體網卡、Router 的關係。

### Debug Lab

VM 無法連網時，以 Link → IP → Route → DNS → Port 順序排查；不要直接刪 VM。

### ⚠️ 最容易卡住的地方

Bridged 不是『效能比較好』的代名詞；它讓 VM 像區網中的獨立主機，安全與位址管理都不同。

### AWS 對照（補充，不延伸成獨立課程）

EC2 也以虛擬化提供運算資源，但雲端使用者操作的是更高層 API；理解 VMware 有助於比較私有雲與公有雲。

### 職務／公司技能備註

VMware Technical Support／Professional Services 最直接；其他 SI 的虛擬化專案也會用到。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 20｜Windows Server 基礎、DNS／DHCP 角色

### 今日驗收目標

> Windows Server VM Snapshot 與一份服務驗證紀錄。

### 理論 90 分鐘

- Windows Server 與一般 Windows Client 的角色差異；Server Role、Feature、Service。
- GUI 與 PowerShell 都是管理介面；真實環境需能讀命令輸出。
- 固定 IP 對伺服器的重要性；DNS 與 DHCP 服務依賴。
- 本日重點是認識，不追求熟練所有管理工具。

### Lab 90 分鐘

- 建立 Windows Server 2025 Evaluation VM；資源不足時只完成安裝與 Snapshot，後續與 Ubuntu 擇一開機。
- 設定固定 IP；使用 `ipconfig /all`、`Get-NetIPConfiguration`、`Test-NetConnection`。
- 安裝 DNS 或 DHCP Role（二選一先完成），建立一筆測試紀錄或 Scope。
- 從 Client 或 Host 進行 `nslookup`／DHCP 取得測試。

### Debug Lab

將 Windows Server DNS 指向錯誤位置或讓 Client 使用錯 DNS，觀察名稱解析失敗但 IP 連線可能正常。

### ⚠️ 最容易卡住的地方

AD Domain 環境中，Client DNS 通常應指向能解析 AD 區域的 DNS，而不是隨意填公共 DNS。

### AWS 對照（補充，不延伸成獨立課程）

Windows Server 可運行於 EC2；AWS Managed Microsoft AD 則把部分 AD 維運交由代管服務。

### 職務／公司技能備註

MIS、SI Windows 系統工程師、Infrastructure SI基礎架構職缺最直接；AWS 架構師需要理解混合雲客戶的 Windows 依賴。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 21｜Active Directory、Domain、OU、Group Policy

### 今日驗收目標

> AD 物件關係圖與第 3 週測驗。

### 理論 90 分鐘

- AD DS 解決集中式身分、電腦、群組與原則管理；Domain 不只是網站網域。
- Domain Controller、Forest、Domain、OU、User、Group、Computer Object。
- Authentication 與 Authorization；登入成功不代表有權存取所有資源。
- Group Policy 的套用範圍與繼承概念。

### Lab 90 分鐘

- 在 Windows Server 安裝 AD DS 並建立測試 Forest（資源不足時完成架構圖與官方教學閱讀即可）。
- 建立 OU、User、Security Group；將使用者加入群組。
- 建立一個簡單 GPO，例如限制控制台或設定桌布；有 Client VM 才進行 Join Domain。
- 整理『本機帳號』與『網域帳號』差異。

### Debug Lab

製造 DNS 指向錯誤導致 Client 無法 Join Domain，先用 `nslookup` 與時間同步觀念排查。

### ⚠️ 最容易卡住的地方

AD 很多『看似權限問題』其實是 DNS、時間同步或物件範圍問題。

### AWS 對照（補充，不延伸成獨立課程）

IAM 與 AD 都處理身分與權限，但模型不同；企業常透過 IAM Identity Center、AD Connector 或 Managed Microsoft AD 整合。

### 職務／公司技能備註

MIS、Windows SI 最直接；AWS 架構師做企業遷移與混合身分時會遇到。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 22｜Git／GitHub：把實驗變成可追蹤作品

### 今日驗收目標

> 至少 10 個有意義 Commit、一次 Branch／Merge／Conflict 紀錄。

### 理論 90 分鐘

- Repository、Working Tree、Staging Area、Commit；Git 不是單純雲端備份。
- Commit 應表達一個可理解的變更；Log 是工程紀錄。
- Branch、Merge、Conflict 建立概念；先學可靠的單人流程。
- 敏感資訊、密碼、私鑰不得 Commit。

### Lab 90 分鐘

- 練習 `git status add commit log diff branch switch merge`。
- 建立 `feature/memo-template` Branch，修改 Memo 格式，再 Merge 回 main。
- 故意在兩個 Branch 修改同一行，處理一次 Merge Conflict。
- 新增 `.gitignore`，排除 VM、ISO、封包檔與秘密資料。

### Debug Lab

復原一次誤改：先用 `git diff` 找變化，再選擇還原工作區或建立修正 Commit；不要亂用強制 reset。

### ⚠️ 最容易卡住的地方

Git 最常卡在不知道檔案目前位於工作區、Staging 還是 Commit；每一步先看 `git status`。

### AWS 對照（補充，不延伸成獨立課程）

Infrastructure as Code、架構文件與自動化設定都應版本控制；Cloud Architect 也需要能審查變更。

### 職務／公司技能備註

DevOps、SRE、雷麒雲端系統、宏燁雲原生最直接；SI 用 Git 管理文件與自動化也很有價值。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 23｜YAML 與 Ansible：第一次自動化部署

### 今日驗收目標

> 可重複執行的第一個 Playbook 與 Debug 紀錄。

### 理論 90 分鐘

- 自動化目標是可重複、可檢查、降低手動差異，不只是少打幾個命令。
- YAML 依縮排表達階層；空白與資料型態容易造成錯誤。
- Ansible Control Node、Managed Node、Inventory、Module、Playbook。
- Idempotency：重複執行應維持目標狀態，而不是每次造成額外副作用。

### Lab 90 分鐘

- 在 Ubuntu 安裝 Ansible；若只有一台 VM，先以 localhost 練習。
- 建立 Inventory，執行 `ansible all -m ping`。
- 寫 Playbook：安裝 Nginx、啟動並 enable、部署自訂首頁。
- 連續執行兩次，比較 changed 與 ok。

### Debug Lab

故意製造 YAML 縮排錯誤、Module 名稱錯誤或 SSH 權限問題，依錯誤訊息修正。

### ⚠️ 最容易卡住的地方

Ansible 成功連線不代表所有 Task 有權限；`become`、使用者與 sudo 規則要分開理解。

### AWS 對照（補充，不延伸成獨立課程）

AWS 架構常使用 CloudFormation／CDK／Terraform；Ansible偏向組態與跨系統自動化。工具不同，但宣告式與可重複思想相通。

### 職務／公司技能備註

DevOps、SRE、雷麒、宏燁雲原生與進階 SI；AWS 架構師需理解自動化交付，而非只會 Console 點選。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 24｜資訊安全核心：CIA、風險、弱點與分層防禦

### 今日驗收目標

> 風險登錄表與 Hardening Checklist。

### 理論 90 分鐘

- Confidentiality、Integrity、Availability；安全不是只防駭客，也包含誤刪、故障與權限錯誤。
- Asset、Threat、Vulnerability、Risk、Control 的關係。
- Authentication、Authorization、Accounting；Least Privilege、Defense in Depth。
- Patch、Backup、Logging、MFA 都是不同控制，不互相取代。

### Lab 90 分鐘

- 對本月 Lab 環境做簡易資產清單與風險表：資產、威脅、弱點、影響、控制。
- 檢查 Ubuntu 更新、使用者、Listening Port、UFW、SSH 設定；只在自己的 VM 內操作。
- 建立一次可還原的 VM Snapshot，並說明它為何不是正式備份。
- 寫一份 10 條基礎 Hardening Checklist。

### Debug Lab

故意讓 Nginx 以不必要的開放 Port 或過寬權限運作，找出暴露面並縮小。

### ⚠️ 最容易卡住的地方

『有防火牆』不等於安全；錯誤規則、過寬權限、未修補服務與缺少日誌仍會形成風險。

### AWS 對照（補充，不延伸成獨立課程）

Well-Architected Security Pillar、IAM、Security Group、CloudTrail、Encryption 都是分層控制。

### 職務／公司技能備註

Network Security Engineer 最直接；AWS 架構師、DevSecOps、SI、MIS 都需要。Security+ 會以情境題測責任與控制。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 25｜Firewall、ACL、Port、VPN 與方向判斷

### 今日驗收目標

> ACL 決策流程、VPN 架構圖、5 題方向判斷。

### 理論 90 分鐘

- Stateless ACL 與 Stateful Firewall 的概念差異。
- Source／Destination IP、Protocol、Source／Destination Port；Client 通常使用臨時來源 Port。
- Inbound／Outbound 取決於觀察設備與介面，不是以『網際網路方向』死背。
- ACL 放置位置與順序；First Match、Implicit Deny。
- VPN 提供加密通道與身分驗證，不保證兩端主機本身安全。

### Lab 90 分鐘

- Packet Tracer 使用 Standard／Extended ACL 限制特定來源或服務。
- 設計三條規則：允許內部到 Web、拒絕某網段 SSH、保留必要回應；逐條預測。
- Ubuntu UFW 只允許 Host 到 SSH，其他來源拒絕（依本機環境安全執行）。
- 畫出 Site-to-Site VPN 對應企業機房與 AWS VPC 的架構圖。

### Debug Lab

故意把 ACL 套錯 Interface 或 Direction，使用封包路徑圖找出錯誤。

### ⚠️ 最容易卡住的地方

ACL 題先畫封包進哪個介面、出哪個介面，再決定 in／out；直接背『靠近來源／目的』容易在拓樸題失誤。

### AWS 對照（補充，不延伸成獨立課程）

Security Group 是 Stateful；NACL 是 Stateless 且作用於 Subnet。Site-to-Site VPN 連接 VPC 與機房。

### 職務／公司技能備註

Firewall／ADC／Network Security Engineer 技能高度相關；AWS 架構師與 SI 也直接使用。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 26｜系統化 Troubleshooting 與封包證據

### 今日驗收目標

> 5 份迷你故障紀錄與 1 份完整 Incident Report。

### 理論 90 分鐘

- 建立 Baseline；先確認正常狀態才知道異常。
- 症狀、Root Cause、Contributing Factor、Fix、Workaround、Prevention。
- 變更一次一項；保留回復方式；問題解決後驗證與文件化。
- 遠端 on-call 的價值在於快速縮小範圍與清楚交接。

### Lab 90 分鐘

- 由自己或 AI 隨機選 5 個故障：介面關閉、Mask 錯、缺 Route、DNS 錯、Service 停止、Firewall 阻擋、權限錯誤。
- 每案只使用有目的的命令，記錄『命令 → 預期 → 實際 → 下一步』。
- 至少一案使用 Wireshark 或 Packet Tracer Simulation Mode 取得封包證據。
- 撰寫一份標準 Incident Report。

### Debug Lab

今天所有 Lab 都是 Debug；禁止以重裝系統作第一步。

### ⚠️ 最容易卡住的地方

修好不等於知道原因。若無法說明哪一項證據排除了哪些假設，代表仍是碰巧修好。

### AWS 對照（補充，不延伸成獨立課程）

CloudWatch、CloudTrail、VPC Flow Logs、Load Balancer Health Check 分別提供不同層級證據。

### 職務／公司技能備註

技術客服、SI、DevOps、SRE、MIS、AWS Support 全部直接使用；VMware Technical Support 尤其重視問對問題與 Case 紀錄。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 27｜API、JSON、Controller-based Networking 與自動化觀念

### 今日驗收目標

> JSON 筆記、一次 API 呼叫紀錄、簡單讀取腳本。

### 理論 90 分鐘

- API 是系統間約定的操作介面；Request、Response、Method、Status Code、Authentication。
- JSON Object、Array、Key、Value；資料型態與巢狀結構。
- 傳統逐台 CLI 與 Controller／Automation 的差異。
- CCNA v1.1 會觸及 Automation、AI/ML 基礎與 REST API；目標是看懂，不要求成為程式設計師。

### Lab 90 分鐘

- 用瀏覽器或 PowerShell `Invoke-RestMethod` 呼叫一個不需密鑰的公開測試 API。
- 將 JSON 回應整理成表格，指出 Object、Array、String、Number、Boolean。
- 寫一個簡單 PowerShell 或 Python 腳本，讀取本機 JSON 檔並輸出設備名稱與 IP。
- 把 Ansible Inventory 或網路設備清單轉成 YAML／JSON 對照。

### Debug Lab

故意拿錯 Key、製造逗號或引號錯誤，閱讀 Parser Error。

### ⚠️ 最容易卡住的地方

API 成功回 HTTP 200 不代表內容符合需求；要同時驗證狀態碼、資料結構與業務結果。

### AWS 對照（補充，不延伸成獨立課程）

AWS Console 背後大量操作都可透過 API、CLI、SDK 執行；架構師需要理解可自動化與可治理性。

### 職務／公司技能備註

DevOps、SRE、DevOps 與 Cloud-native 團隊最直接；AWS 架構師也必須能與開發及平台團隊討論 API 與自動化。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 28｜整合專題設計：小型企業混合架構

### 今日驗收目標

> 需求文件、架構圖、IP/VLAN/規則表。

### 理論 90 分鐘

- 需求先於產品：使用者數量、服務、可用性、安全、管理、預算、成長。
- 將網路、系統、身分、服務、日誌、自動化放在同一張圖。
- 區分 Functional Requirement 與 Non-functional Requirement。
- 建立 Assumption、Constraint、Risk；不知道的條件要標記，不自行補成事實。

### Lab 90 分鐘

- 設計虛擬公司：辦公室 VLAN 10、伺服器 VLAN 20、管理 VLAN 99；Router、DHCP、DNS、Ubuntu Web、Windows AD（可只畫不全建）。
- 畫出 IP Plan、VLAN Table、Route、Firewall Rule、服務相依關係。
- 加入 AWS 對照：VPC、Public／Private Subnet、EC2、ALB、Route 53、Site-to-Site VPN，只畫架構不建立付費資源。
- 在 GitHub 建立 `project/requirements.md` 與 `project/architecture.md`。

### Debug Lab

在設計中刻意加入三個問題：CIDR 重疊、單一 DNS、過寬 Firewall；完成 Review 時找出。

### ⚠️ 最容易卡住的地方

架構圖若只有產品 Logo 而沒有資料流、信任邊界與失敗情境，無法用來排錯或評估。

### AWS 對照（補充，不延伸成獨立課程）

今天是本月 AWS 比重最高的一天，但仍以傳統基礎映射到 VPC 架構，不深入考證照題。

### 職務／公司技能備註

AWS Solutions Architect 的核心是需求訪談、取捨與設計；SI 架構工程師也做類似工作，只是產品與交付範圍不同。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 29｜整合專題建置、故障注入與公司技能映射

### 今日驗收目標

> 可展示專題、故障報告、技能興趣矩陣。

### 理論 90 分鐘

- 建置順序：底層連通 → 位址／路由 → 基礎服務 → 身分／權限 → 應用 → 安全 → 監控。
- Acceptance Criteria 要可測量，例如『Client 可透過 DNS 名稱開啟 Web』。
- 故障注入是驗證理解，不是故意製造混亂；每次要有還原點。

### Lab 90 分鐘

- 在 Packet Tracer 完成可建置的 VLAN、Trunk、Router-on-a-Stick／L3 Routing、DHCP、基本 ACL。
- Ubuntu 提供 Nginx；Windows Server／AD 可依硬體資源選做，無法同時開機可用文件與截圖證明。
- 用 Ansible 重建 Nginx 設定；Git 保存每次里程碑。
- 注入至少三個故障並由零開始排查。
- 建立技能對照表：技能 → 我是否喜歡 → 我是否能持續練 → 對應職位 → 對應公司案例。

### Debug Lab

三個故障至少分屬 Network、Service、Permission／Security 不同層。

### ⚠️ 最容易卡住的地方

專題不是功能越多越好；能清楚展示需求、設計、驗證、故障與改進，比堆產品名稱更有價值。

### AWS 對照（補充，不延伸成獨立課程）

把本地專題說明成未來可遷移的 AWS 架構，但不要聲稱已做過未實作的 AWS 服務。

### 職務／公司技能備註

以 VMware Technical Support、Network Security Engineer、DevOps Engineer、SI Engineer 等職稱比較技能內容，不預先替自己決定。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


## Day 30｜總驗收、職涯判讀與 9/14 開課銜接

### 今日驗收目標

> 最終測驗、專題 README、個人技能興趣矩陣、開課銜接清單。

### 理論 90 分鐘

- 重新走一次完整資料流：Client → DNS → L2 → Gateway → Route/NAT/VPN → Firewall → Server Process → Response。
- 分清 SAA-C03（Associate）與 SAP-C02（Professional）；沒有『SAA Pro』這個正式名稱。
- AWS 官方將 SAP-C02 目標考生描述為具兩年以上使用 AWS 設計與實作雲端解決方案的經驗。證照沒有強制工作年資門檻，但證照本身不能替代架構取捨、建置、故障與文件證據。
- 職涯探索結論以 Memo 與實作證據為主，不因一天覺得困難就排除一條路。

### Lab 90 分鐘

- 完成最終測驗，不查筆記先作答，再針對錯題回到 Lab。
- 用 10 分鐘口頭解釋專題：需求、架構、封包路徑、安全、故障、AWS 對照。
- 整理 GitHub README：學到什麼、做了什麼、遇到什麼問題、如何驗證；不要寫成證照關鍵字清單。
- 建立開課後追蹤表：正式課程每週補充哪些章節、哪些技術想深入。
- 完成工作條件面試清單：是否輪班、on-call 頻率、是否長期駐點、客戶現場比例、AWS／on-prem 比例、教育訓練與考核方式。

### Debug Lab

請另一個人或 AI 只看你的 README 重現其中一個 Lab；若無法重現，補文件。

### ⚠️ 最容易卡住的地方

『會做』與『能清楚重現、說明與交接』是不同能力；架構與維運工作都要求後者。

### AWS 對照（補充，不延伸成獨立課程）

本月成果不是把自己包裝成 AWS 架構師，而是建立未來學 SAA-C03、做 AWS Lab 與累積實務的底層能力。

### 職務／公司技能備註

暫定主線仍是 AWS 雲端架構師；DevOps、SRE、SI、MIS 是你在實作過程中觀察興趣與工作型態的比較組。

### 完成清單

- [ ] 能不用照抄，口頭說明今天的核心流程
- [ ] 完成 Lab 並保存輸出或截圖
- [ ] 至少記錄一個錯誤、假設、測試與結果
- [ ] Git Commit 今日變更

### 每日 Memo（選填，不列入完成條件）

- 今天最有興趣的內容：
- 今天最沒興趣的內容：
- 我遇到的具體錯誤／現象：
- 我採取過的診斷步驟：
- 我仍然說不清楚的問題：
- 這項技能可能對應的職位／公司案例：
- 我對這類工作的興趣（0–5）：
- 明天需要補的內容：


---

# 7. 每週測驗與解析

> 規則：先在紙上或另一個 Markdown 檔作答，再展開答案。題目為自行設計的 CCNA／實務風格題，不是外流考題。

## 第 1 週測驗：封包、ARP、IPv4、Subnetting

1. 主機 A 為 `192.168.1.10/24`，主機 B 為 `192.168.2.20/24`。A 要傳給 B 時，A 會 ARP 查詢誰的 MAC？
2. Switch 收到一個 Frame，目的 MAC 不在 MAC Table 時會怎麼做？
3. `192.168.10.130/26` 的 Network Address 與 Broadcast Address 是什麼？
4. 為何兩台主機 IP 看似同一段，仍可能因 Mask 不一致而無法正常溝通？
5. Wireshark 中 DNS Query 成功，但網站仍打不開，至少列出三個其他可能原因。
6. `/27` 每個子網共有多少個 IPv4 位址？傳統情況下有多少可用 Host？
7. Frame、Packet、Segment 各主要對應哪一層？
8. Default Gateway 必須與主機位於什麼關係？
9. ARP Request 通常是 Broadcast 還是 Unicast？ARP Reply 呢？
10. `169.254.x.x` 最常提示什麼問題？

<details>
<summary>展開答案與理由</summary>

1. A 會查 Default Gateway 在 A 所在 LAN 的 MAC，因 B 不在本地網段。
2. 在該 VLAN 內，除來源 Port 外 Flood。
3. /26 Block Size 64；130 位於 128–191，所以 Network `192.168.10.128`，Broadcast `192.168.10.191`。
4. 雙方各自用自己的 Mask 判斷本地／遠端，可能做出不同決策，形成不對稱行為。
5. Route／Gateway、Firewall、TCP Port、Proxy、TLS、Web Service 停止、應用設定錯誤等。
6. 32 個總位址；傳統可用 Host 30 個。
7. Ethernet Frame：L2；IP Packet：L3；TCP Segment：L4。
8. Gateway 的 IP 必須在主機可直接到達的同一個 Layer 3 Subnet。
9. Request 通常 Broadcast；Reply 通常 Unicast。
10. DHCP 租約未取得，主機使用 APIPA；仍要查 DHCP Client、Server、Relay、VLAN、線路等原因。

</details>

## 第 2 週測驗：VLAN、STP、Routing、DHCP/DNS/NAT

1. Trunk 已建立，為何 VLAN 10 與 VLAN 20 仍不能直接互通？
2. STP 選 Root Bridge 時首先比較什麼？
3. 一台 Router 同時有 `10.0.0.0/8`、`10.10.0.0/16`、`10.10.10.0/24`，目的 `10.10.10.50` 使用哪條？
4. 有去程 Static Route，但回程沒有，Ping 會怎樣？
5. Default Route 的 Prefix 是什麼？何時使用？
6. DHCP DORA 四個步驟依序為何？
7. 能 Ping `8.8.8.8`，但 `example.com` 無法解析，優先檢查什麼？
8. PAT 為何能讓多台內部主機共用一個 Public IP？
9. ACL 套錯 Direction 為何可能完全沒效果？
10. Native VLAN mismatch 可能造成什麼問題？
11. TTL 的主要目的？
12. IPv6 是否使用 Broadcast？

<details>
<summary>展開答案與理由</summary>

1. Trunk 只承載多個 VLAN；跨 VLAN 仍需 Layer 3 Routing。
2. Bridge ID，包含 Priority 與 MAC 等欄位；實務推導先比較較低 Bridge ID。
3. `10.10.10.0/24`，因 Longest Prefix Match 最精確。
4. Request 可能到達，但 Reply 無法返回，因此 Ping 失敗。
5. `0.0.0.0/0`；沒有更精確匹配時使用。
6. Discover、Offer、Request、Acknowledgment。
7. Client 的 DNS Server、DNS 可達性、查詢回應與 Cache。
8. 同時轉換來源 IP 與來源 Port，以不同 Port 對應不同連線。
9. 封包沒有在所選介面以所選方向經過該 ACL。
10. Untagged Traffic 可能進入錯誤 VLAN，並產生告警或連線異常。
11. 防止 Packet 在路由迴圈中永久存在；每經 L3 Hop 遞減。
12. 不使用 Broadcast，改用 Multicast 等機制。

</details>

## 第 3 週測驗：Linux、VMware、Windows、AD

1. Linux 目錄 `x` 權限代表什麼？
2. `chmod 640 file` 對 Owner、Group、Other 分別給什麼權限？
3. Nginx 連不上時，列出至少五個依序檢查項目。
4. `Connection refused` 與 `Timeout` 在初步判讀上有何差異？
5. VMware NAT、Bridged、Host-only 各適合什麼情境？
6. Snapshot 為何不能視為完整備份？
7. AD Client 為何通常要使用 AD DNS？
8. Authentication 與 Authorization 差別？
9. Git Staging Area 的用途？
10. Ansible Idempotency 是什麼？

<details>
<summary>展開答案與理由</summary>

1. Traverse／進入目錄與存取路徑中的項目。
2. Owner `rw-`、Group `r--`、Other `---`。
3. 主機可達、Route、DNS、Process、Listening Port、Firewall、設定檔、Log、權限。
4. Refused 常表示路徑到主機但 Port 無服務或被主動拒絕；Timeout 常見於路徑、Firewall 或無回覆。只是初步線索，不是絕對結論。
5. NAT：VM 透過 Host 連外；Bridged：VM 直接成為 LAN 主機；Host-only：只與 Host／同 Host-only 網路溝通。
6. Snapshot 依賴原 VM Disk Chain，長期保留有效能與損毀風險，且不是獨立異地副本。
7. AD 依賴特定 DNS Records 定位 Domain Controller 與服務。
8. Authentication 驗證你是誰；Authorization 判斷你能做什麼。
9. 選擇下一個 Commit 要包含的變更。
10. 重複執行仍達成同一目標狀態，沒有不必要副作用。

</details>

## 最終測驗：整合與職涯

1. 使用者輸入 `https://app.example.com` 到看到頁面，列出至少八個可能步驟或元件。
2. Security Group 與 NACL 的核心差異？
3. VPC Route Table 與 Cisco Routing Table 共同的核心選路概念？
4. DevOps 與 SRE 是否只是工具清單？分別關注什麼？
5. SI 與 MIS 的客戶／服務對象有何常見差異？
6. 為何只拿 SAP-C02 不能證明已能獨立做大型 AWS 架構？
7. 一份可說服面試官的 Lab 紀錄應包含哪些證據？
8. 你可接受遠端 on-call 但不希望輪班，面試至少要問哪四題？
9. ACL 題目判斷 in／out 的可靠方法？
10. 如何證明 Ansible Playbook 具基本 Idempotency？
11. 架構圖除了產品 Logo，還應標示什麼？
12. 最終請依 Memo 回答：目前最想深入的三項技能、最不想做的兩種工作內容、仍未知的三個職缺條件。

<details>
<summary>展開參考答案</summary>

1. DNS Cache／Resolver、DNS Record、ARP／Gateway、Switch、Routing、NAT／VPN、Firewall、Load Balancer、Server Port、Application Process、TLS、回程等。
2. Security Group Stateful、綁定 ENI／資源；NACL Stateless、作用於 Subnet 並需考慮雙向規則。
3. Longest Prefix Match。
4. DevOps 是文化、流程與工具，提升交付速度與穩定性；SRE 把維運視為軟體與可靠性問題，關注 SLO、可用性、延遲、容量、事故與自動化。
5. SI 通常為多個外部客戶交付專案與產品；MIS 通常維護自己公司的內部 IT。實際公司仍可能混合。
6. 證照驗證考試範圍，無法單獨證明需求訪談、取捨、建置、事故、成本、組織溝通與交付經驗。
7. 需求、環境／版本、架構、步驟、輸出／截圖、錯誤、假設、測試、修正、驗收、限制。
8. 是否 24/7 輪班、on-call 頻率、能否遠端、實際被叫醒頻率、補償／補休、是否駐點、事故後工時安排。
9. 畫出封包相對於要套用 ACL 的那台設備，是進入哪個介面、離開哪個介面。
10. 執行兩次；第二次大部分 Task 應為 `ok` 而非持續 `changed`，且目標狀態一致。
11. 資料流、信任邊界、Subnet/VLAN、Route、安全規則、相依服務、HA、監控與失敗情境。
12. 沒有標準答案；必須引用自己的 Memo，不臆測。

</details>

---

# 8. CCNA 最容易卡住的主題優先表

| 優先 | 主題 | 必須先理解的核心 | 自我驗收 |
|---|---|---|---|
| 1 | Subnetting / VLSM | Prefix、Block Size、Network/Broadcast、需求反推 | 10 題 15 分鐘，正確率 80% 以上 |
| 2 | ARP + Default Gateway | 遠端 IP 對應的是 Gateway MAC | 能在 Simulation Mode 逐 Frame 解釋 |
| 3 | VLAN / Trunk | 分段與承載，不等於跨 VLAN Routing | 能從 `show vlan`、`show trunk` 找錯 |
| 4 | STP | Root → Root Port → Designated → Alternate 的推導順序 | 能不用背答案判斷三角拓樸 |
| 5 | Routing / LPM | 路由是雙向、最精確 Prefix 優先 | 能逐條解讀 `show ip route` |
| 6 | ACL Direction | 相對於設備介面畫封包方向 | 5 題至少 4 題正確 |
| 7 | DHCP/DNS/NAT | 三者責任分開，錯誤訊息分開 | 能設計三種不同故障 |
| 8 | IPv6 | Link-local、ND、SLAAC、無 Broadcast | 能完成兩網段 IPv6 Ping |
| 9 | Automation / JSON | 資料結構、API、Controller 思維 | 能讀取 JSON 並抓出指定欄位 |

---

# 9. 每日錯誤紀錄模板

```markdown
# Incident / Lab Error

- 日期：
- Lab：
- 原本目標：
- 環境與版本：
- 實際現象：
- 完整錯誤訊息：
- 最近一次變更：
- 初始假設：
  1.
  2.
  3.
- 診斷紀錄：
  - 命令／操作：
  - 預期：
  - 實際：
  - 排除了什麼：
- Root Cause：
- Fix：
- 驗證方式：
- 是否已還原不必要變更：
- 如何預防：
- 尚未確認的限制：
```

---

# 10. 技能興趣矩陣

每週更新一次。不要只寫「喜歡／不喜歡」，寫出你喜歡的是哪個工作動作。

| 技能／工作動作 | 實作證據 | 興趣 0–5 | 願意持續練 0–5 | 對應職位 | 公司案例 |
|---|---|---:|---:|---|---|
| 子網路與路由規劃 |  |  |  | AWS Architect、Network、SI | 鉅立、宏燁 |
| 封包與故障定位 |  |  |  | Support、Network Security、SRE | 零壹、鉅立 |
| Linux 系統管理 |  |  |  | Cloud、DevOps、SRE | 雷麒、宏燁 |
| VMware／私有雲 |  |  |  | VMware Engineer、SI | 零壹、宏燁 |
| Windows／AD |  |  |  | MIS、Windows SI、Hybrid Cloud | 零壹、宏燁 |
| Git／自動化 |  |  |  | DevOps、SRE、Cloud Engineer | 雷麒、宏燁 |
| 資安規則與風險 |  |  |  | Cloud Architect、Security Engineer | 鉅立、宏燁 |
| 需求整理與架構圖 |  |  |  | AWS Architect、Pre-sales、SI Architect | 四家公司皆可能用到 |
| 客戶技術支援 |  |  |  | Technical Support、SI、FAE | 零壹、鉅立 |
| 事故 on-call |  |  |  | DevOps、SRE、Support | 逐職缺確認 |

---

# 11. 正式開課後如何延續

9 月 14 日後，不建議繼續照本手冊每天三小時額外衝刺。正式課程已是高時數訓練，改採：

1. 課前 15 分鐘：看當天相關 Day 的圖與錯題。
2. 課後 30 分鐘：把老師教材補進原有筆記，不重抄一份。
3. Lab 卡住時：沿用 Incident Template。
4. 每週末：更新技能興趣矩陣與輪班／on-call／駐點職涯問題。
5. 課程進度超前時，再決定是否增加 AWS VPC、IAM、EC2、Load Balancer、Auto Scaling、RDS、Route 53、CloudWatch 與 IaC 的專門 Lab。

---


# 12. 指令第一次登場的實戰說明規格

每個指令第一次出現時，必須依下列格式記錄：

```markdown
### 指令：`ip addr show`

**解決什麼問題**  
查看 Linux 所有網路介面與 IP 位址。

**語法拆解**
- `ip`：Linux 的網路設定查詢與管理工具。
- `addr`：address 的縮寫，操作 IP 位址。
- `show`：只顯示，不修改設定。

**預期看到**
- 介面名稱，例如 `ens33`。
- `state UP` 表示介面啟用。
- `inet 192.168.x.x/24` 是 IPv4 位址與 Prefix。

**常見錯誤**
- 沒有 `inet`：可能尚未取得 DHCP 位址。
- `state DOWN`：介面未啟用或虛擬網卡未連接。

**下一步排查**
`ip link show` → `ip route show` → `resolvectl status`

**如何驗證修好**
重新執行 `ip addr show`，並以 `ping -c 4 <gateway-IP>` 驗證 Layer 3 連通。
```

後續再次使用同一指令時，只需寫操作目標，不重複整段說明。

---

# 13. 最終 DevOps Project：Git → CI → Ansible → Nginx → Health Check → Recovery

## 13.1 完成定義

Project 必須能展示：

1. 使用 Feature Branch 修改 Nginx 首頁。
2. Pull Request 或 Push 觸發 GitHub Actions。
3. GitHub-hosted Runner 執行 YAML 與 Ansible Syntax Check。
4. CI 通過後，在本機 Ubuntu 手動執行 Ansible 部署。
5. 自動以 HTTP Status Code 驗證服務健康。
6. 故意部署錯誤設定，依 Log 找到 Root Cause。
7. 使用 Git Revert 或前一版本重新部署完成回復。
8. 寫一份 Incident Report 與 README 操作證據。

> Repository 為 Public，因此不使用連到本機 VM 的 self-hosted runner，也不提交 SSH Private Key。

## 13.2 建議目錄

```text
.
├── .github/workflows/ci.yml
├── .yamllint.yml
├── ansible/
│   ├── ansible.cfg
│   ├── inventory.example.ini
│   ├── deploy.yml
│   └── templates/index.html.j2
├── scripts/health-check.sh
├── docs/
│   └── incident-template.md
└── README.md
```

## 13.3 Ubuntu 首次準備指令

### `sudo apt update`

**功能**：下載目前啟用的 APT 軟體來源索引，不會直接升級套件。

```bash
sudo apt update
```

- `sudo`：以系統管理權限執行下一個命令。
- `apt`：Ubuntu/Debian 套件管理工具。
- `update`：更新可安裝套件清單。

驗證：最後不應出現無法解析網域或 Repository 簽章錯誤。

### `sudo apt install -y ansible git curl`

**功能**：安裝 Ansible、Git 與 curl。

```bash
sudo apt install -y ansible git curl
```

- `install`：安裝指定套件。
- `-y`：對確認問題自動回答 yes；先確認套件名稱正確再使用。
- `curl`：用來發送 HTTP Request 做 Health Check。

驗證：

```bash
ansible --version
git --version
curl --version
```

## 13.4 Ansible Inventory

建立只在本機使用、不提交的 `ansible/inventory.local.ini`：

```ini
[web]
web01 ansible_host=192.168.1.50 ansible_user=benson

[web:vars]
ansible_python_interpreter=/usr/bin/python3
```

將 IP 與使用者改成 Ubuntu VM 實際值。

### `ansible -i ... all -m ping`

**功能**：確認 Ansible 能以 SSH 連線並在遠端執行 Python Module；不是 ICMP Ping。

```bash
ansible -i ansible/inventory.local.ini all -m ping
```

- `-i`：指定 Inventory 檔。
- `all`：對 Inventory 中所有 Host 執行。
- `-m ping`：使用 Ansible Ping Module。

預期：

```text
web01 | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
```

常見錯誤：

- `UNREACHABLE!`：先查 IP、SSH、帳號、防火牆。
- `Permission denied`：查 SSH Key／Password 與 User。
- 找不到 Python：確認 `ansible_python_interpreter`。

## 13.5 Playbook

`ansible/deploy.yml`：

```yaml
---
- name: Deploy Nginx website
  hosts: web
  become: true

  vars:
    nginx_package: nginx
    web_root: /var/www/html

  tasks:
    - name: Install Nginx
      ansible.builtin.apt:
        name: "{{ nginx_package }}"
        state: present
        update_cache: true

    - name: Deploy homepage
      ansible.builtin.template:
        src: templates/index.html.j2
        dest: "{{ web_root }}/index.html"
        owner: root
        group: root
        mode: "0644"
      notify: Reload Nginx

    - name: Ensure Nginx is enabled and running
      ansible.builtin.service:
        name: nginx
        enabled: true
        state: started

  handlers:
    - name: Reload Nginx
      ansible.builtin.service:
        name: nginx
        state: reloaded
```

### Syntax Check

```bash
ansible-playbook \
  -i ansible/inventory.local.ini \
  ansible/deploy.yml \
  --syntax-check
```

- `ansible-playbook`：執行 Playbook。
- `--syntax-check`：只檢查 YAML 與 Playbook 結構，不部署。
- `\`：Bash 的續行符號；也可寫成同一行。

### Check Mode

```bash
ansible-playbook \
  -i ansible/inventory.local.ini \
  ansible/deploy.yml \
  --check --diff
```

- `--check`：模擬可能變更；不是所有 Module 都能完整模擬。
- `--diff`：顯示檔案內容可能如何改變。

### 實際部署

```bash
ansible-playbook \
  -i ansible/inventory.local.ini \
  ansible/deploy.yml
```

再執行第二次，理想情況應大多顯示 `ok` 而不是每次都 `changed`，用來驗證基本 Idempotency。

## 13.6 Health Check Script

`scripts/health-check.sh`：

```bash
#!/usr/bin/env bash
set -euo pipefail

TARGET_URL="${1:-http://192.168.1.50}"
EXPECTED_STATUS="200"

actual_status="$(
  curl \
    --silent \
    --show-error \
    --output /dev/null \
    --write-out '%{http_code}' \
    --max-time 5 \
    "${TARGET_URL}"
)"

if [[ "${actual_status}" != "${EXPECTED_STATUS}" ]]; then
  echo "Health check failed: expected ${EXPECTED_STATUS}, got ${actual_status}" >&2
  exit 1
fi

echo "Health check passed: ${TARGET_URL} returned HTTP ${actual_status}"
```

首次執行：

```bash
chmod +x scripts/health-check.sh
./scripts/health-check.sh http://192.168.1.50
```

- `chmod +x`：增加執行權限。
- `./`：執行目前目錄中的檔案。
- `set -euo pipefail`：遇到命令失敗、未定義變數或 Pipeline 失敗時停止。
- `curl --write-out '%{http_code}'`：只取回 HTTP Status Code。
- `exit 1`：回傳非零狀態，讓 CI 或操作者知道驗收失敗。

## 13.7 GitHub Actions CI

`.github/workflows/ci.yml`：

```yaml
name: Validate DevOps project

on:
  push:
    branches:
      - main
  pull_request:

permissions:
  contents: read

jobs:
  validate:
    runs-on: ubuntu-latest

    steps:
      - name: Check out repository
        uses: actions/checkout@v4

      - name: Set up Python
        uses: actions/setup-python@v6
        with:
          python-version: "3.13"

      - name: Install validation tools
        run: |
          python -m pip install --upgrade pip
          pip install ansible-core ansible-lint yamllint

      - name: Validate YAML
        run: yamllint .

      - name: Validate Ansible syntax
        run: ansible-playbook -i ansible/inventory.example.ini ansible/deploy.yml --syntax-check

      - name: Run ansible-lint
        run: ansible-lint ansible/deploy.yml
```

`.yamllint.yml`：

```yaml
---
extends: default

rules:
  line-length:
    max: 120
    level: warning
  truthy:
    allowed-values:
      - "true"
      - "false"
      - "on"
    check-keys: false
```

## 13.8 故障注入與回復

至少完成三種：

1. Template 路徑打錯 → Ansible 找不到檔案。
2. Nginx 設定檔語法錯誤 → `nginx -t` 失敗。
3. Firewall 阻擋 80/TCP → Process 正常但 Health Check Timeout。

排查順序：

```bash
systemctl status nginx --no-pager
sudo nginx -t
sudo ss -lntp
sudo journalctl -u nginx --since "15 minutes ago" --no-pager
sudo ufw status verbose
```

每個指令第一次使用時，依「功能 → 參數 → 預期 → 常見錯誤 → 驗證」格式補進自己的 Lab 筆記。

### Git Revert

```bash
git log --oneline --decorate -n 10
git revert <錯誤Commit-SHA>
git push origin main
```

- `git log --oneline`：以一行顯示一個 Commit。
- `git revert`：建立一個新 Commit 反向取消指定 Commit，適合已 Push 的公開歷史。
- 不建議以 `git reset --hard` 改寫共享分支歷史。

## 13.9 Project 驗收清單

- [ ] CI 在 Pull Request 與 main Push 都會執行。
- [ ] YAML、Ansible Syntax、ansible-lint 全數通過。
- [ ] Inventory 真實 IP 與秘密資料未進版控。
- [ ] 第一次部署顯示必要 `changed`。
- [ ] 第二次部署大多顯示 `ok`。
- [ ] Health Check 回傳 HTTP 200。
- [ ] 三個故障都有完整錯誤訊息、假設、證據、Root Cause、Fix 與驗證。
- [ ] 至少一次使用 `git revert` 完成回復。
- [ ] README 有架構圖、操作步驟、限制與實際截圖。
- [ ] 能在 10 分鐘內說明整條流程，而不是只展示成功畫面。

---

# 12. 官方教材與查核來源

## 課程與工具

- 使用者提供：《資展國際 雲端網路與資安工程師就業養成班（第 5 梯次）招生簡章》
- Cisco CCNA 200-301 v1.1 Exam Topics  
  https://learningcontent.cisco.com/documents/marketing/exam-topics/200-301-CCNA-v1.1.pdf
- Cisco Networking Academy / Packet Tracer  
  https://www.cisco.com/site/us/en/learn/training-certifications/training/netacad/index.html
- Packet Tracer Download Instructions  
  https://skillsforall.com/skillsforall/files/Cisco_Packet_Tracer_Download_and_Installation_Instructions.pdf
- VMware Workstation / Fusion  
  https://www.vmware.com/products/desktop-hypervisor/workstation-and-fusion
- Broadcom：Desktop Hypervisor 免費授權與下載說明  
  https://knowledge.broadcom.com/external/article/368667/download-and-license-vmware-desktop-hype.html
- Ubuntu Server Tutorial  
  https://ubuntu.com/server/docs/tutorial/
- Ubuntu Server Networking  
  https://ubuntu.com/server/docs/how-to/networking/
- Windows Server 2025 Evaluation  
  https://www.microsoft.com/en-us/evalcenter/download-windows-server-2025
- Ansible Getting Started  
  https://docs.ansible.com/projects/ansible/latest/getting_started/index.html
- Pro Git（免費官方書）  
  https://git-scm.com/book/zh-tw/v2
- Wireshark User’s Guide  
  https://www.wireshark.org/docs/wsug_html_chunked/

## AWS 與職務定義

- AWS Certified Solutions Architect – Professional  
  https://aws.amazon.com/tw/certification/certified-solutions-architect-professional/
- SAP-C02 Exam Guide（目標考生經驗）  
  https://docs.aws.amazon.com/aws-certification/latest/solutions-architect-professional-02/solutions-architect-professional-02.html
- AWS Skill Builder（有免費數位教材）  
  https://aws.amazon.com/training/digital/
- AWS：What is DevOps  
  https://aws.amazon.com/tw/devops/what-is-devops/
- Google SRE  
  https://sre.google/
- Google SRE Resources  
  https://sre.google/resources/

## 公司案例（查核日：2026-07-25）

- 零壹科技公司概述  
  https://www.zerone.com.tw/about/zerone
- 零壹科技 VMware by Broadcom  
  https://www.zerone.com.tw/product/brand/vmware-by-broadcom/
- 雷麒科技官網  
  https://www.lctech.com.tw/
- 雷麒科技 Cloud／DevOps 職務案例（職缺可能變動）  
  https://www.cake.me/companies/lctech_/jobs/cloud-system-engineer-devops-engineer-taoyuan
- 鉅立資訊官網  
  https://www.jlead.com.tw/zh/
- 宏燁資訊官網  
  https://www.asgard.com.tw/
- 宏燁資訊公司／服務介紹（職缺內容可能變動）  
  https://www.104.com.tw/company/7f39r7c

---

# 13. 完成本月後的判定標準

不要以「看完多少影片」判斷完成。符合以下條件才算完成：

- [ ] 30 天至少完成 24 天；缺少的 6 天有明確補課標記
- [ ] 每週測驗都有作答與錯因
- [ ] 至少 15 份 Debug／Incident 紀錄
- [ ] Packet Tracer 可展示 VLAN、Routing、DHCP、NAT、ACL
- [ ] Ubuntu VM 可透過 SSH 管理並提供 Nginx
- [ ] Git 紀錄可看出學習過程，而不是最後一次全部上傳
- [ ] 至少一個 Ansible Playbook 可重複執行
- [ ] 完成小型企業混合架構文件與 AWS 對照
- [ ] 技能興趣矩陣有實作證據
- [ ] 能清楚說出自己「不知道哪些職缺條件」，並在面試中詢問，不自行臆測


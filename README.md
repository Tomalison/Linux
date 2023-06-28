# Linux學習紀錄

## 認識與建置Linux
- 甚麼是Linux，Debin、UBUNTU、CENTOS、FEDORA、RED HAT 她是一個自由開放的作業系統。
- 相關國際認證，操作的能力(活用知識)>>管理的能力(包含防火牆、檔案系統、帳號權限)>>服務的控制(套件、安全性規則做好、Shell、腳本)>>解決問題
- 認證 : LPIC(Linux Professional Institute)，各發行版共通的知識規範 101 102通過第一級認證 201 202通過第二級認證 PIC 301 通過第三級認證 302~306 / Red hat RHCE認證 要先通過RHCSA

#### 甚麼是ISO映像檔
- 安裝全新作業系統，通常會有光碟，但這個年代不太有光碟機，目前作業系統都會用光碟格式(ISO)釋出，所以目前Linux發行版都會用ISO格式發行，這是目前安裝的趨勢。大小都會落在數G/ 先準備磁碟空間有50G /或是用雲端空間與資源來建立Linux
#### VirtualBox:Windows虛擬機器軟體安裝
- 虛擬機器就是模擬另外一台機器的一個機制設計，市面上最常見的是VMware跟Oracle VirtualBox這兩套軟體，我們先選VirtualBox來下載，一路按下下一步到安裝，就會裝一些虛擬模擬的網路設備，就會出現如下圖介面
![image](https://github.com/Tomalison/Linux/assets/96727036/feb86dae-e74f-46c1-aed3-79cd3122d719)
- 打開瀏覽器，下載Red Had(rhel 8/ https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux/server/trial)企業版的ISO檔跟CentOS(https://centos.org/)
#### 安裝CentOS8.1與了解磁碟分割機
- 先按下Virtualbox的新增>>名稱選擇centos，底下類型就會自動偵測為Linux與Red Hat，記憶體至少要選為8GB(8192MB)>>立即建立虛擬硬碟>>VDI>>動態分配>>檔案位置和大小要選20GB
- ![image](https://github.com/Tomalison/Linux/assets/96727036/c46526af-f3b3-43fe-b817-4ab3bcea2bf1)
- ![image](https://github.com/Tomalison/Linux/assets/96727036/7576165d-9328-47c7-83bf-6809f21ce4b0)
- 開啟後，按下設定來設定這台虛擬機器>存放裝置>選到空的光碟機圖形>選到開機的映像檔>選擇磁碟檔/放入centos開機映像檔/CentOS8.1
- ![image](https://github.com/Tomalison/Linux/assets/96727036/463b2e95-c668-4be9-9b3f-0e30ded0ac1b)
- ![image](https://github.com/Tomalison/Linux/assets/96727036/366ded99-912c-4b8e-a4c8-e5abed2bd4c2)
- Install CentOS Linux 8>更改台灣時區>含GUI伺服器/RPM開發工具/科學支援/安全性工具/Legacy UNIX/效能工具/基本網站伺服器/系統工具>安裝目的地/自訂>點按這裡讓系統自動建立(C)
![image](https://github.com/Tomalison/Linux/assets/96727036/5325651d-4bdd-45d5-a54f-0c6d1e319290)
- 一個Linxu至少要有一個swap置換分割區，建議這個伺服器(對外服務)，可以多給他一些 > /var拆4G /先-4G才有足夠空間建立
- ![image](https://github.com/Tomalison/Linux/assets/96727036/dfa99420-f8c5-4112-8732-f122e606f0fe)
- 接受變更>網路和主機名(裝好要自動連線網路)先把開關打開>完成>開始安裝
- ![image](https://github.com/Tomalison/Linux/assets/96727036/6ddb58c1-cf06-4edc-a54a-afeeddd8ca66)
- 設定根密碼 root/自己設密碼
- ![image](https://github.com/Tomalison/Linux/assets/96727036/4d4ef0a3-c000-4e55-9a2b-f709fa057031)  <--讓此使用者成為管理員/需要密碼才能使用此帳號
- 




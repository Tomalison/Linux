# Linux學習紀錄

## 認識與建置Linux
- 甚麼是Linux，Debin、UBUNTU、CENTOS(GNOME圖形介面)、FEDORA、RED HAT 她是一個自由開放的作業系統。
- 相關國際認證，操作的能力(活用知識)>>管理的能力(包含防火牆、檔案系統、帳號權限)>>服務的控制(套件、安全性規則做好、Shell、腳本)>>解決問題
- 認證 : LPIC(Linux Professional Institute)，各發行版共通的知識規範 101 102通過第一級認證 201 202通過第二級認證 PIC 301 通過第三級認證 302~306 / Red hat RHCE認證 要先通過RHCSA

#### 甚麼是ISO映像檔
- 安裝全新作業系統，通常會有光碟，但這個年代不太有光碟機，目前作業系統都會用光碟格式(ISO)釋出，所以目前Linux發行版都會用ISO格式發行，這是目前安裝的趨勢。大小都會落在數G/ 先準備磁碟空間有50G /或是用雲端空間與資源來建立Linux
#### VirtualBox:Windows虛擬機器軟體安裝
- 虛擬機器就是模擬另外一台機器的一個機制設計，市面上最常見的是VMware跟Oracle VirtualBox這兩套軟體，我們先選VirtualBox來下載，一路按下下一步到安裝，就會裝一些虛擬模擬的網路設備，就會出現如下圖介面
![image](https://github.com/Tomalison/Linux/assets/96727036/feb86dae-e74f-46c1-aed3-79cd3122d719)
- 打開瀏覽器，下載Red Had(rhel 8/ https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux/server/trial)企業版的ISO檔跟CentOS(https://centos.org/)
- http://ftp.iij.ad.jp/pub/linux/centos-vault/8.1.1911/isos/x86_64/
#### 安裝CentOS8.1與了解磁碟分割機
- 先按下Virtualbox的新增>>名稱選擇centos，底下類型就會自動偵測為Linux與Red Hat，記憶體至少要選為8GB(8192MB)>>立即建立虛擬硬碟>>VDI>>動態分配>>檔案位置和大小要選20GB
 ![image](https://github.com/Tomalison/Linux/assets/96727036/c46526af-f3b3-43fe-b817-4ab3bcea2bf1)
 ![image](https://github.com/Tomalison/Linux/assets/96727036/7576165d-9328-47c7-83bf-6809f21ce4b0)
- 開啟後，按下設定來設定這台虛擬機器>存放裝置>選到空的光碟機圖形>選到開機的映像檔>選擇磁碟檔/放入centos開機映像檔/CentOS8.1
 ![image](https://github.com/Tomalison/Linux/assets/96727036/463b2e95-c668-4be9-9b3f-0e30ded0ac1b)
 ![image](https://github.com/Tomalison/Linux/assets/96727036/366ded99-912c-4b8e-a4c8-e5abed2bd4c2)
- Install CentOS Linux 8>更改台灣時區>含GUI伺服器/RPM開發工具/科學支援/安全性工具/Legacy UNIX/效能工具/基本網站伺服器/系統工具>安裝目的地/自訂>點按這裡讓系統自動建立(C)
![image](https://github.com/Tomalison/Linux/assets/96727036/5325651d-4bdd-45d5-a54f-0c6d1e319290)
- 一個Linxu至少要有一個swap置換分割區，建議這個伺服器(對外服務)，可以多給他一些 > /var拆4G /先-4G才有足夠空間建立
 ![image](https://github.com/Tomalison/Linux/assets/96727036/dfa99420-f8c5-4112-8732-f122e606f0fe)
- 接受變更>網路和主機名(裝好要自動連線網路)先把開關打開>完成>開始安裝
  ![image](https://github.com/Tomalison/Linux/assets/96727036/6ddb58c1-cf06-4edc-a54a-afeeddd8ca66)
- 設定根密碼 root/自己設密碼
 ![image](https://github.com/Tomalison/Linux/assets/96727036/4d4ef0a3-c000-4e55-9a2b-f709fa057031)  <--讓此使用者成為管理員/需要密碼才能使用此帳號
- 安裝完成要重啟之前，(顯示記憶體要調高不然會黑屏)先將底下的光碟機圖示按右鍵將掛載的iso檔勾選拿掉，然後重新啟動再第一個地方按Enter
- 一開始作一些必要的設定，同意條款然後設定完成
 ![image](https://github.com/Tomalison/Linux/assets/96727036/8e69d9ec-5260-41ed-97e4-d293a0a203ac)
- 選者漢語、台灣語；不給偵測位置、不設定線上帳號；Linux放在概覽，終端機_ifconfig可以顯示網路狀況 ip a也可以顯示
- 企業版類似安裝方式 red hat，只有在訂閱相關內容有點不同 其他都相同 紅帽的帳號要key入，新增訂閱設定。
#### 遠端登入到Linux畫面
- 目前他預設的ip _ enp0s3 的10.0.2.15 (NAT供給)，目前外部的windows或是Mac無法連線近來，因為Linux位於一個內部的虛擬網域裡面
- 所以我們先關閉這台Linux電源，回到virtualbox的那台主機開啟設定>網路>橋接介面卡>開啟Linux>終端機，就可以看到他的ip已經被更改。192.168.0.121/24
- 目前linux已經自動啟動了SSH服務，使用SSH客戶端工具可以連線，瀏覽器請輸入pietty>下載完成之後，開啟執行檔，輸入你的IP跟埠號/SSH連線
![image](https://github.com/Tomalison/Linux/assets/96727036/0eacb1fe-9c13-4e08-a289-a42ee59fabd5)
- key你的linux使用者帳密進入 ；MAC的做法則是工具列中的終端機使用者帳號@LINUX IP位置

## Linux基礎操作指令
#### Linux的開機流程
- Bios/UEFI(與硬體溝通的主程式) >GRUB(bootloader(硬碟啟動要載入的作業系統))>Kernel核心(使用者與電腦的溝通程式)>System
- ![image](https://github.com/Tomalison/Linux/assets/96727036/d6213754-ab9c-490a-9b0b-0caaf0b11e84)
- 登入後都必須要logout登出

#### 指令操作
- ![image](https://github.com/Tomalison/Linux/assets/96727036/95800c3c-38bb-424d-9b52-b29a20393977)
- 超級使用者跟一般使用者的命令提示字元是不一樣的，一般使用者最後是一個$號
- ![image](https://github.com/Tomalison/Linux/assets/96727036/fc94061b-2986-4e36-a8f7-16c95c496f65)
- ~代表自己的家目錄 pwd
- 如何變身成超級使用者 su -，root的密碼輸入就會變成特殊使用者，後面也會變成#號，要特別謹慎。
- 加上-才可以變身成為超級使用者的環境變數
- ![image](https://github.com/Tomalison/Linux/assets/96727036/a169a9ee-bcd3-4967-803a-10562cdd54ed)
- clear or ctrl+L都可以清除畫面
#### 基礎資料夾切換、列表、別名
- 切換資料夾 cd ..(目前資料夾的上一層，相對位置的切換) ； cd /home/tomsu25478(絕對位置的切換) ；cd ~(家目錄) ； ls 目錄下的檔案清單 ； ls -l(詳細檔案清單) ； ls -a(顯示全部資料包含隱藏資料) ； ls -al /
- centos 有一個alias 可以看到每個指令的別名(如下圖)
- ![image](https://github.com/Tomalison/Linux/assets/96727036/45bd8e55-7264-4431-a883-1c01c1c2af6b)
- 



![image](https://github.com/Tomalison/Linux/assets/96727036/5e99815d-99e5-40a3-ab5c-d336999862fa)![image](https://github.com/Tomalison/Linux/assets/96727036/065a9ecf-c255-480a-942c-f1d54cc6bb55)# Linux學習紀錄

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

#### Linux主要目錄與辯讀權限
- ![image](https://github.com/Tomalison/Linux/assets/96727036/d5d5f535-750c-46bc-ade0-d0f888ee49a8) 權限的表現字元，譬如說左邊的dr-xr-xr-x ，d代表是directory就是資料夾
- r=read w=write x=execute 檔案擁有者對他的權限；檔案傭有者同一族群的人的權限；other的權限
- ![image](https://github.com/Tomalison/Linux/assets/96727036/36598a05-8c9a-4bbe-ae5b-ba344cae0a0a)
- bin 或是sbin 依照檔案的權限直來決定是不是可執行，而不是用檔名來判斷 binary  ls /bin 都放在根目錄  ls /sbin是super user可以用的執行檔案(例如網管的軟體、關機、重開機等等)
- ls -l /etc 裡面放置了所有的設定檔，都是純文字檔，只有系統管理員可以修改這些檔案  ls -l /dev 所有裝置與設備  ls -l /home 如果你是一個擁有許多使用者的時候，如果要控制這些檔案使用額度，會再切一個分割區讓他放。
- root超級使用者的根目錄 /root，other無法讀取，只有超級使用者可以看到。
- usr許多套件軟體都會放在usr
- ![image](https://github.com/Tomalison/Linux/assets/96727036/9b6a81c7-3062-46d4-b081-c0f83da7fbd3)
- var變動性與系統等待排隊處理的檔案 (例如網頁的變動資料也會放在這
- opt非Linux預設安裝的軟體會放在這裡

#### 關機與重啟系統，SUDO指令
- 先變身為超級使用者 su -
- w可以看線上使用者 who也可以看
- shutdown用於關機 ， -h now(直接關機) -h 10(10分鐘後關機) -c(取消關機指令) 'Please back up your job' <可以做一些文字提醒
- reboot(重新開機)
- 管理者的話 就是輸入 sudo shutdown -h 10 ，輸入使用者密碼就可以用超級使用者的功能

#### 基本檔案操作_複製_搬移_刪除
- ls -al / 看一下目錄資訊
- cp (複製) 來源_目的地 /etc/ (設定膽)
- ![image](https://github.com/Tomalison/Linux/assets/96727036/b9828d26-2db8-4431-8e6d-affc9ad90953)
- ![image](https://github.com/Tomalison/Linux/assets/96727036/52b6095a-e5eb-454e-861b-b4ad133d0fed)
- cp /etc/fstab . <--就可以將這個資料夾複製到root裡
- cat指令可以看存文字內容
- cp fstab aa 可以複製成aa這個檔案
- cp aa /tmp 可以複製aa到 /tmp
- 如果要移動這個檔案，mv aa /tmp
- mv也常常拿來改檔名 mv fstab bb 這樣也可以改檔名
- 我想要刪除資料 rm /tmp/aa
- 要刪除資料夾也可以，我們先建立一個資料夾 mkdir dd
- mv bb /dd
- 如果要刪除空的資料夾可以用 rmdir dd
- rm -rf dd一層一層把所有資料刪除，將資料夾有資料的檔案同時刪除 要注意( rm -rf / 可能就把全部資料全刪除)

#### 學怎麼用LINUX，而不是背指令
- 先問自己要做甚麼事情，例如先有想複製檔案，才聯想到cp指令>在思考學習的經歷
- 例如圖中範例，我剛剛放進資料夾兩個檔案hostname、hosts。創了一個settings資料夾。這時候將這兩個檔案擺入的settings的一個過程
- ![image](https://github.com/Tomalison/Linux/assets/96727036/9907f30b-08cc-485f-a91c-fbd479c6d4b6)
- cd settings進到該目錄 看一下檔案 或是可以直接 ls -l settings/

## Linux的檔案系統

#### XFS檔案系統
- CentOS7、8的檔案系統 / EXT3加上了日誌功能，節省傳統需掃描的問題，EXT4更好，最大可達1EB。而XFS檔案系統最大可達8EB
- ![image](https://github.com/Tomalison/Linux/assets/96727036/16e720fb-d4be-44b8-b24e-202aa7c9a89e)
- xfs指令可以看到相關資訊

#### 認識inode
- 檔案資訊紀錄檔inode，紀載這個檔案的所有資訊 / 包括檔名、更動時間、權限與檔案儲存的區塊位置等資料 / 每個inode都有唯一的編號
- ls -i
- df -h
- inode使用有限 df -i 可以看到使用量狀況 ，儲存量還夠，但不能存東西，通常都是inode用光了，他不是無限制可以使用

#### 檔案系統相關指令與操作說明
- 這裡比較需要管理者權限，先變成超級使用者，
- 如果要看檔案掛載狀況 可以輸入cat /etc/fstab
- ![image](https://github.com/Tomalison/Linux/assets/96727036/11beb3f6-2390-47a8-9c3c-9c7723cd2e39)
- 檢查磁碟空間 可以用df這個指令，看檔案使用狀況
- df -h(human readable) 可讀性可以更高
- man (操作手冊manual) 例如用man df就可以看到df的完整內容有甚麼
- info 用info df可以更白話一點 q
- 佔了多少空間 可以用du /var 可以看/var這個資料夾裡面的資料夾用了多少 --> du -h /var 可以看到完整使用狀況
- ls -l /
- du -d 1 -h /

#### 認識連結(LINK)-符號連結與硬連結
- 允許一個檔案參考到另一個檔案
- 連結是一種指向另一個檔案的特別檔案 ln -s (目標是哪一個對象) /var myvar
- ls -l
- ![image](https://github.com/Tomalison/Linux/assets/96727036/ca75b871-07cd-4de0-b541-0196d6026663)
- 這個好處是不用複製整個目標資料到這，也可擁有這根目錄var的所有資料(類似捷徑)
- cp /etc/fstab . 然後我們在連結到fstab這 ln -s fstab slink >> cat slink 就等同於 cat fstab
- 如果我們刪除fstab (rm fstab) slink就會如下圖
- ![image](https://github.com/Tomalison/Linux/assets/96727036/6dda7b22-8c51-48fa-a439-bedf6d9bf16c)
- 那這樣我們就也可以刪除這個連結 rm slink  / rm myvar
- 硬連結 hotlink   原本的>> cp /etc/fstab . > ll > ln -s fstab slink > ll > ls -i
- hotlink > ln fstab hlink >> ll可以看到不一樣 >> ls -i 可以看到hlink 等於 fstab一模一樣的inode值 > 所以rm fstab > hlink還是存在 > 可以用cat hlink看 > 他也可以自己做自己權限處理
- 但硬連結無法跨越分割區
- ![image](https://github.com/Tomalison/Linux/assets/96727036/af82abb4-abc5-4442-9dfb-817409db93b2)
- 也不能用在目錄
- ![image](https://github.com/Tomalison/Linux/assets/96727036/bd475fc4-af59-41cf-9559-04e8b1678808)

#### 執行檔案與PATH環境變數
- ls /usr/bin/ 之所以可以執行，是因為在PATH環境變數可以被搜索有沒有執行檔可以被執行
- echo $PATH
- echo "echo Hello" > runme  這段指令就是把echo Hello 放到runme。但這個可以rw，但不能執行(x)
- 如果要執行要用到change mode指令 >> chmod u+x runme
- ![image](https://github.com/Tomalison/Linux/assets/96727036/4fac1b16-0199-4ab2-a48a-5694e4d6662b)
- 所以要執行當前目錄之下的檔案 要輸入 ./runme 這樣就可以執行了


## 檔案編輯與工具
#### 熟悉VIM文字編輯器
- 下載網路文字檔案並編輯
- 所有UNIX跟LINUX都內建的文字編輯器，在任何LINUX都可以用它編輯文字檔案 輸入vi
- wget 抓取網址 ，如果沒安裝可以用dnf install wget -y
- wget https://www.rfc-editor.org/rfc/rfc854.txt 抓這個測試文檔
- vim rfc854.txt 就可以
- ![image](https://github.com/Tomalison/Linux/assets/96727036/8df1f45c-5785-46db-b1a8-0f1c071441b0)
- 一進來是一般模式，可以用滑鼠跟pageup/down去移動 用:可以進入命令模式，在這裡q就可以離開 不存檔離開q!  w是儲存 wq儲存離開
- dd 1下是快速刪除一行 gg可以回到檔案最前頭 shift+G可以到檔尾 w可以跳一個空白到下一個字符過去 yy是複製 p是貼上 u回復上一動
- i o a 可以進到編輯模式 i是插入  o是進到編輯模式在新增一行 a會進入到編輯模式然後到下一個字元
- esc就是回復到一般模式
- 200 + G 就是快速到200行
- 沒存檔就直接XX 就是沒經過完整存檔就關掉，再進去該檔案，會出現警告 說有找到一個暫存檔，R繼續編輯 存檔後 可以用rm刪除剛剛的暫存檔
- ![image](https://github.com/Tomalison/Linux/assets/96727036/603afb88-9f83-4843-9ba1-522739b6dea9)

#### 標準輸出入與重導
- 標準輸入 :鍵盤 標準輸出 :螢幕 標準的錯誤訊息輸出 :螢幕
- df > 可以導到一個檔案之中 例如df > myfile 這就是說把df原本要輸出到螢幕上的內容 導到myfile這個檔案中，請注意myfile不能存在不然會覆蓋 /<是重導
- ls >> myfile 就可以把內容導到myfile後面的
- 要將錯誤訊息導到另一個地方 可以用2> 例如 ls /abcde 2> myfile
- 如果要把錯誤跟標準正確的資訊都導到一個地方 可以用 ls /abcde > myfile 2>&1 就可以都導到myfile上
- 重導輸入 wc ，輸入資料後Ctrl+D 就可以算出 行數 /幾個字 /幾個字元
- wc < /var/log/messages 就可以重導輸入 
- pipeline : more 例如 ls /usr/bin | more 就是把左邊的指令送給 more 就是管線的應用
  
#### 篩選與管線處理
- 在檔案中要找特定的內容時 grep 特定文字 檔案(對象)
- grep login /var/log/messages 就會出現如下圖在該檔案中找到跟login有關的字元資訊
- ![image](https://github.com/Tomalison/Linux/assets/96727036/75bc0024-8efe-49fd-8be3-9520402b2e9d)
- 要找全部檔案 可以如範例* grep login /var/log/*
- 如果你在檔案中 只對某些字有興趣，可以像這樣 ls /usr/bin | grep mk 把左邊的資訊 透過管線 導入 右邊指令再找
- ![image](https://github.com/Tomalison/Linux/assets/96727036/3d8b5f1b-f0ca-45ba-8ac3-dd9cbc5fe8ee)
- rpm -qa 可以找到我們系統有安裝甚麼套件通常找很多套件 我只想找某個檔案 rpm -qa | grep httpd

#### 搜尋檔案
- 例如pwd是放在PATH環境變數 echo $PATH
- 可以用 which pwd ，但which適合查一些已經存在的命令或是執行檔案
- locate pwd 他是一種查詢 不是搜尋 updatedb(通常半夜排程這個指令) 再用locate才可以查的到
- 希望可以搜尋整個系統資料，要用find。 盡量不要用/目錄 要用 find /home -name tomsu25478
- find /var/ -perm 755  (755=rwxr-xr-x的權限) 還可以查某一個有變更時間的資料 find /root -ctime -2 (2天內有更新的資料)
- find /usr/ -size +5M (可以找出這個資料夾有5M以上的檔案)

#### 檢視檔案內容
- cat可以用來產生文字檔 cat > test.txt  Enter 開始輸入內容 然後Ctrl+D 存test.txt
- cat -n > data.txt 可以存成有行號的資料
- more在做分頁顯示  例如 more anaconda-ks.cfg 要繼續用空白看完其他資訊
- less anaconda-ks.cfg  可以輸入:數字 往下幾行
- head anaconda-ks.cfg 呈現檔案前面的10行資料
- tail anaconda-ks.cfg 呈現檔案後面的10行資料， 這常常使用，最新的LOG資料時常都是補在檔案的最尾巴 / 他也可以持續的追蹤
- tail -f data.txt 追蹤剛剛的data檔
- 例如在開啟一個命令列，然後用cat >> data.txt 後 新增某些資訊，就可以看到剛剛的命令-f 可以看到他做的事情
- Ctrl+C就可以停止追蹤他
- more時常配合管線做分頁資料查找 例如 ls -l /usr/bin | more 就可以一頁頁查找資料

## 硬體設備管理
#### 硬體設備管理
- 要談到硬體設備，要談到 ls /dev(硬碟) 這個資料夾  這是設備檔案  例如 /dev/sda = SCSI硬碟 SATA硬碟
- ![image](https://github.com/Tomalison/Linux/assets/96727036/2fab56ac-e716-4320-903d-bb9e0af2ce29)
- ls -l /dev | more 可以看到這些分類字母，-號是一般的檔案 l是連結 d是資料夾 b是區塊型檔案(光碟機/硬碟) c代表是文字型(終端機/磁帶機/印表機等等)
- ![image](https://github.com/Tomalison/Linux/assets/96727036/cf3b2491-962e-4762-acf2-4d8c64a06e7a)
- ![image](https://github.com/Tomalison/Linux/assets/96727036/bcb7fc12-3d7c-4adc-9e09-7b84c8b8738a) 這是Major number 旁邊是次要的辨識碼 這辨識碼很重要，之後要使用這些設備都必須先用mount掛載設備
- mount需要的指令就是設備的名稱
- ![image](https://github.com/Tomalison/Linux/assets/96727036/bef91c46-65f0-47f0-850c-00bf74762371) tty
- 連接到UNIX伺服器 稱為是終端機
- 所以Linux準備了許多終端機連線這些設備

#### 掛載光碟片
- mount掛載設備 umount卸載設備 (超級使用者)
- ls / 後可以看到一個media 是我們常用來掛載資料的資料夾
- 譬如說mkdir /media/iso
- man mount可以看一下使用手冊
- ![image](https://github.com/Tomalison/Linux/assets/96727036/f14c3ef0-7e8e-4ee2-b4f2-384e1ac4a1a2)
- lsblk(列出區塊設備) 可以看到我們剛剛掛載的光碟片 blkid(看更詳細的資料)
- iso9660 = 光碟片檔案系統
- blkid -p /dev/sr0(剛掛載在虛擬機的ISO檔)
- mount /dev/sr0 /media/iso 就可以掛載到我們剛剛建好的資料夾
- 如果ls /media/iso 就可以看到這個光碟上面的資訊
- 要退出 要 umount /media/iso 就可以退出這個光碟

#### 加入新硬碟、MBR與新一代GPT
- shutdown -h now(先關機)
- 關機後 VB進入設定>存放裝置>選控制器SATA>加入硬碟>建立>測試1G>取名newdisk1>這顆磁碟機就已經附加到我們虛擬機上面
- ![image](https://github.com/Tomalison/Linux/assets/96727036/50a2786e-f07c-48b8-b6df-d48b5c833449)
- 舊的磁碟分割 MBR(Master Boot Record) :512byte磁區 /一個硬碟最多能有4個主分割區 /無法處理超過2TB以上的硬碟 /使用fdisk指令管理
- 新的磁碟機分割是使用GPT (Guid Partition Table) 4096byte磁區 /支援超過2TB磁碟 /使用parted、gdisk指令管理
- fdisk -l /dev/sdb 就可以看到剛剛我們建立的磁碟區
- ![image](https://github.com/Tomalison/Linux/assets/96727036/2cf07861-ac16-4b0b-9895-ebaea8f3a048)
- fdisk /dev/sdb  一般用D刪除分割區 按N建立分割區 按P看硬碟有沒其他分割區
- ![image](https://github.com/Tomalison/Linux/assets/96727036/ab547bda-e9c1-43bf-97db-74a0b6aa86ed)
- 我們按n建立分割區>按p當作主分割區>編號有4個要放在哪一個 > +800M
- ![image](https://github.com/Tomalison/Linux/assets/96727036/61536363-d6c8-425d-89d3-ad04945aab91)
- 按下w 寫入 這樣就建立完成了
- 用blkid檢查剛剛建立的磁碟有沒有在裡面
- 有了之後要格式化>掛載
- mkfs.xfs -f /dev/sdb1 (格式化)
- mkdir /disk1 建一個未來要掛載的資料夾
- mount /dev/sdb1 /disk1 掛載
- ls -l / 檢查 blkid
- 這時候我就可以 cd /disk1 去做操作 例如 touch data 放置一個資料

#### 建立GPT磁碟分割區、使用Parted
- shutdown -h now(先關機)
- 操作方式一樣，名稱取做newdisk2 / 可以預測它的名稱會排在/dev/sdc
- fdisk -l /dev/sdc 檢查一下有沒有出現
- parted /dev/sdc 建立GPT 
- ![image](https://github.com/Tomalison/Linux/assets/96727036/627776b3-9fbd-4bb2-940a-039c77cd2b57)
- mktable gpt 建立GPT格式的分割區
- print 指令
- mkpart primary xfs 1MB 800MB (起始在1MB 結束在800MB，建立完不需要儲存 直接quit就可)
- blkid 
- mkfs.xfs -f /dev/sdc1 (再三確認在下這個指令)
- mkdir /disk2
- mount /dev/sdc1 /disk2
- 可以測試 touch /dsik2/data 丟一個資料 cp /etc/fstab /disk2 複製到disk2 最後檢查 ls -l /disk2來看資料

#### Linux開機自動掛載/etc/fstab
- cat /etc/fstab
- cp /etc/fstab /etc/fstab.backup(先做一個備份 比較保險)
- blkid 先找到sdc1整段資訊複製
- blkid /dev/sdc1 >> /etc/fstab(一定要兩個>> 不然一個>會蓋過去) 
- vim /etc/fstab 游標放到該行 用i 將sdc1 UUID 雙引號""後面的資訊全刪除  告訴他我未來要掛載的 /disk2 xfs  defaults 0 0 (預設值 /不用備份 / 不須重新開機 然後UUID前面也都刪除
- ![image](https://github.com/Tomalison/Linux/assets/96727036/44ededb7-e6f8-4b64-b1ad-749fb933ff38)
- 下完之後 要wq 儲存
- ![image](https://github.com/Tomalison/Linux/assets/96727036/fb7d5b5f-8d80-4236-9b92-a8e27a61f1c7)
- mount -a    用cat /proc/mounts看一下有成功掛載
- ![image](https://github.com/Tomalison/Linux/assets/96727036/9049b037-d8fa-46e1-b140-f89fba740371)
- 確認完重新開機 shutdown -h now
- blkid   ls /disk2   df -h

## Linux的帳號、群組與權限
#### Linux的使用者帳號與群組
- ![image](https://github.com/Tomalison/Linux/assets/96727036/c3821fdf-2c38-4d74-969c-e701e1b3028e)
- Linux一定是多人作業，你一定要建立帳號的所屬群組
- Linux的群組是建立在etc裡的group  cat /etc/group
- 第一個是群組名稱:有沒有使用:編號值:存在帳號
- ![image](https://github.com/Tomalison/Linux/assets/96727036/4bc3c0a9-922c-4b41-8c38-dc9e2759019c)
- 建立群組 groupadd >> 要建rd  就輸入groupadd rd
- 建立帳號 useradd  >> 要建andy 就輸入useradd andy 但這樣就會直接在建一個叫做andy的群組
- cat /etc/passwd 帳料資料檔 冒號之間依序為 帳號:x(代表密碼):使用者ID:群組ID:註解:使用者的家目錄:這使用者使用的Shell程式是哪一隻
- ![image](https://github.com/Tomalison/Linux/assets/96727036/b5b4fd4d-a746-4c2f-a325-c7c7defaa3f4)
- cat /etc/shadow 帳號的密碼放在這 可以看到hank的密碼是有經過處理的，mike的是!!代表還沒密碼 無法登入
- ![image](https://github.com/Tomalison/Linux/assets/96727036/40ef8026-5be7-4688-8c81-e9fd12de2a9b)
- ls -al /home/mike
- ![image](https://github.com/Tomalison/Linux/assets/96727036/80acee42-b680-4edd-8d7c-d5610fdbf668)

#### 新增群組與帳號、刪除帳號
- id tomsu25478 可以觀察帳號資訊 使用者uid 群組gid groups代表有加哪些群組
- useradd -g rd tomsu25478 就可以把這個帳號加到rd這個主要群組
- 將該帳號加入額外群組 usermod -G sales tomsu25478 就可以將這帳號再額外加入 sales這個群組
- 但如果要額外加兩個群組 usermod -G sales,manager tomsu25478 才可以一次加兩個額外群組 不然會蓋過去
- 如何刪除帳號 userdel mike 這樣只會刪除etc裡面的帳號跟群組紀錄 不會刪除他的家目錄 要記得home的資料夾要自己去刪
- 所以要一次刪除 userdel -r mike就會將家目錄一起刪除
- ![image](https://github.com/Tomalison/Linux/assets/96727036/0fd01454-2c4a-4da3-8d78-ba4e7c4acbcd)
- 建立群組與帳號並設定練習

#### 刪除群組、讓使用者無法登入
- groupdel rd 刪除rd群組
- 但是如果群組裡面還有其他使用者帳號，他無法直接刪除
- 之前設定的useradd的帳號沒有密碼登入不了。所以要用 passwd tomsu25478 就會叫你設定密碼
- 如果要禁止某使用者帳號無法登入 手動改 :vi /etc/passwd 進入後 到該帳號的 /bin/bash處 改成 /sbin/nologin
- 還有一種是比較常用的指令改他無法登入 : (change shell) chsh tomsu25478 就會叫出新命令殼 改成/sbin/nologin
- ![image](https://github.com/Tomalison/Linux/assets/96727036/55dd57f3-1a1c-4e67-a419-1ee0e74993c2)

#### 檔案權限管理與變更
- ls -l 可以看到每個檔案最左邊有10個字元表達他的權限狀態
- ![image](https://github.com/Tomalison/Linux/assets/96727036/e86d6b21-97ed-451e-84dd-d7193ebdbde9)
- r=可讀(read) / w=可變動與刪除(write) / x=可執行(execute)
- 下圖解析權限值計算方式 
- ![image](https://github.com/Tomalison/Linux/assets/96727036/6ba5a81c-d236-490a-94ca-a24de674d6d3)
- ![image](https://github.com/Tomalison/Linux/assets/96727036/a470afa3-7994-43b6-9d5a-6f07b9e7be7d)
- 要改變權限可以使用change mode指令 chmod 例如 chmod 755 data.txt 那他就可以改變data.txt成我們指定權限值的權限內容 像755就是 rwxr-xr-x
- ![image](https://github.com/Tomalison/Linux/assets/96727036/1d2d35ba-7970-466a-bb45-891a0c423e99)
- 上圖chmod 可以用權限者 例如"u"ser  "g"roup "o"ther的角度 新增刪除權限 例如 chmod o-rx data.txt 這時候就會剝奪other的權限值就會減掉rx / 或是 我們chmod o=r data.txt 就是讓這個other只有r的權限
- 如果要一次改兩個擁有者 我們可以 chmod go=r data.txt 就會一次把group跟other一起改成r權限
- 如果要加權限 chmod g+x data.txt 就可以將group加上x的權限
- 如果全部類型傭有者都要一起改 chmod a=r data.txt 就可以將所有傭有者都變成r的權限
- ![image](https://github.com/Tomalison/Linux/assets/96727036/9196960e-f4ff-4649-85a6-6476210c7852)

#### 目錄資料夾的權限
- 目錄的 r=列出目錄內容 w=可在目錄中編輯與刪除檔案 x=可進入該目錄
- 如下圖我在root進入opt資料夾後，新增project，再用另外一個帳號近來會看不到opt內的project但我可以新增myfile 這時候我再用root近來用ls -l看一下就會看到myfile跟project兩個
- ![image](https://github.com/Tomalison/Linux/assets/96727036/d179da0e-17df-4eb8-908a-a617375f0f26)
- 這時候我再用chmod o-rx project/將其他人這個資料夾的rx權限拿掉 這時候其他人就進不了也看不了這個資料夾
- chgrp 可以將這個資料夾或是檔案的群組權限轉給另一個群組 chgrp wheel project/ 就是將 project這個權限轉給wheel這個群組
- ![image](https://github.com/Tomalison/Linux/assets/96727036/5a52a1de-dcc4-4e33-9b34-0d80334086f4)

## 系統行程操作與管理
#### 行程管理與ps指令
- ![image](https://github.com/Tomalison/Linux/assets/96727036/860d5ad3-a0e3-450e-949b-a8f956d7ee59)
- CPU配置了許多一段段的時間給要執行的行程，是一項行程都有所謂的PID(process id 行程ID)
- 每次我們執行了一個指令 就會產生一個行程 去執行完
- ps(process status) 可以看到所有執行的行程資訊 ps -f詳細資訊 可以看到PPID 是PID衍伸出來的副行程(如下圖 -bash是su -衍伸出來的行程
- ![image](https://github.com/Tomalison/Linux/assets/96727036/19ad5225-b389-486a-81c1-92d49fed9219)
- ps aux (所有伺服器背後的所有行程 ps aux | more用通道做分頁
- ps aux | grep cron 篩選cron去觀察有關他的行程資訊
- top  持續監控  (Priority優先權
- ![image](https://github.com/Tomalison/Linux/assets/96727036/a9f62ac1-ffb9-4d30-9afd-9cab6f88f453)

#### 背景行程管理
- 前景行程 : 例如之前的updatedb要執行6秒  updatedb & 就會把這個行程放到背景去執行
- jobs可以看背景行程有哪些
- sleep 3 可以睡3秒  所以用 sleep 60 & 再用jobs就可以觀察背景這個行程
- ![image](https://github.com/Tomalison/Linux/assets/96727036/b162ace7-910b-48a7-b084-ea54c8bbf0c7)
- CTRL +Z可以暫停你的指令 >> bg可以把指令丟到背景
- 如果要取回背景行程 打下fg 後 CTRL+C取消行程
- 單取回某個正在執行的背景行程，打下fg 數字(該行程代號)
- ![image](https://github.com/Tomalison/Linux/assets/96727036/92055732-cbe6-4b47-a4c8-70a4c1c0492d)

#### 行程優先權、nice指令
- NICE值 行程優先權 -20~19 數字越低有越高優先處理權 / 一般預設是0
- ![image](https://github.com/Tomalison/Linux/assets/96727036/0950eefb-4baa-470a-b689-5ce2439e68ff)
- nice -n -10 sleep 60 & 用 ps l可以觀察 sleep這個行程的NI是-10
- ![image](https://github.com/Tomalison/Linux/assets/96727036/4ac2210c-9194-41fe-a7a0-ad8e92f6dc7c)
- kill指令 : 送出15term訊號到行程中，利如下圖範例 kill 25708 就會送出一個值 15號 結束行程
- ![image](https://github.com/Tomalison/Linux/assets/96727036/07a5cdbe-2b64-445a-ac53-571eaa359e33)
- kill -9 25722 用9這個是強制殺除
- killall sleep(可以殺除跟sleep相關的所有指令可以全部殺除)

#### 系統行程資訊 /proc虛擬檔案
- /proc 系統行程虛擬檔案
- tree /proc 可以看到裡面的樹狀結構  ls -l /proc | more  來觀察行程資料的資料夾 都是虛擬檔案 例如可以看到cpuinfo
- 這時候將 cat /proc/cpuinfo 就可以看到CPU的相關資訊 有非常多資訊都是以虛擬檔案的方式來告訴你
- ![image](https://github.com/Tomalison/Linux/assets/96727036/c3bda813-7caa-4db4-9c23-e03709ac0d31)
- cat /proc/partitions 可以列出來現在分割區的狀態
- cat /proc/sys/kernel/hostname 可以看到主機資訊 阿如果你要改名稱也可 echo "centos8" > /proc/sys/kernel/hostname 就改了centos8
- 行程管理在系統面管理的觀念很重要

## Linux防火牆
#### 防火牆機制FirewallD介紹
- ![image](https://github.com/Tomalison/Linux/assets/96727036/41fc5369-14df-4a84-9295-f3ab74f58318)
- 防火牆在Linux是他的一個服務 限制哪些流量可以進來或出去
- FirewallD 這個D就是Daemon常駐背景的程式 ， 
- ![image](https://github.com/Tomalison/Linux/assets/96727036/081e289f-5742-4f05-ade6-816f22998f8b)
- ![image](https://github.com/Tomalison/Linux/assets/96727036/1125c403-ad6a-4ab3-a5ab-532bd3d4e026)
- FirewallD 提供了一個Zone 我們這個主機在哪個地點  提供了 介面=網路卡的設備 提供了Service幫我們設定了埠號、網路協定、封包等等 提供了port去做限制
- firewall -cmd
- firewall -cmd --get-zones 可以看到我們主機有哪些zone 如果要知道現在主機定位在哪個zone > 可以用 firewall -cmd --get-default-zone 查看

#### 允許特定服務通過防火牆
- firewall-cmd --get-active-zone 這是目前我們正在使用的區域ZONE值 他會顯示目前的虛擬網路設備 ，目前是public用的乙太網路卡
- ![image](https://github.com/Tomalison/Linux/assets/96727036/a0bc7c9e-3c1d-46f3-8480-1a32e4dd19f3)
- firewall-cmd --list-all 可以看到詳細的資訊
- ![image](https://github.com/Tomalison/Linux/assets/96727036/170522f5-b22e-4456-afe2-419d0e59c692)
- 如上圖 SSH代表可以從外部連線到Linux的22埠號
- ls /usr/lib/firewalld/services/ 這裡已經放好的預先儲存好的服務的定義 xml值
- cat /usr/lib/firewalld/services/ssh.xml 就可以看到這個檔案定義的資訊
- ![image](https://github.com/Tomalison/Linux/assets/96727036/472c7ec7-6f22-4b4a-9280-22260df8c652)
- cat /usr/lib/firewalld/services/cockpit.xml 可以看到9090port是開啟的
- ![image](https://github.com/Tomalison/Linux/assets/96727036/3bceaeea-cd21-434f-9161-2aefc57d3f34)
- 假設我這台機器想要開啟80port 就是網頁伺服器的服務
- cat /usr/lib/firewalld/services/http.xml 可以看到80port是開放的
- ![image](https://github.com/Tomalison/Linux/assets/96727036/0c4f3067-21df-410e-bdb8-2cefc20a5b4b)
- 如果我想打開防火牆有關80port的設定
- firewall-cmd --add-service=http  他有兩種設定 一個是runtime正在執行中的儲存值(系統關機後會消失) 一個是permanent持久設定值 firewall-cmd --add-service=http --permanent --zone=public 這個時候才會寫入到設定裡
- firewall-cmd --reload 去讀取已儲存的設定值套用到目前核心的執行環境 這才是完整設定好。 未來網路來的80port才會被通過
- ![image](https://github.com/Tomalison/Linux/assets/96727036/fa0e2341-cc06-46ed-a543-11dc9709c379)
- 如果我只是想讓本機的某個埠號通過，我可以用firewall-cmd --add-port=9958/tcp --permanent >> firewall-cmd --reload
- 再觀察一下 就會看到9958port
- ![image](https://github.com/Tomalison/Linux/assets/96727036/c6afd4cb-0eea-4b8e-ad5a-daca5b7576b3)

#### 新一代管理介面cockpit
- redhat8有一個新的管理介面 叫做cockpit
- systemctl enable --now cockpit.socket 可以啟動這個服務
- 如果再firewall-cmd --list-all 沒有看到這個cockpit的服務 也可以用firewall-cmd --add-port=9090/tcp --permanent >>firewall-cmd --reload 開啟這個服務
- 這個指令就是取代 netstat -tanlp這個網管指令 ss -tanlp 可以傾聽服務是否有被啟動 可以看下圖9090有通了
- ![image](https://github.com/Tomalison/Linux/assets/96727036/0be251f8-8d10-4a9e-a0df-5b4ef5ef9009)
- ![image](https://github.com/Tomalison/Linux/assets/96727036/7c6c97ff-d099-4f81-bd37-29c14c3aee33)
- 這工具也取代了以前我們都要裝webmin這樣的網頁管理Linux套件軟體


## 軟體套件管理RPM、YUM、DNF
#### 軟體套件RPM:查詢query
- rpm : Red hat Package Management 是將預先編譯好的軟體給包裝起來 直接在該系統安裝 省去在上面編譯的工作，所以這個RPM被各個Linux使用
- ![image](https://github.com/Tomalison/Linux/assets/96727036/324e388f-5f54-4979-9d0e-13196273146a)
- rpm 可以看到許多用法
- 例如man rpm看它的使用手冊 最常用的是query(查詢) rpm -q / rpm -i / rpm -e
- rpm -qa 查詢全部套件 也可以透過管線方式 rpm -qa | grep gzip來查gzip軟體套件資訊 包含名稱/大版號/修正次數.版本/平台
- rpm -qi gzip 可以查他的相關資訊
- rpm -ql gzip 可以查這個檔案的清單，看他在我們系統裝了哪些資訊
- rpm -qf ^C
- rpm -qf /etc/fstab
- ![image](https://github.com/Tomalison/Linux/assets/96727036/d9231fd2-a708-4228-9849-ba62f7e70954)

#### 安裝RPM軟體套件:install
- rpm的安裝 先開啟虛擬機器的光碟片按右鍵 掛載CentOS
- mount /dev/sr0 /media/iso
- 這時候我們要找rpm放在哪 他是放在 ls /media/iso/AppStream/Packages/
- rpm -ivh /media/iso/AppStream/Packages/mc i=安裝 v=資訊 h=進度條
- 這樣就可以安裝mc這個軟體，如果有依賴型的安裝還要先把其他安裝完才能安裝
- ![image](https://github.com/Tomalison/Linux/assets/96727036/cae1597e-5527-4139-9ee0-d5efd2bf05a6)
- 像這樣裝好後，就可以執行mc這個指令
- ![image](https://github.com/Tomalison/Linux/assets/96727036/25f3eff3-a72f-45cb-a382-187a41628544)
- 按下F10 就可以離開剛剛的軟體
- rpm -e mc (erase)就可以刪除套件軟體
- 如果我們裝一個比較大的軟體 rpm -ivh /media/iso/AppStream/Packages/ant 他是JAVA的開發建置工具，這時候她出現了錯誤說要先裝ant-lib + java-devel + javapackages-tool才可以裝ant-1
- 這時候我們就要裝這些依賴的套件，但這樣就會牽扯到許多的指令
- ![image](https://github.com/Tomalison/Linux/assets/96727036/8f4b7109-28f5-49db-9ed4-f137cdf1ae5b)
- 所以red hat又發表了yum dnf來解決上述的問題

#### YUM與DNF套件管理
- yum (Yellow dog Updater, Modifield) 將軟體套件的檔案集中在網路伺服器
- 伺服器會算出你有多少相依檔案要安裝，一起打包下載回來依照順序安裝
- ![image](https://github.com/Tomalison/Linux/assets/96727036/12d2d9bb-540a-4380-9a44-e983f2accc9f)
- 他的CentOS 是放在 ls /etc/yum
- cat /etc/yum.conf ； ls /etc/yum.repos.d/ 看到這些檔案設定黨
- cat /etc/yum.repos.d/CentOS-AppStream.repo (REPO 檔案庫) 可以看到一些鏡像檔 我們可以找出離我們最近最快的方式
- ![image](https://github.com/Tomalison/Linux/assets/96727036/eda1051e-923c-401b-a1f3-3b5402893cb5)
- 承前一單元範例 yum install ant 他就會去伺服器檢查 ant到底要裝那些軟體 要得話Y
- 如果要直接安裝 也可以 yum install ant -y
- dnf (Dandified Yum)
- dnf install -y (跟yum用法一樣)

#### 軟體檔案庫repo管理、EPEL擴充軟體庫、remi安裝PHP7.4
- dnf repolist 可以列出來現在有幾個伺服器資訊
- dnf search php 可以搜尋有沒有可以被我們安裝的軟體 例如範例就是去找出PHP有關的軟體
- EPEL (Extra Package Enterprise Linux) 是由FEDORA社群維護的額外型檔案庫。
- dnf install -y epel-release 可以安裝這個軟體包
- ls /etc/yum.repos.d/ 可以看一下跟epel有關的設定檔
- dnf repolist
- dnf search htop
- dnf -y install htop
- htop這個軟體就是由EPEL軟體庫安裝而來
- 那像PHP7就沒放在官方軟體庫也沒放在EPEL 而是放在REMI檔案庫
- dnf install https://rpms.remirepo.net/enterprise/remi-release-8.rpm
- 直接找到你要安裝的網址 來安裝
- dnf -y install php74 ； dnf -y install httpd

## 系統服務與網頁伺服器
#### 系統服務systemd
- Linux最大的優點是她的網路服務 例如網頁伺服器 apache ngnix 或是域名轉換的伺服器
- 也就是說我們需要安裝這些軟體，由一個systemd (System Daemon) 他是開機後執行的第一個程式，他在管理Linux的常駐程式
- systemd Linux新一代服務啟動程序
- systemctl 可以管理各類的服務
- 談談systemd裡面的一些設定檔
- ls /usr/lib/systemd 
- ![image](https://github.com/Tomalison/Linux/assets/96727036/728816f6-d4b6-4906-8437-14448e32d5e5)
- 裡面有個資料夾叫system 服務設定檔資料夾 就可以看到裡面一堆設定檔
- UNIT 每一個服務都是一個單元
- TARGET代表的是一個階段標的，可訂定在某個階段時需要啟動甚麼UNIT服務
- cat /usr/lib/systemd/system/graphical.target
- ![image](https://github.com/Tomalison/Linux/assets/96727036/eb4a29fe-316b-42f6-ad80-0a585316f3bd)
- systemctl isolate multi-user.target 可以用這指令去做切換 你未來要到文字介面做
- systemctl isolate graphical.target 這就是在設定開機要在甚麼模式下
- cat /usr/lib/systemd/system/httpd.service 當我們安裝APACH的伺服器 這裡面就會有一個這樣的設定檔
- systemctl status httpd 可以看到我們目前沒有啟用他，如何啟用他呢
- ![image](https://github.com/Tomalison/Linux/assets/96727036/827257e0-5890-4733-8431-fa775f1b6209)
- systemctl start httpd.service 就可以啟動 systemctl stop httpd.service 可以停止這個服務
- systemctl restart httpd.service 重啟這個伺服器
- 如果要自動開機開啟阿帕契 systemctl enable httpd  / 如果未來開機不要再打開則用 systemctl disable httpd
  
#### 管理服務systemctl指令,Apache網頁伺服器
- systemctl status httpd
- firewall-cmd --list-all 可以看一下PUBLIC這個ZONE有沒有允許 HTTPD SSH通過
- cat /usr/lib/firewalld/
- firewall-cmd --add-service=https --permanent
- firewall-cmd --reload
- firewall-cmd --list-all 這時就可以看到https被加入了
- ![image](https://github.com/Tomalison/Linux/assets/96727036/c7e8a0c1-e192-4706-b8e8-53f7ee669445)
- ps aux | grep httpd 可以看到許多行程跟httpd有關 可快速回應網路需求
- vim /etc/httpd/conf/httpd.conf
- ![image](https://github.com/Tomalison/Linux/assets/96727036/5621363d-8473-440c-997f-ce1f5e5209cb)
- ![image](https://github.com/Tomalison/Linux/assets/96727036/e3b179bb-a010-4cd7-b9f5-f4789cf2c4ac)

#### 架設範例網頁
- 用APACHE建立一個對外的範例網頁 free web template
- 下載ZIP檔(複製他的網址)
- wget 剛剛複製的網址
- unzip 剛剛的ZIP檔名稱
- cd 剛剛解壓縮後的資料夾/
- ls 看一下裡面的檔案
- ls /var/www/html 可以放在這裡
- cp -R . /var/www/html 複製該資料夾 (cp -R:Recursive連資料夾內的檔案一併複製) .目前所在資料夾的所有資料
- cd /var/www/html
- ![image](https://github.com/Tomalison/Linux/assets/96727036/7fddc014-64c8-4719-ab91-864c9200e1e7)
- 可以看到擁有者都是root
- 在先前的APACH我們知道使用者與群組都是APACH
- 換擁有者的指令是 chown -R apache:apache * (使用者:群組) 就會把所有檔案使用者變成APACH
- ![image](https://github.com/Tomalison/Linux/assets/96727036/f8c4b323-1c6e-4637-a8e2-45c9d656f302)
- 可以測試你LINUX的ID EX 192.168.0.188

#### 模組與設定檔
- cd /etc/httpd/ > ls -al
- ![image](https://github.com/Tomalison/Linux/assets/96727036/bea36106-03f8-422c-8fef-14466b9053d1)
- modules 可以看一下APACH裡面的模組 Module模組 各個功能依照模組的方式開發後，啟動APACHE時可選擇要載入某些附加功能的模組
- 可以選擇性的導入這些模組
- ls conf.modules.d/
- vi /var/www/html/test.php 來確認一些PHP模組狀況
- systemctl restart httpd

## 系統管理實務
#### Mysql(mariaDB)資料庫安裝與設定
- dnf install mariadb-server
- systemctl start mariadb 啟動資料庫
- 做初始化設定 mysql_secure_installation
- MYSQL有自己的管理者帳號，也叫root 因為第一次安裝先按ENTER 接下來會設定密碼
- 自行建立root密碼
- 是否允許遠端登入 要的話按N 是否要刪除測試資料庫 Y 是否要讀取權限的表格 Y
- 這樣就完成初始化設定
- mysql -u root -p 互動式方式給密碼 > 打密碼
- 就進入到mysql畫面 可以在這裡建立 資料庫 表格 權限
- 完成後就exit 就可以跳出MYSQL
- Linux上目前都用mariaDB去用 

#### Tar壓縮檔案與活用date日期指令
- ls /vsr/www/html 前二單元有放一個範例網頁
- tar (壓縮檔按指令 > 將所有檔案集合起來包成一包>在壓縮成壓縮檔) 選像c 產生新的包裹檔案 / 選項v觀看指令進度 選項f指定包裹檔案的名稱 選項z檔案壓縮
- tar cvfz web.tar.gz /var/www/html/*(壓縮指令 名稱 對象的所有內容)
- 完成之後目錄下就有這個壓縮檔
- mkdir web 建一個資料夾
- mv web.tar.gz web 移動這個壓縮檔到這個資料夾
- cd web 
- ls
- tar xvfz web.tar.gz (x=解壓縮)
- ![image](https://github.com/Tomalison/Linux/assets/96727036/5905f531-081a-4b7c-b9ed-13de437f8785)
- date
- echo $LANG
- date +%Y
- date +%Y%m%d
- tar cvfz web-`date +%Y%m%d`.tar.gz /var/www/html/* 可以得到這個壓縮檔的壓縮日期
- ![image](https://github.com/Tomalison/Linux/assets/96727036/0421098a-a54b-4d5b-8977-bc46c7069737)

#### SHell程式設計:批次建立帳號實務
- ![image](https://github.com/Tomalison/Linux/assets/96727036/560c5eb6-6a84-4fda-9f20-430091282813)
- vi test.sh (這就是一個SHELL的程式)
- 可以把重複執行的程式寫在do跟done之間 :wq存檔
- chmod +x test.sh
- ./test.sh 就可以執行剛剛寫好的程式

- 批次建帳號的功能
- seq 1 10 (seq=產生循序數字sequence) 如果想要1 3 5 7 9 (seq 1 2 10) seq -w 1 10
- groupadd cs
- useradd -g cs mike
- passwd mike 這樣建立很慢
- chpasswd 會依照你前面給他的資料來改
- echo "mike:abc123" | chpasswd
- 所以要快速建立useradd跟密碼
- dnf install -y pwgen
- pwgen 6 3 (我要6個字元 3個密碼)
- 就可以輸出亂數密碼來
- 依照上面的知識來寫一隻程式
- vi add.sh
- #!/bin/bash >>u8801~u8820
- for n in `seq -w l 20`(`＝他會把它輸出的資料換成她所輸入的資料)
- do
-  useradd -g cs u88$n
-  echo -n "u88$n:" >> user.list
-  echo `pwgen 6 1` >> user.list
- done
- :wq
- vi add.sh
- chmod +x add.sh
- ./add.sh
- ls -l 看一下有沒有user.list
- ![image](https://github.com/Tomalison/Linux/assets/96727036/5537b589-ff35-4f64-b69f-a322186eb7c6)
- cat add.sh
- cat user.list | chpasswq

#### 設計磁碟用量配額設定
- dh -h (quota磁碟配額)
- xfs (tab tab兩下)看一下磁碟資訊
- xfs_quota XFS 檔案系統磁碟配額工具
- 掛載參數 uquota,gquota,pquota
- umount /disk2 先去卸載她
- mount -o (再掛載時加入選項OPTIONS)
- mount -q uquota,gquota /dev/sdc1 /disk2
- blkid 可以看sdc1
- mount | grep sdc1
- 掛載完成後 可以用 xfs_quota -x /dev/sdc1 (x=EXPERT專家模式)
- help
- report -h
- inode用量配額
- block空間用量配額
- df -h
- 為使用者在DISK2只能用50M
- limit bsoft=50m bhard=60M tomsu25478 (bsoft=空間基本限額 bhard=空間絕對配額)
- report -h
- ![image](https://github.com/Tomalison/Linux/assets/96727036/5a049e54-202a-453c-994c-6486a7995923)
- 設定完成用quit就可以結束了
- mkdir /disk2/tomsu25478
- chown tomsu25478 /disk2/tomsu25478
- fallocate -l 50m file50m
- fallocate -l 5m file5m
- fallocate -l 10m file10m 這時候就可以看到磁碟已滿 因為配額是60M
- ![image](https://github.com/Tomalison/Linux/assets/96727036/b3723a6a-c61c-4bba-ad5f-4fab58a10c70)
- ![image](https://github.com/Tomalison/Linux/assets/96727036/5523253d-ed1a-41ab-9ac4-167c1b2e9828)
- Grace寬限期

## Docker容器管理
#### Docker容器技術與安裝

#### Image映像檔與Container容器，指令操作

#### 建立私人雲服務NextCloud的docker容器

## Google雲端CentOS8虛擬機器
#### Google雲端虛擬機器準備項目

#### 建立Google雲端CentOS8虛擬機器

#### 使用網頁SSH登入Linux並變身為管理者

#### 安裝Linux必要工具與PHP7.4置換模組

#### GCP雲端防火牆與Linux防火牆

#### 配置固定IP與動態域名(domain name)


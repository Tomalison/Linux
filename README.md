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

#### 檔案權限管理與變更

#### 目錄資料夾的權限

## 系統行程操作與管理
#### 行程管理與ps指令

#### 背景行程管理

#### 行程優先權、nice指令

#### 系統行程資訊 /proc虛擬檔案

## Linux防火牆
#### 防火牆機制FirewallD介紹

#### 允許特定服務通過防火牆

#### 新一代管理介面cockpit

## 軟體套件管理RPM、YUM、DNF
#### 軟體套件RPM:查詢query

#### 安裝RPM軟體套件:install

#### YUM與DNF套件管理

#### 軟體檔案庫repo管理、EPEL擴充軟體庫、remi安裝PHP7.4

## 系統服務與網頁伺服器
#### 系統服務systemd

#### 管理服務systemctl指令,Apache網頁伺服器

#### 架設範例網頁

#### 模組與設定檔

## 系統管理實務
#### Mysql(mariaDB)資料庫安裝與設定

#### Tar壓縮檔案與活用date日期指令

#### SHell程式設計:批次建立帳號實務

#### 設計磁碟用量配額設定

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


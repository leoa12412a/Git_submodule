# Git_submodule
# 使用 git submodule 管理 project 所需的其他模組

# 使用別人的submodule
基本上會用到git submodule的場合，就如標題所說的，我的 project 要用到其他 project 的程式碼，我希望讓我的使用者能直接拿到其他 project 的程式碼，這樣他們不用自己再去載，麻煩之外可能還會載到錯誤的版本。<br>

另一方面，我們又不想把對方的程式全部加到我的 repository 裡面，這樣會帶來不好的後果，上游的程式碼修改，要自己手動更新，沒辦法用 git 的方式更新，增加錯誤的機會。git 針對這個使用情景的解決方式就是 submodule。<br>

使用到git submodule有兩個種情況，是載入別人的project，發現裡面有用到 submodule，例如知名的補齊工具 YouCompleteMe ，裡面針對各種語言的剖析工具都是 submodule，這些專案載下來的時候， submodule 裡面都還是空的，要先用下列指令把 submodule 載下來。<br>

這裡我們先用YouCompleteMe當作例子來做示範<br>
首先我們先在透過github把YouCompleteMe的檔案下載下來<br>
這裡要注意的是你必須對著下載下來的資料夾做git bash，不然是看不到submodule的<br>
![image](https://github.com/leoa12412a/Git_submodule/blob/master/clone.png)<br><br>
再來我們先查看資料夾下面有哪些submodule，這裡只有打上git submodule就可以顯示資料夾下方所有submodule的路徑<br>
![image](https://github.com/leoa12412a/Git_submodule/blob/master/submodule.PNG)<br><br>
這時候我們去含有submoudle的其中一個目錄下可以發現，裡面是空的<br>
![image](https://github.com/leoa12412a/Git_submodule/blob/master/before.PNG)<br><br>
現在我們就必須初始化並更新submodule<br>
使用命令 : git submodule init(初始化) && git submodule update(更新)<br>
也可以使用git submodule update --init --recursive<br>
--recursive 會在 submodule 裡面還有 submodule 的時候，一口氣都設定好。<br>
又或者可以在 clone 專案的時候就指定要一齊複製 submodule<br>
![image](https://github.com/leoa12412a/Git_submodule/blob/master/submodule_init.PNG)<br><br>
更新完以後，再重回我們的資料夾內，可以看到資料都可以新增進來了<br>
![image](https://github.com/leoa12412a/Git_submodule/blob/master/after.PNG)<br><br>
<br>
# 創造一個自己的submodule
而另外一種情況由我們自已新增一個submodule給其他使用者使用<br>
首先我們先在github建立一個repositorbry方便最後做測試<br>
接下來就是要新增submodule<br>
語法：git submodule add <repository> [<path>](哪一個檔案庫/哪個路徑)<br>
範例：git submodule add https://github.com/facebook/facebook-php-sdk-v4.git facebook-php-sdk(facebook-php-sdk為資料夾名稱可以自行更改)<br>
![image](https://github.com/leoa12412a/Git_submodule/blob/master/add_submodule.PNG)<br><br>
新增submodule後git會將資料分別寫入.git/config和.gitmodules<br>
而在git status則會出現<br>
![image](https://github.com/leoa12412a/Git_submodule/blob/master/status.PNG)<br><br>
在 .gitmodules會出現<br>
![image](https://github.com/leoa12412a/Git_submodule/blob/master/file.PNG)<br><br>
而在submodule內座新的修改並commit後，在前面資料夾的git status會看到有新的commit
![image](https://github.com/leoa12412a/Git_submodule/blob/master/new.PNG)<br><br>
在最外層的git把剛剛的submodule做commit並push到我們一開始設定好的github repository<br>
![image](https://github.com/leoa12412a/Git_submodule/blob/master/remote.PNG)<br><br>
現在我們再把剛剛的資料複製下來，並打開facebook-php-sdk資料夾，發現跟一開始一樣是看不到submodule裡面資料<br>
![image](https://github.com/leoa12412a/Git_submodule/blob/master/sdk.PNG)<br><br>
這時候只要再使用git submodule init 和git submodule update就可以拿到fb最新的sdk了


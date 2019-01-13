# Git_submodule
# 使用 git submodule 管理 project 所需的其他模組

<textarea>
基本上會用到git submodule的場合，就如標題所說的，我的 project 要用到其他 project 的程式碼，我希望讓我的使用者能直接拿到其他 project 的程式碼，這樣他們不用自己再去載，麻煩之外可能還會載到錯誤的版本。

另一方面，我們又不想把對方的程式全部加到我的 repository 裡面，這樣會帶來不好的後果，上游的程式碼修改，要自己手動更新，沒辦法用 git 的方式更新，增加錯誤的機會。git 針對這個使用情景的解決方式就是 submodule。

使用到git submodule有兩個種情況，是載入別人的project，發現裡面有用到 submodule，例如知名的補齊工具 YouCompleteMe ，裡面針對各種語言的剖析工具都是 submodule，這些專案載下來的時候， submodule 裡面都還是空的，要先用下列指令把 submodule 載下來。

這裡我們先用YouCompleteMe當作例子來做示範
首先我們先在透過github把YouCompleteMe的檔案下載下來
![image]()
</textarea>

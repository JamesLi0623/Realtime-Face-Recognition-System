![](https://i.imgur.com/YKIltkp.jpg)

## 執行專案前先安裝對應套件，步驟如下
1. anaconda prompt切到要裝的環境
2. 輸入 'pip install -r PATH/requirements.txt'
3. 然後等他自己跑完就裝好了，dlib裝很久及跳編碼錯誤是正常的，我12thread裝了快5分鐘

## Note: 
如果自己手動安裝的話切記要照順序裝，不然會失敗。不過建議直接用我打包好的requirements裝啦，如果部分套件已經安裝過的它會自己跳過。


### V1.8版 (李恩)
1. 這版是加速版，未來都以加速版為更新主體，慢速版若無特殊需要暫時不更新
2. 本版把索引資料的資料結構換成class，方便日後管理
3. API 中 addPerson() 參數資料有變更，且本版配合使用模型修正為新加入的參考資料會在陣列的最前端以提升命中率，務必整個 james_module.py 一起更新


### V1.7版 (李恩)
這版是加速版，比前一版(1.6.1)改了很多部分，主要加速變更是 : 
1. 將每一幀輸入影像的邊長大小降為1/2，也就是像素變1/4以壓低處理複雜度，但UI輸出畫質不變
2. 只偵測影像中的每個其他幀中的臉(也就是指偵測差異變化)
3. 這樣做的後遺症是會大幅歧視低畫素的 WebCam，容易無法辨識(速度/準度 的權衡)，可耨過參數微調來改善


### V1.6.1版 (李恩)
1. 編寫新的動態加入索引資料組code，支援連續加入多組，位於 RunMe.py 46行
2. 刪除原本簡陋的新增功能
3. 這只是小改版


### V1.6版 (李恩)

1. 增加自訂函式庫 : james_module
2. 增加自訂函式 : addPerson() 位於 james_module，用以動態新增「照片+名稱」組合於索引資料List
3. 增加 addPerson() 使用範例，位於 RunMe.py 46~49行


### V1.0版 (李恩)

1. 能夠在具有正臉照片的情況下辨識 WebCam 中的正臉影像，可識別者顯示名稱；不可識別者顯示 "Unknown"
2. 具有在 code 內靜態增加索引資料組能力，範例位於 RunMe.py 14~43行
3. 識別門檻可在 RunMe.py 60行之 face_recognition.compare_faces(tolerance) 調整，並非愈高或愈低愈準，此為兩張臉特徵值之公差門檻，需微調尋找最佳值

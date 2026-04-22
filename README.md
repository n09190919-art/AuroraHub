<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Aurora Hub 數位小卡</title>
    <style>
        /* 整體風格設定：奶灰與奶茶色系 */
        :root {
            --bg-gray: #EAEAEA; /* 現代奶灰背景 */
            --milk-tea: #D9C5B2; /* 核心奶茶色 */
            --milk-tea-dark: #B8A38F;
            --text-main: #4A4A4A;
            --white: #FFFFFF;
        }

        * {
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            margin: 0;
            padding: 0;
            background-color: var(--bg-gray);
            font-family: "PingFang TC", "Heiti TC", "Microsoft JhengHei", sans-serif;
            color: var(--text-main);
            line-height: 1.6;
            display: flex;
            justify-content: center;
        }

        .container {
            width: 100%;
            max-width: 430px; /* 模擬手機寬度 */
            background-color: var(--bg-gray);
            min-height: 100vh;
            position: relative;
            /* 底部預留空間 */
            padding-bottom: 120px;
        }

        /* 標題區 */
        .header {
            padding: 40px 20px 20px;
            text-align: center;
            background-color: var(--bg-gray);
        }

        .header h1 {
            margin: 0;
            font-size: 24px;
            letter-spacing: 2px;
            color: var(--text-main);
        }

        .header p {
            margin: 5px 0 0;
            font-size: 14px;
            color: var(--milk-tea-dark);
            letter-spacing: 1px;
        }

        /* 黏性導航分頁 (Sticky Tabs) */
        .tabs-wrapper {
            position: -webkit-sticky;
            position: sticky;
            top: 0;
            z-index: 100;
            background-color: var(--bg-gray);
            padding: 10px 0;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
        }

        .tabs {
            display: flex;
            justify-content: space-around;
            padding: 0 10px;
        }

        .tab-btn {
            background: none;
            border: none;
            padding: 8px 5px;
            font-size: 14px;
            color: var(--text-main);
            cursor: pointer;
            position: relative;
            white-space: nowrap;
        }

        .tab-btn.active {
            color: var(--milk-tea-dark);
            font-weight: bold;
        }

        .tab-btn.active::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 20%;
            width: 60%;
            height: 2px;
            background-color: var(--milk-tea);
        }

        /* 內容區塊 */
        .content-section {
            display: none;
            padding: 20px;
            animation: fadeIn 0.3s ease;
        }

        .content-section.active {
            display: block;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .card {
            background-color: var(--white);
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.02);
        }

        h2 {
            font-size: 18px;
            margin-top: 0;
            color: var(--milk-tea-dark);
            border-left: 4px solid var(--milk-tea);
            padding-left: 10px;
            margin-bottom: 15px;
        }

        /* 列表樣式 */
        .price-item, .promo-item {
            display: flex;
            justify-content: space-between;
            margin-bottom: 10px;
            border-bottom: 1px dashed #eee;
            padding-bottom: 5px;
            /* 避免不自然斷行 */
            word-break: keep-all; 
        }

        .price-item span:last-child {
            color: var(--milk-tea-dark);
            font-weight: bold;
        }

        .notice-list {
            padding: 0;
            list-style: none;
            font-size: 14px;
        }

        .notice-list li {
            margin-bottom: 12px;
            position: relative;
            padding-left: 20px;
        }

        .notice-list li::before {
            content: '•';
            position: absolute;
            left: 0;
            color: var(--milk-tea);
            font-weight: bold;
        }

        /* 預約按鈕樣式 */
        .btn-group {
            display: flex;
            flex-direction: column;
            gap: 15px;
            margin-top: 20px;
        }

        .btn {
            display: block;
            text-align: center;
            padding: 15px;
            border-radius: 10px;
            text-decoration: none;
            font-weight: bold;
            transition: 0.3s;
        }

        .btn-primary {
            background-color: var(--milk-tea);
            color: white;
        }

        .btn-line {
            background-color: #06C755;
            color: white;
        }

        .highlight {
            color: #d9534f;
            font-weight: bold;
        }

    </style>
</head>
<body>

<div class="container">
    <div class="header">
        <h1>Aurora Hub</h1>
        <p>心 靈 與 美 睫 的 療 癒 空 間</p>
    </div>

    <div class="tabs-wrapper">
        <div class="tabs">
            <button class="tab-btn active" onclick="openTab(event, 'promo')">當月優惠</button>
            <button class="tab-btn" onclick="openTab(event, 'notice')">預約須知</button>
            <button class="tab-btn" onclick="openTab(event, 'price')">價目表</button>
            <button class="tab-btn" onclick="openTab(event, 'booking')">預約方式</button>
        </div>
    </div>

    <div id="promo" class="content-section active">
        <div class="card">
            <h2>🎁 五月限定活動</h2>
            <p style="font-weight: bold; text-align: center;">【寵愛自己・療癒盛典】</p>
            <p style="font-size: 13px; text-align: center; color: #888;">活動期間：即日起 - 2026/05/31</p>
            
            <h3 style="font-size: 15px; color: var(--milk-tea-dark);">1. 初夏滑溜專區 (除毛限定)</h3>
            <div class="promo-item">
                <span>【清爽必備】 VIO 私密處全除 + 腋下</span>
                <span>$1,499</span>
            </div>
            <div class="promo-item">
                <span>【夏日美腿】 全腿 + 腋下</span>
                <span>$1,699</span>
            </div>
            <div class="promo-item">
                <span>【絲滑女神】 全手臂 + 全腿</span>
                <span>$1,999</span>
            </div>

            <h3 style="font-size: 15px; color: var(--milk-tea-dark); margin-top: 20px;">2. 睫毛/耳燭活動</h3>
            <ul class="notice-list">
                <li>單人預約：享 <span class="highlight">9 折</span> 優惠</li>
                <li>兩人同行：享 <span class="highlight">85 折</span> 優惠</li>
                <li style="font-size: 12px; color: #888;">兩人可預約不同項目，同時預約成功即可享折扣</li>
            </ul>
        </div>
    </div>

    <div id="notice" class="content-section">
        <div class="card">
            <h2>基本預約規範</h2>
            <ul class="notice-list">
                <li>女性專屬 ｜ 本工作室為女性專屬空間 🚫 不得攜伴</li>
                <li>準時預約 ｜ 遲到超過 15 分鐘將自動取消預約</li>
                <li>變更取消 ｜ 需改期請於 <span class="highlight">3 天前</span> 告知</li>
                <li>補貼費用 ｜ 若因個人因素臨時取消，需補貼損失費用，且下次預約需預付訂金 500 元</li>
            </ul>
        </div>

        <div class="card">
            <h2>🍯 熱蠟除毛・須知</h2>
            <ul class="notice-list">
                <li>毛髮長度 ｜ 請勿自行刮除，毛髮需有 <span class="highlight">1 公分以上</span> 才能施作</li>
                <li>皮膚狀況 ｜ 施作部位需無傷口、發炎或傳染性皮膚疾病</li>
                <li>特殊時期 ｜ 生理期可塞棉條施作 ｜ <span class="highlight">暫不接孕婦</span></li>
                <li>產品暫停 ｜ 施作前 7 天請暫停使用酸類保養品或藥物</li>
                <li>行程安排 ｜ 有玩水行程請提早 3-5 天施作</li>
                <li>穿著建議 ｜ 建議穿著「寬鬆、透氣舒適」的衣服</li>
            </ul>
        </div>

        <div class="card">
            <h2>👁 睫毛 / 野生眉・須知</h2>
            <ul class="notice-list">
                <li>眼周素顏 ｜ 當天不能帶眼妝（睫毛膏、眼線），可上底妝</li>
                <li>術後照顧 ｜ 操作後 4 小時內建議不要碰水洗臉</li>
                <li>野生眉長度 ｜ <span class="highlight">前 1-2 天請勿自行修剪</span> 眉毛長短</li>
                <li>售後服務 ｜ 若需調整弧度，可於 3 日內回來重新操作</li>
            </ul>
        </div>

        <div class="card">
            <h2>👂 耳燭舒壓・須知</h2>
            <ul class="notice-list">
                <li>健康確認 ｜ 耳朵發炎、有分泌物、耳膜破損或生理期期間暫不建議</li>
                <li>放鬆體驗 ｜ 過程中請保持放鬆，對溫度敏感請隨時告知</li>
            </ul>
        </div>
    </div>

    <div id="price" class="content-section">
        <div class="card">
            <h2>🍯 熱蠟除毛價目表</h2>
            <p style="font-size: 12px; color: #999; margin-bottom: 10px;">【 核心熱門 】</p>
            <div class="price-item"><span>私密處全除 (VIO)</span><span>$1,199</span></div>
            <div class="price-item"><span>腋下</span><span>$400</span></div>
            
            <p style="font-size: 12px; color: #999; margin: 15px 0 10px;">【 手部系列 】</p>
            <div class="price-item"><span>前手臂 (手肘以下)</span><span>$450</span></div>
            <div class="price-item"><span>全手臂</span><span>$900</span></div>

            <p style="font-size: 12px; color: #999; margin: 15px 0 10px;">【 腿部系列 】</p>
            <div class="price-item"><span>小腿</span><span>$900</span></div>
            <div class="price-item"><span>全腿</span><span>$1,399</span></div>
        </div>

        <div class="card">
            <h2>🕯️ 睫毛管理 & 耳燭 (原價)</h2>
            <div class="price-item"><span>水光睫 (似角蛋白)</span><span>$1,200</span></div>
            <div class="price-item"><span>眉毛雕塑 (野生眉)</span><span>$1,400</span></div>
            <div class="price-item"><span>耳燭舒壓 SPA</span><span>$1,000</span></div>
        </div>
    </div>

    <div id="booking" class="content-section">
        <div class="card" style="text-align: center;">
            <h2>立即預約</h2>
            <p style="font-size: 14px; color: #666;">點擊下方按鈕跳轉至預約系統</p>
            <div class="btn-group">
                <a href="https://go.hotcake.app/g/9IZHN8" class="btn btn-primary" target="_blank">✨ 夯客系統 立即預約</a>
                <a href="https://line.me/R/ti/p/@144ukdbp" class="btn btn-line" target="_blank">💬 官方 Line 諮詢</a>
            </div>
        </div>
    </div>
</div>

<script>
    function openTab(evt, tabName) {
        var i, content, tablinks;
        
        // 隱藏所有內容
        content = document.getElementsByClassName("content-section");
        for (i = 0; i < content.length; i++) {
            content[i].classList.remove("active");
        }

        // 移除按鈕的 active 狀態
        tablinks = document.getElementsByClassName("tab-btn");
        for (i = 0; i < tablinks.length; i++) {
            tablinks[i].classList.remove("active");
        }

        // 顯示當前分頁並將按鈕設為 active
        document.getElementById(tabName).classList.add("active");
        evt.currentTarget.classList.add("active");
        
        // 切換分頁時自動回到頂部（導航列下方）
        window.scrollTo({ top: 0, behavior: 'smooth' });
    }
</script>

</body>
</html>

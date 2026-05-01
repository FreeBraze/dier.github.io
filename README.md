<!DOCTYPE html>
<html lang="zh-CN">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>单词趣味消消乐 - Unit 2</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: "Microsoft YaHei", sans-serif;
    }

    body {
      background: linear-gradient(135deg, #e6f7ff, #c2e9fb);
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
      position: relative;
      overflow-x: hidden;
    }

    .wave {
      position: fixed;
      bottom: 0;
      left: 0;
      width: 100%;
      height: 100px;
      background: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 120" preserveAspectRatio="none"><path d="M0,0V46.29c47.79,22.2,103.59,32.17,158,28,70.36-5.37,136.33-33.31,206.8-37.5C438.64,32.43,512.34,53.67,583,72.05c69.27,18,138.3,24.88,209.4,13.08,36.15-6,69.85-17.84,104.45-29.34C989.49,25,1113-14.29,1200,52.47V0Z" opacity=".25" fill="%2346a0f5"/><path d="M0,0V15.81C13,36.92,27.64,56.86,47.69,72.05,99.41,111.27,165,111,224.58,91.58c31.15-10.15,60.09-26.07,89.67-39.8,40.92-19,84.73-46,130.83-49.67,36.26-2.85,70.9,9.42,98.6,31.56,31.77,25.39,62.32,62,103.63,73,40.44,10.79,81.35-6.69,119.13-24.28s75.16-39,116.92-43.05c59.73-5.85,113.28,22.88,168.9,38.84,30.2,8.66,59,6.17,87.09-7.5,22.43-10.89,48-26.93,60.65-49.24V0Z" opacity=".5" fill="%2346a0f5"/><path d="M0,0V5.63C149.93,59,314.09,71.32,475.83,42.57c43-7.64,84.23-20.12,127.61-26.46,59-8.63,112.48,12.24,165.56,35.4C827.93,77.22,886,95.24,951.2,90c86.53-7,172.46-45.71,248.8-84.81V0Z" fill="%2346a0f5"/></svg>');
      background-size: cover;
      z-index: 1;
    }

    .books {
      position: fixed;
      bottom: 30px;
      left: 50%;
      transform: translateX(-50%);
      display: flex;
      gap: 10px;
      z-index: 2;
    }

    .book {
      width: 40px;
      height: 50px;
      background: #8B4513;
      border-radius: 3px;
      position: relative;
    }

    .book:nth-child(2) {
      background: #A0522D;
      height: 55px;
    }

    .book:nth-child(3) {
      background: #CD853F;
      height: 45px;
    }

    .book::after {
      content: "";
      position: absolute;
      top: 5px;
      left: 5px;
      right: 5px;
      bottom: 5px;
      background: rgba(255, 255, 255, 0.1);
      border-radius: 2px;
    }

    .flower-branch {
      position: fixed;
      top: 20px;
      right: 20px;
      width: 100px;
      height: 120px;
      z-index: 2;
    }

    .branch {
      position: absolute;
      width: 5px;
      height: 100px;
      background: #8B7355;
      top: 0;
      right: 50px;
      border-radius: 3px;
      transform: rotate(-10deg);
    }

    .flower {
      position: absolute;
      width: 25px;
      height: 25px;
      background: #FFB6C1;
      border-radius: 50%;
      top: 15px;
      right: 35px;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .flower::before {
      content: "";
      position: absolute;
      width: 10px;
      height: 10px;
      background: #FFD700;
      border-radius: 50%;
    }

    .petal {
      position: absolute;
      width: 8px;
      height: 8px;
      background: #FFB6C1;
      border-radius: 50%;
    }

    .petal:nth-child(1) {
      top: -5px;
      left: 50%;
      transform: translateX(-50%);
    }

    .petal:nth-child(2) {
      top: 50%;
      right: -5px;
      transform: translateY(-50%);
    }

    .petal:nth-child(3) {
      bottom: -5px;
      left: 50%;
      transform: translateX(-50%);
    }

    .petal:nth-child(4) {
      top: 50%;
      left: -5px;
      transform: translateY(-50%);
    }

    .leaf {
      position: absolute;
      width: 15px;
      height: 10px;
      background: #90EE90;
      border-radius: 50% 0 50% 0;
      top: 40px;
      right: 45px;
      transform: rotate(45deg);
    }

    .leaf:nth-child(2) {
      top: 60px;
      right: 40px;
      transform: rotate(-30deg);
    }

    .container {
      width: 100%;
      max-width: 1200px;
      background: white;
      border-radius: 20px;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
      padding: 30px;
      margin: 0 auto;
      z-index: 3;
      position: relative;
    }

    .page {
      display: none;
      width: 100%;
    }

    .page.active {
      display: block;
    }

    .unit-selection-page h1 {
      text-align: center;
      color: #6a5acd;
      margin-bottom: 30px;
      font-size: 2.5rem;
    }

    .units-container {
      display: flex;
      flex-wrap: wrap;
      gap: 20px;
      justify-content: center;
    }

    .unit-item {
      display: flex;
      width: 100%;
      max-width: 350px;
      margin-bottom: 20px;
    }

    .unit-circle {
      width: 80px;
      height: 80px;
      background: #FFD700;
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      box-shadow: 0 5px 15px rgba(255, 215, 0, 0.3);
      margin-right: 20px;
      flex-shrink: 0;
    }

    .unit-circle span {
      font-size: 1.5rem;
      font-weight: bold;
      color: #333;
    }

    .unit-card {
      flex-grow: 1;
      background: #f9f9f9;
      border-radius: 15px;
      padding: 15px;
      text-align: left;
      cursor: pointer;
      transition: all 0.3s;
      border: 2px solid transparent;
    }

    .unit-card:hover {
      transform: translateY(-5px);
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
      border-color: #6a5acd;
    }

    .unit-card h3 {
      color: #333;
      margin-bottom: 5px;
      font-size: 1.2rem;
    }

    .unit-card p {
      color: #666;
      font-size: 0.9rem;
    }

    .unit-detail-page {
      text-align: center;
    }

    .btn-back {
      position: absolute;
      top: 20px;
      left: 20px;
      background: #6a5acd;
      color: white;
      border: none;
      border-radius: 50%;
      width: 50px;
      height: 50px;
      font-size: 1.5rem;
      cursor: pointer;
      display: flex;
      justify-content: center;
      align-items: center;
      transition: all 0.3s;
    }

    .btn-back:hover {
      background: #5a4abd;
      transform: scale(1.1);
    }

    .unit-detail-page .unit-circle {
      width: 120px;
      height: 120px;
      margin: 0 auto 30px;
    }

    .unit-detail-page .unit-circle span {
      font-size: 2.5rem;
    }

    .dropdown-area {
      margin: 30px 0;
      position: relative;
    }

    .dropdown {
      width: 100%;
      padding: 15px 20px;
      background: white;
      border: 2px solid #E0E0E0;
      border-radius: 10px;
      font-size: 1.2rem;
      text-align: center;
      cursor: pointer;
      transition: all 0.3s;
    }

    .dropdown:hover {
      border-color: #6a5acd;
    }

    .button-group {
      display: flex;
      flex-direction: column;
      gap: 15px;
      margin-top: 30px;
    }

    .btn {
      padding: 15px 30px;
      border: none;
      border-radius: 10px;
      font-size: 1.2rem;
      font-weight: bold;
      cursor: pointer;
      transition: all 0.3s;
    }

    .btn-challenge {
      background: #D2B48C;
      color: white;
    }

    .btn-challenge:hover {
      background: #C19A6B;
      transform: translateY(-3px);
      box-shadow: 0 5px 15px rgba(194, 154, 107, 0.3);
    }

    .btn-pk {
      background: #FFD700;
      color: #333;
    }

    .btn-pk:hover {
      background: #FFC400;
      transform: translateY(-3px);
      box-shadow: 0 5px 15px rgba(255, 196, 0, 0.3);
    }

    .game-page h1 {
      text-align: center;
      color: #6a5acd;
      margin-bottom: 20px;
      font-size: 2.5rem;
    }

    .game-controls {
      display: flex;
      justify-content: space-between;
      flex-wrap: wrap;
      margin-bottom: 20px;
      gap: 15px;
      background: #f8f9ff;
      padding: 15px;
      border-radius: 15px;
    }

    .control-group {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      align-items: center;
    }

    select,
    button {
      padding: 10px 15px;
      border: none;
      border-radius: 10px;
      font-size: 1rem;
      cursor: pointer;
      transition: all 0.3s;
    }

    select {
      background-color: #f0f8ff;
      border: 2px solid #b0e0e6;
      min-width: 120px;
    }

    button {
      background: linear-gradient(to right, #6a5acd, #9370db);
      color: white;
      font-weight: bold;
    }

    button:hover {
      transform: translateY(-2px);
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
    }

    .game-info {
      display: flex;
      justify-content: space-between;
      margin-bottom: 20px;
      font-size: 1.2rem;
      font-weight: bold;
      color: #555;
      background: #f0f8ff;
      padding: 10px 20px;
      border-radius: 10px;
    }

    .timer {
      font-size: 1.8rem;
      text-align: center;
      margin: 20px 0;
      color: #ff6347;
      font-weight: bold;
      background: #fff9f0;
      padding: 10px;
      border-radius: 10px;
    }

    .game-board {
      display: flex;
      gap: 20px;
      margin-bottom: 20px;
    }

    .player-section {
      flex: 1;
      background: #f9f9f9;
      border-radius: 15px;
      padding: 15px;
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
      min-height: 400px;
    }

    .player-header {
      text-align: center;
      margin-bottom: 15px;
      font-size: 1.3rem;
      color: #6a5acd;
      padding-bottom: 10px;
      border-bottom: 2px solid #e6e6fa;
    }

    .cards-container {
      display: flex;
      flex-wrap: wrap;
      gap: 12px;
      justify-content: center;
      min-height: 300px;
      align-content: flex-start;
    }

    .card {
      padding: 15px 20px;
      border-radius: 12px;
      font-size: 1.5rem;
      font-weight: bold;
      text-align: center;
      cursor: pointer;
      transition: all 0.3s;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
      user-select: none;
      min-width: 120px;
      display: flex;
      align-items: center;
      justify-content: center;
      word-break: break-word;
    }

    .english-card {
      background: linear-gradient(135deg, #ffb6c1, #ff69b4);
      color: #8b0000;
    }

    .chinese-card {
      background: linear-gradient(135deg, #87ceeb, #1e90ff);
      color: #000080;
    }

    .card.selected {
      transform: scale(1.1);
      box-shadow: 0 0 15px 5px rgba(255, 215, 0, 0.7);
      z-index: 10;
    }

    .card.matched {
      visibility: hidden;
      opacity: 0;
      transform: scale(0);
      transition: all 0.5s;
    }

    .card.wrong {
      animation: shake 0.5s;
      background: linear-gradient(135deg, #ff9999, #ff3333);
    }

    @keyframes shake {

      0%,
      100% {
        transform: translateX(0);
      }

      20%,
      60% {
        transform: translateX(-5px);
      }

      40%,
      80% {
        transform: translateX(5px);
      }
    }

    .current-player-indicator {
      background: #ffeb3b;
      color: #333;
      padding: 5px 15px;
      border-radius: 20px;
      font-weight: bold;
      margin-top: 10px;
      display: inline-block;
    }

    .modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.7);
      z-index: 100;
      justify-content: center;
      align-items: center;
    }

    .modal-content {
      background: white;
      padding: 30px;
      border-radius: 20px;
      text-align: center;
      max-width: 500px;
      width: 90%;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
    }

    .modal h2 {
      color: #6a5acd;
      margin-bottom: 15px;
    }

    .modal p {
      margin-bottom: 20px;
      font-size: 1.2rem;
    }

    .winner-section {
      display: flex;
      justify-content: center;
      align-items: center;
      margin: 20px 0;
      gap: 20px;
    }

    .winner-trophy {
      font-size: 3rem;
      color: gold;
    }

    .pause-overlay {
      display: none;
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.7);
      z-index: 5;
      justify-content: center;
      align-items: center;
      border-radius: 20px;
    }

    .pause-content {
      background: white;
      padding: 30px;
      border-radius: 15px;
      text-align: center;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
    }

    .pause-content h2 {
      color: #6a5acd;
      margin-bottom: 15px;
    }

    @media (max-width: 768px) {
      .container {
        padding: 30px 20px;
      }

      .unit-selection-page h1 {
        font-size: 2rem;
      }

      .unit-item {
        flex-direction: column;
        align-items: center;
        text-align: center;
      }

      .unit-circle {
        margin-right: 0;
        margin-bottom: 15px;
      }

      .unit-detail-page .unit-circle {
        width: 100px;
        height: 100px;
      }

      .unit-detail-page .unit-circle span {
        font-size: 2rem;
      }

      .dropdown {
        font-size: 1rem;
      }

      .btn {
        font-size: 1rem;
        padding: 12px 25px;
      }

      .game-board {
        flex-direction: column;
      }

      .game-controls {
        flex-direction: column;
        align-items: center;
      }

      h1 {
        font-size: 1.8rem;
      }

      .card {
        font-size: 1.2rem;
        min-width: 100px;
        padding: 12px 15px;
      }

      .control-group {
        justify-content: center;
      }
    }
  </style>
</head>

<body>
  <div class="wave"></div>

  <div class="books">
    <div class="book"></div>
    <div class="book"></div>
    <div class="book"></div>
  </div>

  <div class="flower-branch">
    <div class="branch"></div>
    <div class="flower">
      <div class="petal"></div>
      <div class="petal"></div>
      <div class="petal"></div>
      <div class="petal"></div>
    </div>
    <div class="leaf"></div>
    <div class="leaf"></div>
  </div>

  <div class="container">
    <div class="page unit-selection-page active" id="unitSelectionPage">
      <div class="units-container">
        <div class="unit-item">
          <div class="unit-circle">
            <span>Unit 1</span>
          </div>
          <div class="unit-card" data-unit="1">
            <h3>Secrets to beauty</h3>
            <p>美丽的秘诀</p>
          </div>
        </div>
      </div>
    </div>

    <div class="page unit-detail-page" id="unitDetailPage">
      <button class="btn-back" id="backButton">←</button>

      <div class="unit-circle">
        <span id="currentUnit">Unit 1</span>
      </div>

      <div class="dropdown-area">
        <div class="dropdown" id="unitDropdown">The digital age: Are we ready?</div>
      </div>

      <div class="game-controls">
        <div class="control-group">
          <label for="difficulty">难度选择：</label>
          <select id="difficulty">
            <option value="5">容易（5词）</option>
            <option value="10" selected>普通（10词）</option>
            <option value="15">困难（15词）</option>
          </select>
        </div>
      </div>

      <div class="button-group">
        <button class="btn btn-challenge" id="challengeButton">开始闯关</button>
        <button class="btn btn-pk" id="pkButton">双人PK</button>
      </div>
    </div>

    <div class="page game-page" id="gamePage">
      <button class="btn-back" id="backToDetailButton">←</button>

      <h1>单词趣味消消乐</h1>

      <div class="game-controls">
        <div class="control-group">
          <div>当前单元: <span id="currentUnitDisplay">Unit 1</span></div>
          <div>游戏模式: <span id="currentModeDisplay">单人模式</span></div>
          <div>难度: <span id="currentDifficultyDisplay">普通（10词）</span></div>
        </div>

        <div class="control-group">
          <button id="startBtn">开始游戏</button>
          <button id="pauseBtn">暂停</button>
          <button id="restartBtn">重新开始</button>
        </div>
      </div>

      <div class="game-info">
        <div>玩家1得分: <span id="player1Score">0</span></div>
        <div>玩家2得分: <span id="player2Score">0</span></div>
      </div>

      <div class="timer">
        用时: <span id="timerDisplay">00:00</span>
      </div>

      <div class="pause-overlay" id="pauseOverlay">
        <div class="pause-content">
          <h2>游戏已暂停</h2>
          <p>点击"继续"按钮恢复游戏</p>
          <button id="resumeBtn">继续</button>
        </div>
      </div>

      <div class="game-board">
        <div class="player-section">
          <div class="player-header">玩家1</div>
          <div id="player1Indicator" class="current-player-indicator" style="display: none;">当前玩家</div>
          <div class="cards-container" id="player1Cards"></div>
        </div>

        <div class="player-section">
          <div class="player-header">玩家2</div>
          <div id="player2Indicator" class="current-player-indicator" style="display: none;">当前玩家</div>
          <div class="cards-container" id="player2Cards"></div>
        </div>
      </div>
    </div>
  </div>

  <div class="modal" id="successModal">
    <div class="modal-content">
      <h2>游戏完成！</h2>
      <div class="winner-section">
        <div class="winner-trophy">🏆</div>
        <div>
          <p id="winnerText">玩家1获胜！</p>
          <p>用时: <span id="completionTime">00:00</span></p>
        </div>
        <div class="winner-trophy">🏆</div>
      </div>
      <button id="closeModal">返回主页面</button>
    </div>
  </div>

  <script>
    const wordData = {
      1: [
        { english: "privilege", chinese: "n. 1 [sing.] 荣幸；殊荣 2 [C] 特权；特殊待遇" },
        { english: "corrode", chinese: "v. 1 （逐渐地）损害，伤害 2 （使）腐蚀；（使）侵蚀" },
        { english: "dread", chinese: "n. [sing., U] 恐惧；害怕；vt. 畏惧；惧怕；担心" },
        { english: "outgoing", chinese: "a. 1 外向的；好交际的 2 即将离任的" },
        { english: "esthetic", chinese: "a. 审美的；美学的；艺术的；n. [U] 美学；审美学" },
        { english: "scar", chinese: "vt. 1 使遭受（精神）创伤 2 在…上留下疤痕；n. 1 精神创伤 2 伤疤；伤痕" },
        { english: "preface", chinese: "vt. 给…做开场白；为…写序言；n. 前言；序言；开场白" },
        { english: "exempt", chinese: "a. 被免除（义务）的；被豁免的" },
        { english: "underscore", chinese: "vt. 1 强调 2 在…的底下画线（以示强调）" },
        { english: "dietary", chinese: "a. 与饮食有关的" },
        { english: "protein", chinese: "n. [C, U] 蛋白质" },
        { english: "supplement", chinese: "n. [C] 1 增补物；补充物；补给品 2 附录；补编；增刊；vt. 补充；增补" },
        { english: "capsule", chinese: "n. [C] 1 胶囊 2 （太空飞行器的）密封舱，太空舱" },
        { english: "meditation", chinese: "n. 1 [U] 冥想；默念；打坐 2 [C, U] 沉思；深思" },
        { english: "manipulation", chinese: "n. 1 [C, U] （巧妙或不诚实的）操纵，控制 2 [U] （熟练的）操作" },
        { english: "interwoven", chinese: "a. 交织的；紧密结合的" },
        { english: "fracture", chinese: "v. 1 （使）折断；断裂 2 （使）分裂；n. [C] 骨折；裂缝；裂痕" },
        { english: "register", chinese: "v. 1 显示；指示；表达 2 记录；登记" },
        { english: "authentic", chinese: "a. 1 可靠的；真实的 2 真的；非复制的 3 正宗的；地道的" },
        { english: "radiant", chinese: "a. 1 灿烂的；明亮的 2 容光焕发的；喜悦的" },
        { english: "radiantly", chinese: "ad. 1 灿烂地；明亮地 2 容光焕发地；喜悦地" },
        { english: "enquire", chinese: "v. 询问；打听" },
        { english: "embodiment", chinese: "n. [sing.] 体现；化身" },
        { english: "mortal", chinese: "a. 1 不能永生的 2 致命的" },
        { english: "checkpoint", chinese: "n. [C] （尤指边境的）关卡，检查站" },
        { english: "purify", chinese: "vt. 1 净化（心灵） 2 净化；使纯净" },
        { english: "resolution", chinese: "n. [C] 1 决心 2 决议，正式决定" },
        { english: "regiment", chinese: "n. [C] 1 一大群；大量 2 （军队的）团" },
        { english: "hamper", chinese: "vt. 1 阻碍；妨碍 2 限制；束缚" },
        { english: "stylish", chinese: "a. 时髦的；有品位的" },
        { english: "costume", chinese: "n. [C, U] 1 （特定地方/历史时期的）服装 2 演出服；戏装" },
        { english: "galaxy", chinese: "n. 1 [C] 星系 2 [sing.] 一大批（相似的人或物）" },
        { english: "symphony", chinese: "n. [C] 交响曲；交响乐" },
        { english: "majestic", chinese: "a. 雄伟的；壮丽的；威严的" },
        { english: "bruise", chinese: "v. （使）碰伤，擦伤；挫伤（自信心）" },
        { english: "collide", chinese: "vi. 1 冲突；抵触 2 碰撞；相撞" },
        { english: "elicit", chinese: "vt. 1 引出，引起（反应） 2 探出（信息）" },
        { english: "eternity", chinese: "n. 1 [U] 永恒 2 [C] 极长一段时间" },
        { english: "barren", chinese: "a. 1 无趣味的；无吸引力的 2 贫瘠的，荒芜的" },
        { english: "stumble", chinese: "vi. 1 蹒跚而行；踉跄 2 绊脚；绊了一下 3 打结巴；说错" },
        { english: "knit", chinese: "v. 1 （使）紧密结合 2 编织；针织" },
        { english: "illuminate", chinese: "vt. 1 照亮；照明；照射 2 阐明；解释" },
        { english: "indulgent", chinese: "a. 溺爱的，纵容的，放任的" },
        { english: "self-indulgent", chinese: "a. 自我放纵的" },
        { english: "wear (sth.) out", chinese: "用坏；（使）磨损" },
        { english: "seek out", chinese: "找出；找到" },
        { english: "be accountable to", chinese: "对…负有责任" },
        { english: "be addicted to", chinese: "1 对…痴迷；沉迷 2 （吸毒）成瘾的" },
        { english: "be exempt from", chinese: "被免除（义务、责任或付款）" },
        { english: "stumble through /across/into", chinese: "摇摇晃晃移动；步履蹒跚" },
        { english: "approve of", chinese: "赞成；同意；赞许" },
        { english: "enquire about", chinese: "询问；打听" },
        { english: "Richard", chinese: "理查德（人名）" }
      ]
    };

    const unitData = {
      1: {
        title: "Unit 1",
        topic: "The digital age: Are we ready?",
        description: "数字时代：我们准备好了吗？"
      }
    };

    let gameActive = false;
    let gameStarted = false;
    let gamePaused = false;
    let startTime;
    let pauseStartTime = 0;
    let totalPauseTime = 0;
    let timerInterval;
    let currentPlayer = 1;
    let selectedCard = null;
    let player1Score = 0;
    let player2Score = 0;
    let player1Matched = 0;
    let player2Matched = 0;
    let totalPairs = 0;
    let gameMode = "single";
    let currentUnit = 1;
    let currentDifficulty = 10;

    const unitSelectionPage = document.getElementById('unitSelectionPage');
    const unitDetailPage = document.getElementById('unitDetailPage');
    const gamePage = document.getElementById('gamePage');
    const unitCards = document.querySelectorAll('.unit-card');
    const backButton = document.getElementById('backButton');
    const backToDetailButton = document.getElementById('backToDetailButton');
    const currentUnitElement = document.getElementById('currentUnit');
    const unitDropdown = document.getElementById('unitDropdown');
    const challengeButton = document.getElementById('challengeButton');
    const pkButton = document.getElementById('pkButton');
    const startBtn = document.getElementById('startBtn');
    const pauseBtn = document.getElementById('pauseBtn');
    const resumeBtn = document.getElementById('resumeBtn');
    const restartBtn = document.getElementById('restartBtn');
    const difficultySelect = document.getElementById('difficulty');
    const timerDisplay = document.getElementById('timerDisplay');
    const player1ScoreDisplay = document.getElementById('player1Score');
    const player2ScoreDisplay = document.getElementById('player2Score');
    const player1CardsContainer = document.getElementById('player1Cards');
    const player2CardsContainer = document.getElementById('player2Cards');
    const player1Indicator = document.getElementById('player1Indicator');
    const player2Indicator = document.getElementById('player2Indicator');
    const successModal = document.getElementById('successModal');
    const winnerText = document.getElementById('winnerText');
    const completionTime = document.getElementById('completionTime');
    const closeModalBtn = document.getElementById('closeModal');
    const pauseOverlay = document.getElementById('pauseOverlay');
    const currentUnitDisplay = document.getElementById('currentUnitDisplay');
    const currentModeDisplay = document.getElementById('currentModeDisplay');
    const currentDifficultyDisplay = document.getElementById('currentDifficultyDisplay');

    function showPage(pageId) {
      document.querySelectorAll('.page').forEach(page => {
        page.classList.remove('active');
      });
      document.getElementById(pageId).classList.add('active');
    }

    unitCards.forEach(card => {
      card.addEventListener('click', function () {
        const unitId = parseInt(this.getAttribute('data-unit'));
        currentUnit = unitId;
        updateUnitDetailPage(unitId);
        showPage('unitDetailPage');
      });
    });

    backButton.addEventListener('click', function () {
      showPage('unitSelectionPage');
    });

    backToDetailButton.addEventListener('click', function () {
      showPage('unitDetailPage');
    });

    function updateUnitDetailPage(unitId) {
      const unit = unitData[unitId];
      currentUnitElement.textContent = unit.title;
      unitDropdown.textContent = unit.topic;
    }

    challengeButton.addEventListener('click', function () {
      gameMode = "single";
      currentDifficulty = parseInt(difficultySelect.value);
      showPage('gamePage');
      setupGame();
    });

    pkButton.addEventListener('click', function () {
      gameMode = "double";
      currentDifficulty = parseInt(difficultySelect.value);
      showPage('gamePage');
      setupGame();
    });

    function playSound(type) {
      const audioContext = new (window.AudioContext || window.webkitAudioContext)();
      let oscillator = audioContext.createOscillator();
      let gainNode = audioContext.createGain();

      oscillator.connect(gainNode);
      gainNode.connect(audioContext.destination);

      switch (type) {
        case 'match':
          oscillator.frequency.setValueAtTime(880, audioContext.currentTime);
          gainNode.gain.setValueAtTime(0.5, audioContext.currentTime);
          gainNode.gain.exponentialRampToValueAtTime(0.01, audioContext.currentTime + 0.5);
          break;
        case 'error':
          oscillator.frequency.setValueAtTime(220, audioContext.currentTime);
          gainNode.gain.setValueAtTime(0.5, audioContext.currentTime);
          gainNode.gain.exponentialRampToValueAtTime(0.01, audioContext.currentTime + 0.3);
          break;
        case 'win':
          const frequencies = [523.25, 659.25, 783.99, 1046.50];
          const times = [0, 0.2, 0.4, 0.6];
          frequencies.forEach((freq, i) => {
            setTimeout(() => {
              const osc = audioContext.createOscillator();
              const gain = audioContext.createGain();
              osc.connect(gain);
              gain.connect(audioContext.destination);
              osc.frequency.setValueAtTime(freq, audioContext.currentTime);
              gain.gain.setValueAtTime(0.3, audioContext.currentTime);
              gain.gain.exponentialRampToValueAtTime(0.01, audioContext.currentTime + 0.3);
              osc.start(audioContext.currentTime);
              osc.stop(audioContext.currentTime + 0.3);
            }, times[i] * 1000);
          });
          return;
        case 'select':
          oscillator.frequency.setValueAtTime(659.25, audioContext.currentTime);
          gainNode.gain.setValueAtTime(0.3, audioContext.currentTime);
          gainNode.gain.exponentialRampToValueAtTime(0.01, audioContext.currentTime + 0.2);
          break;
        case 'pause':
          oscillator.frequency.setValueAtTime(440, audioContext.currentTime);
          gainNode.gain.setValueAtTime(0.3, audioContext.currentTime);
          gainNode.gain.exponentialRampToValueAtTime(0.01, audioContext.currentTime + 0.3);
          break;
      }

      oscillator.start(audioContext.currentTime);
      oscillator.stop(audioContext.currentTime + 0.5);
    }

    function setupGame() {
      currentUnitDisplay.textContent = unitData[currentUnit].title;
      currentModeDisplay.textContent = gameMode === "single" ? "单人模式" : "双人对战";
      currentDifficultyDisplay.textContent = getDifficultyText(currentDifficulty);

      gameActive = false;
      gameStarted = false;
      gamePaused = false;
      player1Score = 0;
      player2Score = 0;
      player1Matched = 0;
      player2Matched = 0;
      currentPlayer = 1;
      selectedCard = null;
      totalPauseTime = 0;

      player1ScoreDisplay.textContent = '0';
      player2ScoreDisplay.textContent = '0';
      timerDisplay.textContent = '00:00';

      updatePlayerIndicator();

      player1CardsContainer.innerHTML = '';
      player2CardsContainer.innerHTML = '';

      const words = [...wordData[currentUnit]];
      const selectedWords = [];
      while (selectedWords.length < currentDifficulty && words.length > 0) {
        const randomIndex = Math.floor(Math.random() * words.length);
        selectedWords.push(words[randomIndex]);
        words.splice(randomIndex, 1);
      }

      totalPairs = selectedWords.length;

      if (gameMode === "single") {
        document.querySelector('.player-section:nth-child(2)').style.display = 'none';
        createCards(selectedWords, player1CardsContainer);
      } else {
        document.querySelector('.player-section:nth-child(2)').style.display = 'block';
        createCards(selectedWords, player1CardsContainer);
        createCards(selectedWords, player2CardsContainer);
      }

      clearInterval(timerInterval);

      pauseOverlay.style.display = 'none';
      pauseBtn.textContent = '暂停';

      startBtn.disabled = false;
      pauseBtn.disabled = true;
    }

    function getDifficultyText(difficulty) {
      switch (difficulty) {
        case 5: return "容易（5词）";
        case 10: return "普通（10词）";
        case 15: return "困难（15词）";
        default: return "普通（10词）";
      }
    }

    function startGame() {
      if (gameStarted) return;

      gameActive = true;
      gameStarted = true;

      startTime = new Date();
      clearInterval(timerInterval);
      timerInterval = setInterval(updateTimer, 1000);
      updateTimer();

      startBtn.disabled = true;
      pauseBtn.disabled = false;

      playSound('select');
    }

    function pauseGame() {
      if (!gameActive || gamePaused) return;

      gamePaused = true;
      pauseStartTime = new Date();

      clearInterval(timerInterval);

      pauseOverlay.style.display = 'flex';
      pauseBtn.textContent = '已暂停';

      playSound('pause');
    }

    function resumeGame() {
      if (!gamePaused) return;

      gamePaused = false;

      const pauseEndTime = new Date();
      totalPauseTime += (pauseEndTime - pauseStartTime);

      timerInterval = setInterval(updateTimer, 1000);

      pauseOverlay.style.display = 'none';
      pauseBtn.textContent = '暂停';

      playSound('select');
    }

    function createCards(words, container) {
      const englishCards = [];
      const chineseCards = [];

      words.forEach(word => {
        const englishCard = document.createElement('div');
        englishCard.className = 'card english-card';
        englishCard.textContent = word.english;
        englishCard.dataset.word = word.english;
        englishCard.dataset.type = 'english';
        englishCards.push(englishCard);

        const chineseCard = document.createElement('div');
        chineseCard.className = 'card chinese-card';
        chineseCard.textContent = word.chinese;
        chineseCard.dataset.word = word.english;
        chineseCard.dataset.type = 'chinese';
        chineseCards.push(chineseCard);
      });

      const allCards = [...englishCards, ...chineseCards];
      shuffleArray(allCards);

      allCards.forEach(card => {
        container.appendChild(card);
        card.addEventListener('click', function () {
          handleCardClick(this, container.id === 'player1Cards' ? 1 : 2);
        });
      });
    }

    function shuffleArray(array) {
      for (let i = array.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [array[i], array[j]] = [array[j], array[i]];
      }
      return array;
    }

    function updateTimer() {
      if (!gameActive) return;

      const currentTime = new Date();
      const elapsedTime = Math.floor((currentTime - startTime - totalPauseTime) / 1000);
      const minutes = Math.floor(elapsedTime / 60).toString().padStart(2, '0');
      const seconds = (elapsedTime % 60).toString().padStart(2, '0');

      timerDisplay.textContent = `${minutes}:${seconds}`;
    }

    function updatePlayerIndicator() {
      if (gameMode === "single") {
        player1Indicator.style.display = 'none';
        player2Indicator.style.display = 'none';
      } else {
        player1Indicator.style.display = currentPlayer === 1 ? 'block' : 'none';
        player2Indicator.style.display = currentPlayer === 2 ? 'block' : 'none';
      }
    }

    function handleCardClick(card, player) {
      if (!gameActive || gamePaused) return;

      if (gameMode === "double" && player !== currentPlayer) return;

      if (!card.classList.contains('card') || card.classList.contains('matched')) return;

      if (card === selectedCard) return;

      playSound('select');

      card.classList.add('selected');

      if (!selectedCard) {
        selectedCard = { card: card, player: player };
        return;
      }

      if (selectedCard.card.dataset.word === card.dataset.word &&
        selectedCard.card.dataset.type !== card.dataset.type) {
        setTimeout(() => {
          selectedCard.card.classList.add('matched');
          card.classList.add('matched');
          selectedCard = null;

          playSound('match');

          if (gameMode === "single") {
            player1Score += 5;
            player1Matched++;
            player1ScoreDisplay.textContent = player1Score;
          } else {
            if (currentPlayer === 1) {
              player1Score += 5;
              player1Matched++;
              player1ScoreDisplay.textContent = player1Score;
            } else {
              player2Score += 5;
              player2Matched++;
              player2ScoreDisplay.textContent = player2Score;
            }
          }

          checkGameCompletion();
        }, 300);
      } else {
        setTimeout(() => {
          selectedCard.card.classList.remove('selected');
          card.classList.remove('selected');
          selectedCard = null;

          playSound('error');

          if (gameMode === "double") {
            currentPlayer = currentPlayer === 1 ? 2 : 1;
            updatePlayerIndicator();
          }
        }, 500);
      }
    }

    function checkGameCompletion() {
      if (gameMode === "single") {
        if (player1Matched === totalPairs) {
          endGame();
        }
      } else {
        if (player1Matched === totalPairs || player2Matched === totalPairs) {
          endGame();
        }
      }
    }

    function endGame() {
      gameActive = false;
      gameStarted = false;
      clearInterval(timerInterval);

      let winner;
      if (gameMode === "single") {
        winnerText.textContent = "恭喜你完成了游戏！";
      } else {
        if (player1Matched === totalPairs && player2Matched === totalPairs) {
          if (player1Score > player2Score) {
            winner = 1;
          } else if (player2Score > player1Score) {
            winner = 2;
          } else {
            winner = 0;
          }
        } else if (player1Matched === totalPairs) {
          winner = 1;
        } else {
          winner = 2;
        }

        if (winner === 0) {
          winnerText.textContent = "平局！";
        } else {
          winnerText.textContent = `玩家${winner}获胜！`;
        }
      }

      completionTime.textContent = timerDisplay.textContent;
      successModal.style.display = 'flex';

      playSound('win');
    }

    function restartGame() {
      gameActive = false;
      gameStarted = false;
      clearInterval(timerInterval);
      setupGame();
    }

    function returnToMain() {
      successModal.style.display = 'none';
      gameActive = false;
      gameStarted = false;
      clearInterval(timerInterval);
      player1CardsContainer.innerHTML = '';
      player2CardsContainer.innerHTML = '';
      player1ScoreDisplay.textContent = '0';
      player2ScoreDisplay.textContent = '0';
      timerDisplay.textContent = '00:00';
      document.querySelector('.player-section:nth-child(2)').style.display = 'block';
      showPage('unitSelectionPage');
    }

    startBtn.addEventListener('click', startGame);
    pauseBtn.addEventListener('click', pauseGame);
    resumeBtn.addEventListener('click', resumeGame);
    restartBtn.addEventListener('click', restartGame);
    closeModalBtn.addEventListener('click', returnToMain);

    timerDisplay.textContent = "00:00";
    document.querySelector('.player-section:nth-child(2)').style.display = 'none';
  </script>
</body>

</html>

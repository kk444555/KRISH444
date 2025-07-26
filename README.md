# KRISH444
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SOLO MISSION</title>
    <style>
        /* CSS poora wahi hai jo pichle premium version mein tha */
        @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@500;700&family=Poppins:wght@300;400;600&display=swap');
        :root { --primary-glow: #ffffff; --secondary-glow: #ff33ff; --success-glow: #00ffff; --reward-glow: #ffd700; --primary-text: #ff0000; --dark-bg: #0a0a0a; --dark-gradient: radial-gradient(ellipse at center, #1a1a1a 0%, #0a0a0a 70%); --container-bg: rgba(20, 20, 20, 0.5); --border-color: rgba(255, 255, 255, 0.1); }
        * { margin: 0; padding: 0; box-sizing: border-box; }
        html { font-size: 16px; }
        body { font-family: 'Poppins', sans-serif; background: var(--dark-bg); color: var(--primary-text); display: flex; justify-content: center; align-items: center; min-height: 100vh; padding: 15px; overflow: hidden; }
        #particles-js { position: fixed; width: 100%; height: 100%; z-index: -1; top: 0; left: 0; background-image: var(--dark-gradient); }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
        @keyframes fadeInUp { from { opacity: 0; transform: translateY(20px); } to { opacity: 1; transform: translateY(0); } }
        @keyframes pulseGlow { 0% { box-shadow: 0 0 15px -5px var(--primary-glow), 0 0 30px -15px var(--primary-glow); } 50% { box-shadow: 0 0 25px 0px var(--primary-glow), 0 0 50px -10px var(--primary-glow); } 100% { box-shadow: 0 0 15px -5px var(--primary-glow), 0 0 30px -15px var(--primary-glow); } }
        @keyframes rewardPulse { 0% { filter: drop-shadow(0 0 8px var(--reward-glow)); transform: scale(1); } 50% { filter: drop-shadow(0 0 16px var(--reward-glow)); transform: scale(1.05); } 100% { filter: drop-shadow(0 0 8px var(--reward-glow)); transform: scale(1); } }
        .container { width: 100%; max-width: 480px; padding: 25px; background: var(--container-bg); backdrop-filter: blur(12px); border-radius: 24px; border: 1px solid var(--border-color); z-index: 1; animation: pulseGlow 5s infinite ease-in-out, fadeInUp 0.8s 0.2s cubic-bezier(0.165, 0.84, 0.44, 1) both; display: flex; flex-direction: column; max-height: 95vh; }
        .header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 25px; border-bottom: 1px solid var(--border-color); padding-bottom: 20px; flex-shrink: 0; }
        #day-counter { font-family: 'Orbitron', sans-serif; font-weight: 700; color: var(--primary-glow); text-shadow: 0 0 4px #ff0000, 0 0 10px var(--primary-glow), 0 0 20px var(--primary-glow); font-size: clamp(1.8rem, 6vw, 2.2rem); }
        #digital-clock { font-family: 'Orbitron', sans-serif; background: rgba(0, 0, 0, 0.4); padding: 8px 12px; border-radius: 8px; border: 1px solid var(--border-color); font-size: clamp(1.3rem, 5vw, 1.5rem); }
        .timer-container { text-align: center; margin-bottom: 25px; flex-shrink: 0; }
        #timer, #rest-day-message, #timer-stopped-message { font-family: 'Orbitron', sans-serif; padding: 12px; border-radius: 12px; border: 1px solid; background: rgba(0,0,0,0.2); font-size: clamp(1.2rem, 4.5vw, 1.4rem); transition: all 0.3s ease; }
        #timer { color: var(--primary-glow); border-color: var(--primary-glow); text-shadow: 0 0 8px var(--primary-glow); }
        #rest-day-message { color: var(--reward-glow); border-color: var(--reward-glow); text-shadow: 0 0 8px var(--reward-glow); }
        #timer-stopped-message { color: var(--secondary-glow); border-color: var(--secondary-glow); text-shadow: 0 0 8px var(--secondary-glow); }
        .mission-section { overflow: hidden; display: flex; flex-direction: column; }
        .mission-title { font-family: 'Orbitron', sans-serif; text-align: center; font-size: clamp(1.4rem, 5vw, 1.6rem); margin-bottom: 20px; color: var(--primary-glow); text-shadow: 0 0 5px var(--primary-glow); flex-shrink: 0; }
        .mission-list { list-style: none; overflow-y: auto; padding-right: 10px; }
        .mission-list::-webkit-scrollbar { width: 8px; }
        .mission-list::-webkit-scrollbar-track { background: rgba(0, 0, 0, 0.3); border-radius: 10px; }
        .mission-list::-webkit-scrollbar-thumb { background-color: var(--primary-glow); border-radius: 10px; box-shadow: 0 0 10px var(--primary-glow); }
        .mission-list::-webkit-scrollbar-thumb:hover { background-color: #ff0000; }
        .mission-item { background: rgba(255, 255, 255, 0.03); padding: 18px; margin-bottom: 12px; border-radius: 12px; border-left: 4px solid var(--primary-glow); cursor: pointer; transition: all 0.3s cubic-bezier(0.165, 0.84, 0.44, 1); display: flex; align-items: center; font-size: clamp(1rem, 4vw, 1.1rem); animation: fadeInUp 0.5s both; }
        .mission-item:nth-child(2) { animation-delay: 0.1s; } .mission-item:nth-child(3) { animation-delay: 0.2s; } .mission-item:nth-child(4) { animation-delay: 0.3s; } .mission-item:nth-child(5) { animation-delay: 0.4s; } .mission-item:nth-child(6) { animation-delay: 0.5s; } .mission-item:nth-child(7) { animation-delay: 0.6s; }
        .mission-item:hover { background: rgba(0, 221, 255, 0.1); transform: translateX(5px); }
        .mission-item::before { content: '›'; font-size: 1.8em; line-height: 1; margin-right: 15px; color: var(--primary-glow); transition: all 0.4s ease; }
        .mission-item.completed { color: #888; border-left-color: var(--success-glow); }
        .mission-item.completed .task-text { text-decoration: line-through; text-decoration-thickness: 2px; }
        .mission-item.completed::before { content: '✓'; color: var(--success-glow); transform: rotate(360deg) scale(1.2); }
        #completion-badge { position: fixed; bottom: -100px; left: 50%; transform: translateX(-50%); background: linear-gradient(45deg, var(--success-glow), #2deabf); color: #000; padding: 15px 30px; border-radius: 15px; font-family: 'Orbitron', sans-serif; font-size: 1.2rem; font-weight: 700; box-shadow: 0 0 30px var(--success-glow); transition: bottom 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275); z-index: 1000; }
        #completion-badge.show { bottom: 25px; }
        #reward-button { position: absolute; top: 25px; right: 25px; font-size: 2.8em; cursor: pointer; transition: transform 0.3s ease; animation: rewardPulse 3s infinite ease-in-out; }
        .reward-popup { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0, 0, 0, 0.5); z-index: 2000; opacity: 0; visibility: hidden; transition: all 0.4s ease; display: flex; justify-content: center; align-items: center; }
        .reward-popup.show { opacity: 1; visibility: visible; backdrop-filter: blur(10px); }
        .reward-form { background: var(--dark-gradient); padding: 35px; border-radius: 20px; border: 1px solid var(--reward-glow); box-shadow: 0 0 40px rgba(255, 215, 0, 0.3); text-align: center; width: 90%; max-width: 380px; transform: scale(0.95); transition: all 0.4s 0.1s cubic-bezier(0.165, 0.84, 0.44, 1); }
        .reward-popup.show .reward-form { transform: scale(1); }
        .reward-form h2 { font-family: 'Orbitron', sans-serif; color: var(--reward-glow); text-shadow: 0 0 8px var(--reward-glow); margin-bottom: 25px; }
        .reward-form input { width: 100%; padding: 14px; margin-bottom: 15px; border-radius: 10px; border: 1px solid var(--border-color); background: rgba(0, 0, 0, 0.3); color: var(--primary-text); font-size: 1.1em; }
        .reward-form button { width: 100%; padding: 15px; border: none; border-radius: 10px; background: linear-gradient(45deg, var(--reward-glow), #ffc107); color: #000; font-size: 1.2em; font-weight: 600; cursor: pointer; transition: all 0.3s ease; }
        .reward-form button:hover { transform: translateY(-3px); box-shadow: 0 5px 20px rgba(255, 215, 0, 0.4); }
        .reward-form button:disabled { background: #555; cursor: not-allowed; transform: none; box-shadow: none; }
        #reward-result { margin-top: 25px; font-size: 1.6em; font-weight: 600; min-height: 30px; }
        .reward-popup .close-btn { position: absolute; top: 15px; right: 20px; font-size: 2.2em; cursor: pointer; color: #888; transition: color 0.3s ease, transform 0.3s ease; }
        .reward-popup .close-btn:hover { color: #ff0000; transform: rotate(90deg); }
        .hidden { display: none !important; }
    </style>
</head>
<body>
    <div id="particles-js"></div>
    <div class="container">
        <div class="header">
            <div id="day-counter">DAY X</div>
            <div id="digital-clock">00:00:00 AM</div>
        </div>
        <div id="reward-button" class="hidden">🔐</div>
        <div class="timer-container">
            <div id="timer" class="hidden"></div>
            <div id="timer-stopped-message" class="hidden">⏱️ Timer Stopped</div>
            <div id="rest-day-message" class="hidden">Rest Day 💤</div>
        </div>
        <div class="mission-section" id="mission-container">
            <h2 class="mission-title">M I S S I O N</h2>
            <ul class="mission-list" id="mission-list"></ul>
        </div>
    </div>
    <div id="completion-badge">ALL MISSIONS COMPLETE 🔥</div>
    <div id="reward-popup" class="reward-popup">
        <div class="reward-form">
            <span class="close-btn" id="close-reward-popup">×</span>
            <h2>🔐 REWARD UNLOCKED</h2>
            <input type="number" id="quiz-total" placeholder="Total Quizzes Attempted" min="1">
            <input type="number" id="quiz-solved" placeholder="Correctly Solved" min="0">
            <button id="calculate-reward-btn">Claim Reward</button>
            <p id="reward-result"></p>
        </div>
    </div>
    <script src="https://cdn.jsdelivr.net/npm/particles.js@2.0.0/particles.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.9.3/dist/confetti.browser.min.js"></script>
    <script>
        // JavaScript poora wahi hai. Ismein koi badlav nahi.
        document.addEventListener('DOMContentLoaded', () => {
            const dayCounterEl=document.getElementById('day-counter'),digitalClockEl=document.getElementById('digital-clock'),timerEl=document.getElementById('timer'),timerStoppedEl=document.getElementById('timer-stopped-message'),restDayMessageEl=document.getElementById('rest-day-message'),missionContainerEl=document.getElementById('mission-container'),missionListEl=document.getElementById('mission-list'),completionBadgeEl=document.getElementById('completion-badge'),rewardButtonEl=document.getElementById('reward-button'),rewardPopupEl=document.getElementById('reward-popup'),closeRewardPopupEl=document.getElementById('close-reward-popup'),calculateRewardBtn=document.getElementById('calculate-reward-btn'),rewardResultEl=document.getElementById('reward-result'),quizTotalInput=document.getElementById('quiz-total'),quizSolvedInput=document.getElementById('quiz-solved');const sounds={complete:new Audio('https://cdn.pixabay.com/audio/2022/03/15/audio_732f22b373.mp3'),fanfare:new Audio('https://cdn.pixabay.com/audio/2022/11/17/audio_81d044062c.mp3'),unlock:new Audio('https://cdn.pixabay.com/audio/2021/08/04/audio_51a299c9b3.mp3'),coin:new Audio('https://cdn.pixabay.com/audio/2022/03/10/audio_c89b3f48af.mp3')};Object.values(sounds).forEach(e=>{e.volume=.5});let state={startDate:null,currentDay:1,completedTasks:{}};const TASKS_SET_A=["5AM – GET READY","MATH – (L-1)","ONE SHOT PHYSICS","ENJOY MUSIC FOR DEEP VOICE","ENGLISH – (L-1)","ONE SHOT REVISION","7PM – REMEMBER + SOLVE QUESTION"],TASKS_SET_B=["5AM – GET READY","MATH – (L-1)","ONE SHOT CHEMISTRY","ENJOY MUSIC FOR DEEP VOICE","ENGLISH – (L-1)","ONE SHOT REVISION","7PM – REMEMBER + SOLVE QUESTION"];function loadState(){const e=localStorage.getItem('soloMissionState');e?state=JSON.parse(e):(state.startDate=(new Date).toISOString().split('T')[0],saveState())}function saveState(){localStorage.setItem('soloMissionState',JSON.stringify(state))}function getTodayString(){return(new Date).toISOString().split('T')[0]}function updateDayCounter(){const e=new Date(state.startDate),t=new Date,a=Math.abs(t-e),n=Math.floor(a/864e5);state.currentDay=n+1,state.currentDay>80&&(state.currentDay=80),dayCounterEl.textContent=`DAY ${state.currentDay}`,state.completedTasks[getTodayString()]||(state.completedTasks[getTodayString()]=[],saveState())}function updateDigitalClock(){const e=new Date;digitalClockEl.textContent=e.toLocaleTimeString('en-US',{hour:'2-digit',minute:'2-digit',second:'2-digit',hour12:!0})}function handleTimerAndUI(){const e=new Date,t=state.currentDay%4==0;[timerEl,timerStoppedEl,restDayMessageEl,missionContainerEl,rewardButtonEl].forEach(e=>{e.classList.add('hidden')}),t?(restDayMessageEl.classList.remove('hidden'),rewardButtonEl.classList.remove('hidden')):(missionContainerEl.classList.remove('hidden'),e.getHours()>=5&&e.getHours()<22?(timerEl.classList.remove('hidden'),updateActiveTimer()):timerStoppedEl.classList.remove('hidden'))}function updateActiveTimer(){const e=new Date,t=new Date;t.setHours(22,0,0,0);const a=t-e;if(a<0)return void handleTimerAndUI();const n=Math.floor(a/36e5).toString().padStart(2,'0'),o=Math.floor(a/1e3/60%60).toString().padStart(2,'0'),d=Math.floor(a/1e3%60).toString().padStart(2,'0');timerEl.textContent=`⏱️ ${n}:${o}:${d} remaining`}function renderMissions(){missionListEl.innerHTML='';const e=Math.floor((state.currentDay-1)/4)%2==0?TASKS_SET_A:TASKS_SET_B,t=getTodayString(),a=state.completedTasks[t]||[];e.forEach(n=>{const o=document.createElement('li');o.classList.add('mission-item');const d=document.createElement('span');d.classList.add('task-text'),d.textContent=n,o.appendChild(d),o.dataset.task=n,a.includes(n)&&o.classList.add('completed'),o.addEventListener('click',()=>toggleTask(o,n,e)),missionListEl.appendChild(o)}),checkAllMissionsComplete(e)}function toggleTask(e,t,a){sounds.complete.currentTime=0,sounds.complete.play().catch(e=>{});const n=e.classList.toggle('completed'),o=getTodayString(),d=new Set(state.completedTasks[o]||[]);n?d.add(t):d.delete(t),state.completedTasks[o]=[...d],saveState(),checkAllMissionsComplete(a)}function checkAllMissionsComplete(e){const t=getTodayString(),a=(state.completedTasks[t]||[]).length;a===e.length&&e.length>0?(completionBadgeEl.classList.add('show'),document.body.dataset.confettiFired||(sounds.fanfare.play().catch(e=>{}),confetti({particleCount:200,spread:100,origin:{y:.6},colors:['#00ddff','#ff33ff','#ffffff']}),document.body.dataset.confettiFired="true")):(completionBadgeEl.classList.remove('show'),document.body.dataset.confettiFired="")}function handleRewardCalculation(){const e=parseInt(quizTotalInput.value),t=parseInt(quizSolvedInput.value);if(isNaN(e)||isNaN(t)||e<=0||t<0||t>e)return rewardResultEl.textContent="Invalid Numbers",void(rewardResultEl.style.color="var(--secondary-glow)");const a=Math.round(20*(t/e));sounds.coin.play().catch(e=>{}),confetti({particleCount:150,spread:70,origin:{y:.7},colors:['#ffd700','#ffc107','#ffffff']}),rewardResultEl.style.color="var(--reward-glow)",rewardResultEl.textContent=a>=15?`🎊 Earned ₹${a}! Outstanding!`:`🔥 Earned ₹${a}! Keep Pushing.`,calculateRewardBtn.disabled=!0,calculateRewardBtn.textContent="Reward Claimed"}rewardButtonEl.addEventListener('click',()=>{sounds.unlock.play().catch(e=>{}),rewardPopupEl.classList.add('show'),[quizTotalInput,quizSolvedInput].forEach(e=>{e.value=''}),rewardResultEl.textContent='',calculateRewardBtn.disabled=!1,calculateRewardBtn.textContent="Claim Reward"}),closeRewardPopupEl.addEventListener('click',()=>rewardPopupEl.classList.remove('show')),calculateRewardBtn.addEventListener('click',handleRewardCalculation);function init(){loadState(),updateDayCounter(),updateDigitalClock(),handleTimerAndUI(),renderMissions(),setInterval(()=>{updateDigitalClock(),state.currentDay%4==0||new Date.getHours()<5||new Date.getHours()>=22||updateActiveTimer()},1e3),setInterval(()=>{const e=state.currentDay;updateDayCounter(),state.currentDay!==e&&(handleTimerAndUI(),renderMissions())},6e4)}init()
        });
        particlesJS('particles-js', { "particles": { "number": { "value": 60, "density": { "enable": true, "value_area": 800 } }, "color": { "value": "#ffffff" }, "shape": { "type": "circle" }, "opacity": { "value": 0.5, "random": true, "anim": { "enable": true, "speed": 1, "opacity_min": 0, "sync": false } }, "size": { "value": 3, "random": true }, "line_linked": { "enable": false }, "move": { "enable": true, "speed": 1, "direction": "none", "random": true, "straight": false, "out_mode": "out" } }, "interactivity": { "detect_on": "canvas", "events": { "onhover": { "enable": true, "mode": "bubble" }, "resize": true }, "modes": { "bubble": { "distance": 250, "size": 0, "duration": 2, "opacity": 0 } } }, "retina_detect": true });
    </script>
</body>
</html>

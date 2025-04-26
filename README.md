# 阿水！！！
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>给阿水的</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: linear-gradient(to bottom, #ffccff, #ff99cc);
            font-family: 'Arial', sans-serif;
            overflow: hidden;
            position: relative;
        }
        
        .container {
            text-align: center;
            z-index: 10;
            background-color: rgba(255, 255, 255, 0.8);
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
            max-width: 80%;
        }
        
        h1 {
            color: #ff6699;
            margin-bottom: 30px;
        }
        
        .dialogue {
            margin: 20px 0;
            padding: 15px;
            border-radius: 10px;
            opacity: 0;
            transform: translateY(20px);
            transition: all 0.5s ease;
            position: relative;
        }
        
        .dialogue.show {
            opacity: 1;
            transform: translateY(0);
        }
        
        .jingling {
            background-color: #ffe6e6;
            border-left: 5px solid #ff6666;
        }
        
        .ashui {
            background-color: #e6f7ff;
            border-left: 5px solid #66b3ff;
            margin-left: 50px;
        }
        
        .reaction {
            font-size: 24px;
            margin-top: 20px;
            opacity: 0;
            transition: opacity 1s ease;
        }
        
        .reaction.show {
            opacity: 1;
        }
        
        .petal {
            position: absolute;
            background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="%23cc66ff"><path d="M12,2C13.1,2 14,2.9 14,4C14,5.1 13.1,6 12,6C10.9,6 10,5.1 10,4C10,2.9 10.9,2 12,2M15.5,8C16.3,8 17,8.7 17,9.5C17,10.3 16.3,11 15.5,11C14.7,11 14,10.3 14,9.5C14,8.7 14.7,8 15.5,8M8.5,8C9.3,8 10,8.7 10,9.5C10,10.3 9.3,11 8.5,11C7.7,11 7,10.3 7,9.5C7,8.7 7.7,8 8.5,8M12,11C13.1,11 14,11.9 14,13C14,14.1 13.1,15 12,15C10.9,15 10,14.1 10,13C10,11.9 10.9,11 12,11M19,17V19H5V17C5,14.8 8.1,13 12,13C15.9,13 19,14.8 19,17Z" /></svg>');
            background-size: contain;
            background-repeat: no-repeat;
            width: 30px;
            height: 30px;
            opacity: 0.7;
            z-index: 1;
            pointer-events: none;
        }
        
        .music-control {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background-color: rgba(255, 255, 255, 0.7);
            padding: 10px;
            border-radius: 50%;
            cursor: pointer;
            z-index: 100;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>❤️ 给阿水的 ❤️</h1>
        
        <div class="dialogue jingling">
            <strong>精灵：</strong> 那我勇敢一次。
        </div>
        
        <div class="dialogue ashui">
            <strong>阿水：</strong> 叫老公。
        </div>
        
        <div class="dialogue jingling">
            <strong>精灵：</strong> 那不行！！！
        </div>
        
        <div class="reaction">😂😂😂</div>
    </div>
    
    <div class="music-control">🎵</div>
    
    <audio id="bgMusic" loop>
        <!-- 这里需要替换为《爱的魔法》音乐文件 -->
        <source src="https://music.163.com/song/media/outer/url?id=287035.mp3" type="audio/mpeg">
        您的浏览器不支持音频元素。
    </audio>
    
    <script>
        // 创建花瓣
        function createPetals() {
            const petalCount = 20;
            for (let i = 0; i < petalCount; i++) {
                const petal = document.createElement('div');
                petal.className = 'petal';
                
                // 随机位置
                petal.style.left = Math.random() * 100 + 'vw';
                petal.style.top = -30 + 'px';
                
                // 随机大小
                const size = Math.random() * 15 + 15;
                petal.style.width = size + 'px';
                petal.style.height = size + 'px';
                
                // 随机旋转
                petal.style.transform = `rotate(${Math.random() * 360}deg)`;
                
                // 随机动画持续时间
                const duration = Math.random() * 10 + 10;
                
                // 随机下落路径
                const animation = petal.animate([
                    { transform: `translate(${Math.random() * 100 - 50}px, 0) rotate(0deg)`, top: '-30px' },
                    { transform: `translate(${Math.random() * 100 - 50}px, 0) rotate(360deg)`, top: '100vh' }
                ], {
                    duration: duration * 1000,
                    iterations: Infinity
                });
                
                document.body.appendChild(petal);
            }
        }
        
        // 显示对话
        function showDialogues() {
            const dialogues = document.querySelectorAll('.dialogue');
            const reaction = document.querySelector('.reaction');
            
            dialogues.forEach((dialogue, index) => {
                setTimeout(() => {
                    dialogue.classList.add('show');
                }, (index + 1) * 1500);
            });
            
            setTimeout(() => {
                reaction.classList.add('show');
            }, dialogues.length * 1500 + 1000);
        }
        
        // 音乐控制
        const musicControl = document.querySelector('.music-control');
        const bgMusic = document.getElementById('bgMusic');
        
        musicControl.addEventListener('click', () => {
            if (bgMusic.paused) {
                bgMusic.play();
                musicControl.textContent = '🔊';
            } else {
                bgMusic.pause();
                musicControl.textContent = '🎵';
            }
        });
        
        // 初始化
        window.onload = function() {
            createPetals();
            showDialogues();
            
            // 尝试自动播放音乐（注意：许多浏览器会阻止自动播放）
            const playPromise = bgMusic.play();
            
            if (playPromise !== undefined) {
                playPromise.catch(error => {
                    musicControl.textContent = '🎵';
                });
            }
        };
    </script>
</body>
</html>

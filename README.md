<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Аниме Математика ✧</title>
    <style>
        :root {
            --main-color: #ff9ff3;
            --secondary-color: #feca57;
            --accent-color: #5f27cd;
            --text-color: #2d3436;
            --light-bg: #f7f1e3;
            --card-bg: #ffffff;
            --correct-color: #1dd1a1;
            --wrong-color: #ff6b6b;
        }
        
        body {
            font-family: 'Comic Sans MS', 'M PLUS Rounded 1c', cursive;
            background-color: var(--light-bg);
            background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100" viewBox="0 0 100 100"><circle cx="20" cy="20" r="3" fill="%23ff9ff3" opacity="0.5"/><circle cx="50" cy="50" r="4" fill="%23feca57" opacity="0.5"/><circle cx="80" cy="30" r="3" fill="%235f27cd" opacity="0.5"/></svg>');
            color: var(--text-color);
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
            line-height: 1.6;
        }
        
        h1 {
            color: var(--accent-color);
            text-align: center;
            font-size: 2.5rem;
            margin-bottom: 30px;
            text-shadow: 3px 3px 0px rgba(95, 39, 205, 0.1);
            position: relative;
        }
        
        h1:after {
            content: "";
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 150px;
            height: 4px;
            background: linear-gradient(90deg, var(--main-color), var(--secondary-color));
            border-radius: 2px;
        }
        
        .controls {
            background-color: var(--card-bg);
            padding: 25px;
            border-radius: 15px;
            margin-bottom: 30px;
            box-shadow: 0 8px 15px rgba(0,0,0,0.1);
            border: 2px solid var(--main-color);
        }
        
        .difficulty-selector {
            margin-bottom: 25px;
        }
        
        label {
            display: block;
            margin-bottom: 10px;
            font-weight: bold;
            color: var(--accent-color);
            font-size: 1.1rem;
        }
        
        select, input {
            width: 100%;
            padding: 12px 15px;
            border: 2px solid var(--main-color);
            border-radius: 10px;
            font-size: 16px;
            font-family: inherit;
            margin-bottom: 15px;
        }
        
        .buttons {
            display: flex;
            gap: 15px;
            flex-wrap: wrap;
        }
        
        button {
            flex: 1;
            min-width: 150px;
            background-color: var(--main-color);
            color: white;
            border: none;
            padding: 14px 20px;
            border-radius: 10px;
            cursor: pointer;
            font-size: 18px;
            font-weight: bold;
            transition: all 0.3s ease;
            font-family: inherit;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }
        
        button:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 12px rgba(0,0,0,0.15);
        }
        
        #check-btn {
            background-color: var(--accent-color);
        }
        
        #generate-btn {
            background-color: var(--secondary-color);
        }
        
        .problem-container {
            background-color: var(--card-bg);
            padding: 30px;
            border-radius: 15px;
            margin-bottom: 25px;
            box-shadow: 0 8px 15px rgba(0,0,0,0.1);
            border: 2px solid var(--secondary-color);
            position: relative;
        }
        
        .problem {
            font-size: 22px;
            margin-bottom: 20px;
            color: var(--text-color);
            font-weight: bold;
        }
        
        .answer-input {
            margin: 20px 0;
        }
        
        .result {
            padding: 15px;
            margin-top: 15px;
            border-radius: 10px;
            font-weight: bold;
            display: none;
            animation: fadeIn 0.5s ease;
        }
        
        .correct {
            background-color: rgba(29, 209, 161, 0.2);
            border-left: 4px solid var(--correct-color);
            color: var(--correct-color);
            display: block;
        }
        
        .incorrect {
            background-color: rgba(255, 107, 107, 0.2);
            border-left: 4px solid var(--wrong-color);
            color: var(--wrong-color);
            display: block;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .footer {
            text-align: center;
            margin-top: 40px;
            color: var(--text-color);
            font-size: 14px;
            opacity: 0.7;
        }
        
        .anime-char {
            text-align: center;
            font-size: 60px;
            margin: 20px 0;
            animation: bounce 2s infinite;
        }
        
        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-15px); }
        }
        
        @media (max-width: 600px) {
            body {
                padding: 15px;
            }
            
            h1 {
                font-size: 1.8rem;
            }
            
            button {
                min-width: 100%;
            }
        }
    </style>
</head>
<body>
    <div class="anime-char">✧(^◡^)✧</div>
    <h1>Аниме Математика</h1>
    
    <div class="controls">
        <div class="difficulty-selector">
            <label for="difficulty">Уровень сложности:</label>
            <select id="difficulty">
                <option value="easy">Легкий (арифметика)</option>
                <option value="medium">Средний (уравнения)</option>
                <option value="hard">Сложный (тригонометрия)</option>
                <option value="expert">Экспертный (матрицы)</option>
                <option value="extreme">Экстремальный (высшая)</option>
            </select>
        </div>
        <div class="buttons">
            <button id="generate-btn">Новая задача ✨</button>
        </div>
    </div>
    
    <div id="problem-area">
        <div class="problem-container">
            <p>Нажмите "Новая задача" чтобы начать!</p>
        </div>
    </div>

    <div class="footer">
        Аниме математический тренажер • Проверь свои навыки!
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const difficultySelect = document.getElementById('difficulty');
            const generateBtn = document.getElementById('generate-btn');
            const problemArea = document.getElementById('problem-area');
            
            let currentCorrectAnswer = null;
            
            function randomInt(min, max) {
                return Math.floor(Math.random() * (max - min + 1)) + min;
            }
            
            function generateEasyProblem() {
                const operations = [
                    { symbol: '+', apply: (a, b) => a + b },
                    { symbol: '-', apply: (a, b) => a - b },
                    { symbol: '×', apply: (a, b) => a * b },
                    { symbol: '÷', apply: (a, b) => a / b }
                ];
                
                const opIndex = randomInt(0, 3);
                const operation = operations[opIndex];
                
                let a, b;
                if (opIndex === 3) {
                    b = randomInt(1, 12);
                    a = b * randomInt(1, 12);
                } else {
                    a = randomInt(1, 25);
                    b = randomInt(1, 25);
                }
                
                const result = operation.apply(a, b);
                currentCorrectAnswer = Number.isInteger(result) ? result : parseFloat(result.toFixed(2));
                
                return {
                    problem: `Вычислите: ${a} ${operation.symbol} ${b}`,
                    answer: result
                };
            }
            
            function generateMediumProblem() {
                const types = ['linear', 'quadratic', 'system', 'fraction', 'percent'];
                const type = types[randomInt(0, types.length - 1)];
                
                switch(type) {
                    case 'linear':
                        const x = randomInt(-10, 10);
                        const a = randomInt(1, 5);
                        const b = a * x + randomInt(-5, 5);
                        currentCorrectAnswer = x;
                        
                        return {
                            problem: `Решите уравнение: ${a}x + ${b - a * x} = ${b}`,
                            answer: x
                        };
                        
                    case 'quadratic':
                        const x1 = randomInt(-5, 5);
                        let x2 = randomInt(-5, 5);
                        while (x2 === x1) x2 = randomInt(-5, 5);
                        
                        const aq = randomInt(1, 3);
                        const bq = -aq * (x1 + x2);
                        const cq = aq * x1 * x2;
                        currentCorrectAnswer = [x1, x2].sort();
                        
                        return {
                            problem: `Решите квадратное уравнение: ${aq}x² ${bq >= 0 ? '+' : '-'} ${Math.abs(bq)}x ${cq >= 0 ? '+' : '-'} ${Math.abs(cq)} = 0`,
                            answer: [x1, x2].sort()
                        };
                        
                    case 'percent':
                        const percent = randomInt(5, 95);
                        const number = randomInt(10, 200);
                        currentCorrectAnswer = (number * percent / 100).toFixed(2);
                        
                        return {
                            problem: `Найдите ${percent}% от числа ${number}`,
                            answer: parseFloat((number * percent / 100).toFixed(2))
                        };
                        
                    default:
                        return generateEasyProblem();
                }
            }
            
            function generateHardProblem() {
                const types = ['trigonometry', 'logarithm', 'derivative'];
                const type = types[randomInt(0, types.length - 1)];
                
                switch(type) {
                    case 'trigonometry':
                        let angle = randomInt(0, 360);
                        const trigFuncs = ['sin', 'cos', 'tan'];
                        const trigFunc = trigFuncs[randomInt(0, 2)];
                        
                        if (trigFunc === 'tan') {
                            while (angle % 90 === 0 && angle % 180 !== 0) {
                                angle = randomInt(0, 360);
                            }
                        }
                        
                        const radians = angle * Math.PI / 180;
                        currentCorrectAnswer = parseFloat(Math[trigFunc](radians).toFixed(4));
                        
                        return {
                            problem: `Вычислите ${trigFunc}(${angle}°)`,
                            answer: parseFloat(Math[trigFunc](radians).toFixed(4))
                        };
                        
                    default:
                        return generateMediumProblem();
                }
            }
            
            function generateExpertProblem() {
                const types = ['complex', 'matrix'];
                const type = types[randomInt(0, types.length - 1)];
                
                switch(type) {
                    case 'matrix':
                        const a11 = randomInt(-3, 3);
                        const a12 = randomInt(-3, 3);
                        const a21 = randomInt(-3, 3);
                        const a22 = randomInt(-3, 3);
                        currentCorrectAnswer = a11 * a22 - a12 * a21;
                        
                        return {
                            problem: `Найдите определитель матрицы:<br>
                                     | ${a11} ${a12} |<br>
                                     | ${a21} ${a22} |`,
                            answer: a11 * a22 - a12 * a21
                        };
                        
                    default:
                        return generateHardProblem();
                }
            }
            
            function generateExtremeProblem() {
                const num = randomInt(10, 100);
                let isPrime = true;
                for (let i = 2; i <= Math.sqrt(num); i++) {
                    if (num % i === 0) {
                        isPrime = false;
                        break;
                    }
                }
                currentCorrectAnswer = isPrime;
                
                return {
                    problem: `Является ли число ${num} простым? (Ответ: да/нет)`,
                    answer: isPrime
                };
            }
            
            function checkAnswer(userAnswer) {
                if (currentCorrectAnswer === null) return false;
                
                if (Array.isArray(currentCorrectAnswer)) {
                    // Для задач с несколькими ответами (например, квадратные уравнения)
                    const userAnswers = userAnswer.split(',').map(x => parseFloat(x.trim()));
                    if (userAnswers.length !== currentCorrectAnswer.length) return false;
                    
                    return userAnswers.every((val, idx) => 
                        Math.abs(val - currentCorrectAnswer[idx]) < 0.001
                    );
                } else if (typeof currentCorrectAnswer === 'boolean') {
                    // Для задач с да/нет
                    const normalizedAnswer = userAnswer.toLowerCase().trim();
                    return (normalizedAnswer === 'да' && currentCorrectAnswer) || 
                           (normalizedAnswer === 'нет' && !currentCorrectAnswer);
                } else {
                    // Для числовых ответов
                    const userNum = parseFloat(userAnswer);
                    return !isNaN(userNum) && 
                           Math.abs(userNum - currentCorrectAnswer) < 0.001;
                }
            }
            
            function generateNewProblem() {
                const difficulty = difficultySelect.value;
                let problemData;
                
                switch(difficulty) {
                    case 'easy': problemData = generateEasyProblem(); break;
                    case 'medium': problemData = generateMediumProblem(); break;
                    case 'hard': problemData = generateHardProblem(); break;
                    case 'expert': problemData = generateExpertProblem(); break;
                    case 'extreme': problemData = generateExtremeProblem(); break;
                    default: problemData = generateEasyProblem();
                }
                
                problemArea.innerHTML = `
                    <div class="problem-container">
                        <div class="problem">${problemData.problem}</div>
                        <div class="answer-input">
                            <label for="user-answer">Ваш ответ:</label>
                            <input type="text" id="user-answer" placeholder="Введите ответ...">
                        </div>
                        <button id="check-btn">Проверить ответ</button>
                        <div id="result" class="result"></div>
                    </div>
                `;
                
                document.getElementById('check-btn').addEventListener('click', function() {
                    const userAnswer = document.getElementById('user-answer').value;
                    const resultDiv = document.getElementById('result');
                    
                    if (checkAnswer(userAnswer)) {
                        resultDiv.className = 'result correct';
                        resultDiv.innerHTML = 'Правильно! ✧(≧◡≦)✧';
                    } else {
                        resultDiv.className = 'result incorrect';
                        let correctAnswer = currentCorrectAnswer;
                        
                        if (Array.isArray(correctAnswer)) {
                            correctAnswer = correctAnswer.join(', ');
                        } else if (typeof correctAnswer === 'boolean') {
                            correctAnswer = correctAnswer ? 'да' : 'нет';
                        }
                        
                        resultDiv.innerHTML = `Неправильно (╥﹏╥)<br>Правильный ответ: ${correctAnswer}`;
                    }
                });
            }
            
            generateBtn.addEventListener('click', generateNewProblem);
        });
    </script>
</body>
</html>
<div class="social-links" style="
    display: flex;
    justify-content: center;
    gap: 20px;
    margin: 30px 0;
">
    <!-- Иконка VK -->
    <a href="https://vk.com/15gg15gg15" target="_blank" class="social-icon" style="
        display: inline-block;
        width: 60px;
        height: 60px;
        border-radius: 50%;
        background: linear-gradient(135deg, #4c75a3, #3a5f89);
        color: white;
        text-align: center;
        line-height: 60px;
        font-size: 30px;
        transition: all 0.3s ease;
        box-shadow: 0 4px 10px rgba(0,0,0,0.2);
        position: relative;
        overflow: hidden;
    ">
        <i class="fab fa-vk" style="
            display: inline-block;
            width: 100%;
            height: 100%;
        "></i>
        <span style="
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle, rgba(255,255,255,0.3) 0%, rgba(255,255,255,0) 70%);
            opacity: 0;
            transition: opacity 0.3s;
        "></span>
    </a>

    <!-- Иконка Telegram -->
    <a href="https://t.me/zigzak5643" target="_blank" class="social-icon" style="
        display: inline-block;
        width: 60px;
        height: 60px;
        border-radius: 50%;
        background: linear-gradient(135deg, #2aabee, #229ed9);
        color: white;
        text-align: center;
        line-height: 60px;
        font-size: 30px;
        transition: all 0.3s ease;
        box-shadow: 0 4px 10px rgba(0,0,0,0.2);
        position: relative;
        overflow: hidden;
    ">
        <i class="fab fa-telegram" style="
            display: inline-block;
            width: 100%;
            height: 100%;
        "></i>
        <span style="
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle, rgba(255,255,255,0.3) 0%, rgba(255,255,255,0) 70%);
            opacity: 0;
            transition: opacity 0.3s;
        "></span>
    </a>
</div>

<!-- Добавьте этот код перед закрывающим тегом </body> -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
<script>
    // Анимация при наведении
    document.querySelectorAll('.social-icon').forEach(icon => {
        icon.addEventListener('mouseenter', function() {
            this.style.transform = 'translateY(-5px)';
            this.querySelector('span').style.opacity = '1';
            this.style.boxShadow = '0 8px 15px rgba(0,0,0,0.3)';
        });
        icon.addEventListener('mouseleave', function() {
            this.style.transform = 'translateY(0)';
            this.querySelector('span').style.opacity = '0';
            this.style.boxShadow = '0 4px 10px rgba(0,0,0,0.2)';
        });
    });
</script>
<style>
  /* Стили для рекламной метки */
  .tg-ad-container {
    position: relative;
    display: inline-block;
    margin: 30px; /* Отступ для демонстрации */
  }
  
  .tg-ad-label {
    position: absolute;
    top: -151px;
    left: 685%;
    transform: translateX(-50%);
    white-space: nowrap;
    font-size: 12px;
    font-weight: bold;
    color: #ff6b6b;
    font-family: 'Comic Sans MS', cursive;
    animation: pulse 1.5s infinite;
    background: white;
    padding: 3px 8px;
    border-radius: 12px;
    box-shadow: 0 2px 8px rgba(0,0,0,0.15);
    z-index: 100;
    border: 1px solid #ffcccc;
  }
  
  /* Стрелка */
  .tg-ad-label::after {
    content: "";
    position: absolute;
    top: 100%;
    left: 50%;
    transform: translateX(-50%);
    width: 0;
    height: 0;
    border-left: 8px solid transparent;
    border-right: 8px solid transparent;
    border-top: 8px solid white;
    filter: drop-shadow(0 2px 1px rgba(255,107,107,0.3));
  }
  
  /* Анимация */
  @keyframes pulse {
    0% { transform: translateX(-50%) scale(0.95); }
    50% { transform: translateX(-50%) scale(1.05); }
    100% { transform: translateX(-50%) scale(0.95); }
  }
  
  /* Стили для иконки Telegram (если ещё не есть) */
  .telegram-icon {
    display: inline-flex;
    width: 60px;
    height: 0px;
    border-radius: 50%;
    background: linear-gradient(135deg, #2aabee, #229ed9);
    color: white;
    align-items: center;
    justify-content: center;
    font-size: 0px;
    text-decoration: none;
    box-shadow: 0 4px 12px rgba(34, 158, 217, 0.3);
    transition: all 0.3s ease;
  }
  
  .telegram-icon:hover {
    transform: translateY(-3px);
    box-shadow: 0 6px 16px rgba(34, 158, 217, 0.4);
  }
</style>

<!-- HTML-структура (добавьте в нужное место) -->
<div class="tg-ad-container">
  <a href="https://t.me/ваш_канал" class="telegram-icon">
    <i class="fab fa-telegram"></i>
  </a>
  <div class="tg-ad-label">Реклама</div>
</div>

<!-- Подключите Font Awesome если ещё не подключен -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">


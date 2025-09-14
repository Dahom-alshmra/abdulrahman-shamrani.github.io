import os

html_content = """
<!DOCTYPE html>
<html lang=\"ar\">
<head>
    <meta charset=\"UTF-8\">
    <meta name=\"viewport\" content=\"width=device-width, initial-scale=1.0\">
    <title>نحوي دحومي™</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(to right, #f0f8ff, #e6e6fa);
            color: #333;
            text-align: center;
            padding: 20px;
        }
        .welcome {
            margin-top: 30px;
        }
        .question-box {
            margin: 20px auto;
            padding: 20px;
            border: 2px solid #ccc;
            border-radius: 10px;
            width: 80%;
            background-color: #fff;
        }
        .store, .score, .stage {
            margin: 20px;
        }
        button {
            margin: 5px;
            padding: 10px 20px;
            font-size: 16px;
            border-radius: 5px;
            border: none;
            background-color: #4CAF50;
            color: white;
            cursor: pointer;
        }
        button:hover {
            background-color: #45a049;
        }
        footer {
            margin-top: 40px;
            font-size: 14px;
            color: #666;
        }
    </style>
</head>
<body>
    <div class=\"welcome\">
        <h1>مرحبًا بك في لعبة نحوي دحومي™</h1>
        <img src=\"https://via.placeholder.com/150\" alt=\"شخصية دحوم\">
        <p>هيا نتعلم النحو بطريقة ممتعة!</p>
    </div>

    <div class=\"score\">
        <h2>النقاط: <span id=\"points\">0</span></h2>
    </div>

    <div class=\"question-box\">
        <h3>السؤال 1: الجملة "ذهب الطالب إلى المدرسة" صحيحة نحويًا؟</h3>
        <button onclick=\"answer(true, 1)\">صح</button>
        <button onclick=\"answer(false, 1)\">خطأ</button>
    </div>

    <div class=\"question-box\">
        <h3>السؤال 2: اختر الكلمة الصحيحة: "الولد ___ في الحديقة"</h3>
        <button onclick=\"answer(true, 2)\">يلعب</button>
        <button onclick=\"answer(false, 2)\">يلعبون</button>
        <button onclick=\"answer(false, 2)\">تلعب</button>
    </div>

    <div class=\"store\">
        <h2>المتجر</h2>
        <button onclick=\"buy('hint', 20)\">شراء تلميح (20 نقطة)</button>
        <button onclick=\"buy('solution', 50)\">شراء حل مباشر (50 نقطة)</button>
        <button onclick=\"buy('background', 30)\">خلفية جديدة (30 نقطة)</button>
        <button onclick=\"buy('character', 40)\">شخصية جديدة (40 نقطة)</button>
    </div>

    <div class=\"stage\">
        <h2>المرحلة الحالية: المرحلة 1</h2>
        <p>تتجدد المراحل كل فترة، ترقب الجديد!</p>
    </div>

    <footer>
        <p>© جميع الحقوق محفوظة لعبدالرحمن الشمراني</p>
    </footer>

    <script>
        let points = 0;

        function answer(isCorrect, questionId) {
            if (isCorrect) {
                points += 5;
                alert('إجابة صحيحة! +5 نقاط');
            } else {
                alert('إجابة خاطئة');
            }
            document.getElementById('points').innerText = points;
        }

        function buy(item, cost) {
            if (points >= cost) {
                points -= cost;
                alert('تم شراء ' + item + '! -' + cost + ' نقاط');
            } else {
                alert('النقاط غير كافية');
            }
            document.getElementById('points').innerText = points;
        }
    </script>
</body>
</html>
"""

output_path = "/mnt/data/nahwi_dahomy_game.html"

try:
    with open(output_path, "w", encoding="utf-8") as f:
        f.write(html_content)
    print(f"HTML file created successfully: {output_path}")
except Exception as e:
    print(f"Error creating HTML file: {e}")

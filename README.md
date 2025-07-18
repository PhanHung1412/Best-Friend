<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <title>Bạn có yêu toiii khônggg</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      background-color: #f0f1ff;
      text-align: center;
      transition: all 0.3s ease;
      overflow: hidden;
    }

    .question {
      font-size: 24px;
      margin-bottom: 30px;
      max-width: 90%;
    }

    #yesButton {
      font-size: 24px;
      padding: 15px 40px;
      background-color: #ff5c77;
      color: white;
      border: none;
      border-radius: 12px;
      transition: all 0.3s ease;
      z-index: 1;
    }

    #noButton {
      font-size: 18px;
      padding: 10px 30px;
      background-color: #007bff;
      color: white;
      border: none;
      border-radius: 10px;
      cursor: pointer;
      margin-top: 20px;
      transition: background-color 0.3s ease;
      z-index: 1;
    }

    #overlay {
      position: absolute;
      top: 0; left: 0;
      width: 100%; height: 100%;
      background-color: rgba(255,255,255,0.8);
      display: none;
      align-items: center;
      justify-content: center;
      font-size: 28px;
      font-weight: bold;
      color: #ff4081;
    }
  </style>
</head>
<body>

  <div class="question" id="mainQuestion">Em có yêu anh không?</div>
  <button id="yesButton">Có</button>
  <button id="noButton">Không</button>

  <div id="overlay">
    <p>🥰 Anh biết mà! Anh cũng yêu em lắm đó 🫶</p>
    </div>

  <script>
    const yesBtn = document.getElementById('yesButton');
    const noBtn = document.getElementById('noButton');
    const question = document.getElementById('mainQuestion');
    const overlay = document.getElementById('overlay');

    let clickCount = 0;
    let fontSize = 24;

    const messages = [
      "Tôi hỏi bạn lại lần nữa, bạn có yêu tôi không?",
      "Bạn không thích tôi à?",
      "Bạn có hối hận không?",
      "Không yêu tui buồn đó 🥺 Nói yêu lẹ đi!!!"
    ];

    const buttonTexts = [
      "Không",
      "Không",
      "Không",
      "Không",
    ];

    noBtn.addEventListener('click', () => {
      if (clickCount < 5) {
        fontSize += 40; // Tăng size mỗi lần
        yesBtn.style.fontSize = fontSize + 'px';
        yesBtn.style.padding = (20 + clickCount * 10) + 'px ' + (60 + clickCount * 20) + 'px';

        // Cập nhật nội dung
        question.innerText = messages[clickCount];
        noBtn.innerText = buttonTexts[clickCount];

        clickCount++;

        // Khi đạt 5 lần
        if (clickCount === 5) {
          yesBtn.style.fontSize = "100px";
          yesBtn.style.padding = "100px 200px";
          noBtn.disabled = true;
          overlay.style.display = "flex";
        }
      }
    });
    // buston "yes"
    yesBtn.addEventListener('click', () => {
      // Ẩn mọi phần tử chính
      question.style.display = 'none';
      yesBtn.style.display = 'none';
      noBtn.style.display = 'none';

      // Hiện overlay
      overlay.style.display = 'flex';
    });
  </script>

</body>
</html>

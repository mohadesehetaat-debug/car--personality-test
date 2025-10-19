<!DOCTYPE html>
<html>
<head>
  <title>تست شخصیت رانندگی</title>
  <meta charset="UTF-8">
  <style>
    body { font-family: sans-serif; direction: rtl; padding: 20px; background-color: #f7f7f7; }
    .question { margin-bottom: 20px; background: #fff; padding: 15px; border-radius: 8px; box-shadow: 0 0 5px #ccc; }
    button { padding: 10px 20px; font-size: 16px; cursor: pointer; }
    img { margin-top: 10px; border-radius: 8px; max-width: 100%; }
  </style>
</head>
<body>

<h2>تست شخصیت رانندگی</h2>
<div id="quiz"></div>
<button onclick="showResult()">نمایش نتیجه</button>
<h3 id="result"></h3>

<script>
// سوال‌ها و گزینه‌ها
const questions = [
  { q: "وقتی پشت فرمون می‌شینی، بیشتر دنبال چی هستی؟", options: ["هیجانی", "آرام", "لوکس", "اقتصادی"] },
  { q: "سبک رانندگی‌ات چطوریه؟", options: ["هیجانی", "آرام", "لوکس", "اقتصادی"] },
  { q: "ماشینت چه ویژگی‌هایی داشته باشه؟", options: ["هیجانی", "آرام", "لوکس", "اقتصادی"] },
  { q: "در سفرهای جاده‌ای، تو معمولاً...", options: ["هیجانی", "آرام", "لوکس", "اقتصادی"] },
  { q: "وقتی ماشینت خراب می‌شه، چه واکنشی داری؟", options: ["هیجانی", "آرام", "لوکس", "اقتصادی"] },
  { q: "ماشین ایده‌آلت چه رنگیه؟", options: ["هیجانی", "آرام", "لوکس", "اقتصادی"] },
  { q: "ماشینت شبیه کدوم شخصیت معروفه؟", options: ["هیجانی", "آرام", "لوکس", "اقتصادی"] }
];

// ماشین پیشنهادی برای هر شخصیت
const car = {
  هیجانی: "Ford Mustang GT یا BMW M3",
  آرام: "Volkswagen Sedan سفید",
  لوکس: "Mercedes-Benz E-Class یا Lexus RX",
  اقتصادی: "Kia Picanto یا Toyota Yaris Hybrid"
};

// تصویر پیشنهادی برای هر شخصیت
const images = {
  هیجانی: "https://images.unsplash.com/photo-1606813909355-8f6e4e2b1c1e",
  آرام: "https://github.com/mohadesehetaat-debug/car--personality-test/blob/main/WhatsApp%20Image%202025-10-19%20at%2011.50.03.jpeg", // 👈 لینک تصویر فولکس‌واگن سفید
  لوکس: "https://images.unsplash.com/photo-1617531653456-4b6e4e2b1c1e",
  اقتصادی: "https://images.unsplash.com/photo-1597004025555-7f6e4e2b1c1e"
};

// ساخت فرم تست
const quizDiv = document.getElementById("quiz");
questions.forEach((item, index) => {
  let html = <div class="question"><p>${index + 1}. ${item.q}</p>;
  item.options.forEach(opt => {
    html += <label><input type="radio" name="q${index}" value="${opt}"> ${opt}</label><br>;
  });
  html += </div>;
  quizDiv.innerHTML += html;
});

// تحلیل نتیجه و نمایش ماشین + تصویر
function showResult() {
  let counts = { هیجانی: 0, آرام: 0, لوکس: 0, اقتصادی: 0 };
  for (let i = 0; i < questions.length; i++) {
    let val = document.querySelector(input[name="q${i}"]:checked)?.value;
    if (!val) {
      document.getElementById("result").innerText = "لطفاً به همه سوال‌ها پاسخ بده.";
      return;
    }
    counts[val]++;
  }

  let personality = Object.keys(counts).reduce((a, b) => counts[a] > counts[b] ? a : b);

  document.getElementById("result").innerHTML = `
    شخصیت رانندگی شما: <strong>${personality}</strong><br>
    ماشین مناسب شما: ${car[personality]}<br>
    <img src="${images[personality]}" alt="ماشین پیشنهادی">
  `;
}
</script>

</body>
</html>



<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Jam Digital</title>
    <style>
      #clock {
  font-size: 3rem;
  text-align: center;
  margin: 2rem;
}

#calendar {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 2rem;
}

#month {
  font-size: 2rem;
  font-weight: bold;
  margin-bottom: 1rem;
}

#days {
  display: grid;
  grid-template-columns: repeat(7, 1fr);
  gap: 0.5rem;
}

#days div {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 3rem;
  height: 3rem;
  border-radius: 50%;
  cursor: pointer;
}

.prev-date,
.next-date {
  color: #a9a9a9;
}

    </style>
  </head>
  <body>
    <!-- Jam Digital -->
<div id="clock"></div>

<!-- Kalender -->
<div id="calendar">
  <div id="month"></div>
  <div id="days"></div>
</div>
    <script>
      // Fungsi untuk menampilkan waktu
function showTime() {
  const date = new Date();
  let hour = date.getHours();
  let min = date.getMinutes();
  let sec = date.getSeconds();

  hour = hour < 10 ? "0" + hour : hour;
  min = min < 10 ? "0" + min : min;
  sec = sec < 10 ? "0" + sec : sec;

  const time = `${hour}:${min}:${sec}`;
  document.getElementById("clock").innerText = time;

  setTimeout(showTime, 1000);
}

// Fungsi untuk menampilkan kalender
function showCalendar() {
  const date = new Date();
  const month = date.getMonth();
  const year = date.getFullYear();

  const monthsArr = [
    "Januari",
    "Februari",
    "Maret",
    "April",
    "Mei",
    "Juni",
    "Juli",
    "Agustus",
    "September",
    "Oktober",
    "November",
    "Desember",
  ];

  document.getElementById("month").innerText = monthsArr[month] + " " + year;

  const firstDay = new Date(year, month, 1).getDay();
  const lastDay = new Date(year, month + 1, 0).getDate();

  let days = "";

  for (let i = 1; i <= lastDay; i++) {
    if (i === 1) {
      for (let j = 0; j < firstDay; j++) {
        days += `<div class="prev-date"></div>`;
      }
    }

    days += `<div>${i}</div>`;

    if (i === lastDay) {
      const lastDayIndex = new Date(year, month, lastDay).getDay();
      for (let k = lastDayIndex; k < 6; k++) {
        days += `<div class="next-date"></div>`;
      }
    }
  }

  document.getElementById("days").innerHTML = days;
}

showTime();
showCalendar();
    </script>
  </body>
</html>

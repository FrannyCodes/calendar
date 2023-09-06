<!DOCTYPE html>
<html>
<head>
  <title>Simple Calendar</title>
</head>
<body>
  <div id="calendar"></div>
  <script>
    function createCalendar(year, month) {
      const daysInMonth = new Date(year, month, 0).getDate();
      const firstDayOfMonth = new Date(year, month - 1, 1).getDay();

      const calendar = document.getElementById('calendar');
      calendar.innerHTML = '';

      // Create table element
      const table = document.createElement('table');

      // Create table header with day names
      const thead = document.createElement('thead');
      const dayNames = ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'];
      const headerRow = document.createElement('tr');

      dayNames.forEach(day => {
        const th = document.createElement('th');
        th.textContent = day;
        headerRow.appendChild(th);
      });

      thead.appendChild(headerRow);
      table.appendChild(thead);

      // Create table body with days
      const tbody = document.createElement('tbody');
      let dayCount = 1;

      for (let i = 0; i < 6; i++) {
        const row = document.createElement('tr');

        for (let j = 0; j < 7; j++) {
          const cell = document.createElement('td');

          if (i === 0 && j < firstDayOfMonth) {
            // Empty cells before the first day of the month
            cell.textContent = '';
          } else if (dayCount <= daysInMonth) {
            cell.textContent = dayCount;
            dayCount++;
          }

          row.appendChild(cell);
        }

        tbody.appendChild(row);
      }

      table.appendChild(tbody);
      calendar.appendChild(table);
    }

    // Get the current date
    const currentDate = new Date();

    // Display the calendar for the current month
    createCalendar(currentDate.getFullYear(), currentDate.getMonth() + 1);
  </script>
</body>
</html>

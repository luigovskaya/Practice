API POST /flight Новая запись в flight с пустым flightNumber

**Предусловия:**

В DB существуют таблицы: flight, airport, aircraft.

Существует минимум 2 разных записи в таблице airport.

Существует минимум 1 запись в таблице aircraft.

Авторизация Basic Auth с логином и паролем Администратора.

Вместо переменных в теле запроса используются валидные данные.

| Шаги воспроизведения | Ожидаемый результат |
| --- | --- |
| Отправить API запрос с телом:<br/>{<br/>"flightNumber": "",<br/>"departureAirportCode": {{DepAirCode}},<br/>"destinationAirportCode": {{DestAirCode}},<br/>"departureDate": {{DepDate}},<br/>"arrivalDate": {{ArrDate}},<br/>"departureTime": {{DepTime}},<br/>"arrivalTime": {{ArrTime}},<br/>"gate": {{Gate}},<br/>"status": {{Status}},<br/>"flightCharge": {{Charge}},<br/>"aircraftId": {{AircraftID}}<br/><br/>} | Ответ API:<br/>{<br/>"timestamp": <CURRENT_TIME>,<br/>"status": "400 BAD_REQUEST - BAD, BAD REQUEST",<br/>"message": "Validation Failed",<br/>"details": ["flightNumber \| must not be blank"]<br/>} |

**Importance:** Medium

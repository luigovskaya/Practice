**Новая запись в flight с flightNumber>30 цифр**

**Предусловия:**

В DB существуют таблицы: flight, airport, aircraft.

Существует минимум 2 разных записи в таблице airport.

Существует минимум 1 запись в таблице aircraft.

Авторизация Basic Auth с логином и паролем Администратора.

Вместо переменных в теле запроса используются валидные данные.

| Шаги воспроизведения | Ожидаемый результат |
| --- | --- |
| Отправить API запрос с телом:<br/>{<br/>"flightNumber": "0123456789012345678901234567890123",<br/>"departureAirportCode": {{DepAirCode}},<br/>"destinationAirportCode": {{DestAirCode}},<br/>"departureDate": {{DepDate}},<br/>"arrivalDate": {{ArrDate}},<br/>"departureTime": {{DepTime}},<br/>"arrivalTime": {{ArrTime}},<br/>"gate": {{Gate}},<br/>"status": {{Status}},<br/>"flightCharge": {{Charge}},<br/>"aircraftId": {{AircraftID}}<br/>} | Ответ API:<br/>{<br/>"timestamp": "2025-05-11 08:56:44:803457460 +0000",<br/>"status": "400 BAD_REQUEST - BAD, BAD REQUEST",<br/>"message": "Validation Failed",<br/>"details": ["flightNumber \| flightNumber - Not longer than 30 characters please!"]<br/>} |

**Importance:** Low

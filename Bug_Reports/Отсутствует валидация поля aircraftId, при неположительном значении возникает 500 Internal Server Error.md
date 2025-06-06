**Отсутствует валидация поля aircraftId, при неположительном значении возникает 500 Internal Server Error**

**Описание:**

При создании полета через POST с отрицательным или нулевым значением aircraftId возвращает ошибку 500.

**Предусловия:**

Авторизация Basic Auth с логином и паролем Администратора.

В DB существуют таблицы: flight, airport, aircraft.

Существует минимум 2 разных записи в таблице airport.

Существует минимум 1 запись в таблице aircraft.

Открыта страница /flight/new.

**Шаги воспроизведения:**

Отправить запрос POST      
Эндпоинт: /api/v0/flights     
Тело запроса:

{      
"flightNumber": {{FlightNumber}},      
"departureAirportCode": {{DepAirCode}},      
"destinationAirportCode": {{DestAirCode}},      
"departureDate": {{DepDate}},      
"arrivalDate": {{ArrDate}},      
"departureTime": {{DepTime}},      
"arrivalTime": {{ArrTime}},      
"gate": {{Gate}},      
"status": {{Status}},      
"flightCharge": {{Charge}},      
"aircraftId": 0      
}

| Ожидаемый результат | Фактический результат |
| --- | --- |
| { <br/>"timestamp": , <br/>"status": "400 BAD_REQUEST - BAD, BAD REQUEST", <br/>"message": "Validation Failed", <br/>"details": ["aircraftId \| Shall be positive!"] <br/>} | { <br/>"timestamp": "2025-05-11 11:06:01:791640186 +0000", <br/>"status": "500 INTERNAL_SERVER_ERROR", <br/>"message": "Server Error", <br/>"details": ["Could not find aircraft Id=0"] <br/>} |

**Рекомендации:**

**API**: Добавить валидацию значения ключа aircraftId на положительные значения

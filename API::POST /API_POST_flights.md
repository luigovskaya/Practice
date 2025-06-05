#### API::POST /flights::Отсутствует валидация поля departureDate, при пустом значении возникает 500 Internal Server Error

##### Предусловия:

- Авторизация Basic Auth с логином и паролем Администратора.
  
- В DB существуют таблицы: flight, airport, aircraft.
  
- Существует минимум 2 разных записи в таблице airport.
  
- Существует минимум 1 запись в таблице aircraft.
  
- Открыта страница /flight/new
  

##### Шаги:

1 Отправить запрос POST {{BaseURL}}/api/v0/flights

{

  "flightNumber": {{FlightNumber}},

  "departureAirportCode": {{DepAirCode}},

  "destinationAirportCode": {{DestAirCode}},

  "departureDate": "",

  "arrivalDate": {{ArrDate}},

  "departureTime": {{DepTime}},

  "arrivalTime": {{ArrTime}},

  "gate": {{Gate}},

  "status": {{Status}},

  "flightCharge": {{Charge}},

  "aircraftId": {{AircraftID}}

}

| Ожидаемый результат: | Фактический результат: |
| --- | --- |
| {<br/>"timestamp": <CURRENT_TIME>,<br/>"status": "400 BAD_REQUEST - BAD, BAD REQUEST",<br/>"message": "Validation Failed", <br/>"details": ["departureDate \\| must not be blank"]<br/>} | {<br/>"timestamp": "2025-05-11 11:31:45:176707095 +0000",<br/>"status": "500 INTERNAL_SERVER_ERROR",<br/>"message": "Server Error",<br/>"details": ["Cannot invoke \"java.time.chrono.ChronoLocalDate.toEpochDay()\" because \"other\" is null"]<br/>} |

##### Рекомендации:

Добавить валидацию поля departureDate на пустое и нулевое значение.

Importance Severnity

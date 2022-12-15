# Postman_HW_2

## Задание № 1

1. Отправить запрос методом GET на URL: http://162.55.220.72:5005/first.
2. Проверить, что статус код 200.

Тест: 
```JS
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
3. Проверить, что в body приходит правильный string.

Тест: 
```JS
pm.test("Body matches string", function () {
    pm.expect(pm.response.text()).to.include("This is the first responce from server!ss");
});
```
## Задание № 2
1. Отправить запрос  методом POST на URL: http://162.55.220.72:5005/user_info_3.

Параметры во вкладке "form-data"

| KEY   | VALUE |
| ----  | -----:|
| name  | Ilya |
| age   | 29 |
| salary| 4000 |

2. Статус код 200

Тест:
```JS
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
3. Спарсить response body в json.

Тест:
```JS
let jsonData = pm.response.json();
```
4. Проверить, что name в ответе равно name s request (name вбить руками)

Тест:
```JS
pm.test("name в ответе равно name s request", function () {
    pm.expect(jsonData.name).to.eql("Ilya");
});
```
5. Проверить, что age в ответе равно age s request (age вбить руками.)

Тест:
```JS
pm.test("age в ответе равно age s request", function () {
    pm.expect(jsonData.age).to.eql("29");
});
```
6. Проверить, что salary в ответе равно salary s request (salary вбить руками.)
Тест:
```JS
pm.test("salary в ответе равно salary s request", function () {
    pm.expect(jsonData.salary).to.eql(4000);
});
```
7. Спарсить request.
Тест:
```JS
let req = request.data 
```
* Создадим переменные req_name, req_age, req_salary, resp_salary_1_5
```JS
let req_name = req.name 
let req_age = req.age  
let req_salary = req.salary  
let req_salary_1_5 = req_salary * 4  
```
* Проверим типы данных в запросе и ответе
```JS
console.log("req_name = " + typeof req_name) // проверили тип переменной req_name
console.log("resp_name =  "+ typeof jsonData.name) // проверили тип переменной resp_name
console.log("req_age = " + typeof req_age) // проверили тип переменной req_age
console.log("resp_age =  "+ typeof jsonData.age) // проверили тип переменной resp_age
console.log("req_salary = " + typeof req_salary) // проверили тип переменной req_salary
console.log("resp_salary =  " + typeof jsonData.salary) // проверили тип переменной resp_salary
```

8. Проверить, что name в ответе равно name s request (name забрать из request.)
Тест:
```JS
pm.test("name в ответе равно name s request", function () {
    pm.expect(jsonData.name).to.eql(req_name);
});
```
9. Проверить, что age в ответе равно age s request (age забрать из request.)
Тест:
```JS
pm.test("age в ответе равно age s request", function () {
    pm.expect(jsonData.age).to.eql(req_age);
});
```
10. Проверить, что salary в ответе равно salary s request (salary забрать из request.)
Тест:
```JS
pm.test("salary в ответе равно salary s request", function () {
    pm.expect(jsonData.salary).to.eql(+req_salary);
});
```
11. Вывести в консоль параметр family из response.
Тест:
```JS
console.log(jsonData.family)
```
12. Проверить что u_salary_1_5_year в ответе равно salary*4 (salary забрать из request)
Тест:
```JS
pm.test("u_salary_1_5_year в ответе равно salary*4", function () {
    pm.expect(jsonData.family.u_salary_1_5_year).to.eql(req_salary_1_5);
});
```

http://162.55.220.72:5005/object_info_3
1. Отправить запрос.
2. Статус код 200
3. Спарсить response body в json.
4. Спарсить request.
5. Проверить, что name в ответе равно name s request (name забрать из request.)
6. Проверить, что age в ответе равно age s request (age забрать из request.)
7. Проверить, что salary в ответе равно salary s request (salary забрать из request.)
8. Вывести в консоль параметр family из response.
9. Проверить, что у параметра dog есть параметры name.
10. Проверить, что у параметра dog есть параметры age.
11. Проверить, что параметр name имеет значение Luky.
12. Проверить, что параметр age имеет значение 4.

http://162.55.220.72:5005/object_info_4
1. Отправить запрос.
2. Статус код 200
3. Спарсить response body в json.
4. Спарсить request.
5. Проверить, что name в ответе равно name s request (name забрать из request.)
6. Проверить, что age в ответе равно age из request (age забрать из request.)
7. Вывести в консоль параметр salary из request.
8. Вывести в консоль параметр salary из response.
9. Вывести в консоль 0-й элемент параметра salary из response.
10. Вывести в консоль 1-й элемент параметра salary параметр salary из response.
11. Вывести в консоль 2-й элемент параметра salary параметр salary из response.
12. Проверить, что 0-й элемент параметра salary равен salary из request (salary забрать из request.)
13. Проверить, что 1-й элемент параметра salary равен salary*2 из request (salary забрать из request.)
14. Проверить, что 2-й элемент параметра salary равен salary*3 из request (salary забрать из request.)
15. Создать в окружении переменную name
16. Создать в окружении переменную age
17. Создать в окружении переменную salary
18. Передать в окружение переменную name
19. Передать в окружение переменную age
20. Передать в окружение переменную salary
21. Написать цикл который выведет в консоль по порядку элементы списка из параметра salary.

http://162.55.220.72:5005/user_info_2
1. Вставить параметр salary из окружения в request
2. Вставить параметр age из окружения в age
3. Вставить параметр name из окружения в name
4. Отправить запрос.
5. Статус код 200
6. Спарсить response body в json.
7. Спарсить request.
8. Проверить, что json response имеет параметр start_qa_salary
9. Проверить, что json response имеет параметр qa_salary_after_6_months
10. Проверить, что json response имеет параметр qa_salary_after_12_months
11. Проверить, что json response имеет параметр qa_salary_after_1.5_year
12. Проверить, что json response имеет параметр qa_salary_after_3.5_years
13. Проверить, что json response имеет параметр person
14. Проверить, что параметр start_qa_salary равен salary из request (salary забрать из request.)
15. Проверить, что параметр qa_salary_after_6_months равен salary*2 из request (salary забрать из request.)
16. Проверить, что параметр qa_salary_after_12_months равен salary*2.7 из request (salary забрать из request.)
17. Проверить, что параметр qa_salary_after_1.5_year равен salary*3.3 из request (salary забрать из request.)
18. Проверить, что параметр qa_salary_after_3.5_years равен salary*3.8 из request (salary забрать из request.)
19. Проверить, что в параметре person, 1-й элемент из u_name равен salary из request (salary забрать из request.)
20. Проверить, что что параметр u_age равен age из request (age забрать из request.)
21. Проверить, что параметр u_salary_5_years равен salary*4.2 из request (salary забрать из request.)
22. ***Написать цикл который выведет в консоль по порядку элементы списка из параметра person.
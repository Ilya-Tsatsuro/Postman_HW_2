# Postman_HW_2
![](https://camo.githubusercontent.com/aaa6ea5d1e36a0c06e6de03c34f584fc825a307680ba5f030ee15eaf41e875fc/68747470733a2f2f6d6d732e627573696e657373776972652e636f6d2f6d656469612f32303139303631393030353135322f656e2f3732383530362f32332f706d2d6c6f676f2d7665727425343032782d3130302e6a7067)

## Задание № 1

1. Отправить запрос методом GET на URL: http:162.55.220.72:5005/first.
2. Проверить, что статус код 200.

Тест: 
```JavaScript
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
## Все тесты пройдены! 
![](https:github.com/Ilya-Tsatsuro/Postman_HW_2/blob/main/:first.png?raw=true)

---------

## Задание № 2
1. Отправить запрос  методом POST на URL: http:162.55.220.72:5005/user_info_3.

* Параметры во вкладке "form-data".

| KEY   | VALUE |
| ----  | -----:|
| name  | Ilya |
| age   | 29 |
| salary| 4000 |

2. Проверить, что статус код 200.

Тест:
```JS
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```

3. Спарсить response body в json.

```JS
let jsonData = pm.response.json();
```
4. Проверить, что name в ответе равно name s request (name вбить руками).

Тест:
```JS
pm.test("name в ответе равно name s request", function () {
    pm.expect(jsonData.name).to.eql("Ilya");
});
```
5. Проверить, что age в ответе равно age s request (age вбить руками).

Тест:
```JS
pm.test("age в ответе равно age s request", function () {
    pm.expect(jsonData.age).to.eql("29");
});
```
6. Проверить, что salary в ответе равно salary s request (salary вбить руками).

Тест:
```JS
pm.test("salary в ответе равно salary s request", function () {
    pm.expect(jsonData.salary).to.eql(4000);
});
```
7. Спарсить request.

```JS
let req = request.data;
```
* Создадим переменные req_name, req_age, req_salary, resp_salary_1_5.
```JS
let req_name = req.name;

let req_age = req.age;

let req_salary = req.salary;

let req_salary_1_5 = req_salary * 4;

```
* Проверим типы данных в запросе и ответе.

```JS
console.log("req_name = " + typeof req_name);  проверили тип переменной req_name.

console.log("resp_name =  "+ typeof jsonData.name);  проверили тип переменной resp_name.

console.log("req_age = " + typeof req_age);  проверили тип переменной req_age.

console.log("resp_age =  "+ typeof jsonData.age);  проверили тип переменной resp_age.

console.log("req_salary = " + typeof req_salary);  проверили тип переменной req_salary.

console.log("resp_salary =  " + typeof jsonData.salary);  проверили тип переменной resp_salary.
```

![](https:github.com/Ilya-Tsatsuro/Postman_HW_2/blob/main/typeof.png?raw=true)

8. Проверить, что name в ответе равно name s request (name забрать из request).

Тест:
```JS
pm.test("name в ответе равно name s request", function () {
    pm.expect(jsonData.name).to.eql(req_name);
});
```

9. Проверить, что age в ответе равно age s request (age забрать из request).

Тест:
```JS
pm.test("age в ответе равно age s request", function () {
    pm.expect(jsonData.age).to.eql(req_age);
});
```

10. Проверить, что salary в ответе равно salary s request (salary забрать из request).

Тест:
```JS
pm.test("salary в ответе равно salary s request", function () {
    pm.expect(jsonData.salary).to.eql(+req_salary);
});
```

11. Вывести в консоль параметр family из response.

```JS
console.log(jsonData.family);
```

![](https:github.com/Ilya-Tsatsuro/Postman_HW_2/blob/main/jsonData.family.png?raw=true)

12. Проверить что u_salary_1_5_year в ответе равно salary*4 (salary забрать из request).

Тест:
```JS
pm.test("u_salary_1_5_year в ответе равно salary*4", function () {
    pm.expect(jsonData.family.u_salary_1_5_year).to.eql(req_salary_1_5);
});
```

## Все тесты пройдены! 
![](https:github.com/Ilya-Tsatsuro/Postman_HW_2/blob/main/:user_info_3.png?raw=true)

-----------

## Задание №3

1. Отправить запрос методом GET на URL: http:162.55.220.72:5005/object_info_3.

2. Проверить, что статус код 200.

Тест: 
```JS
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
3. Спарсить response body в json.
 
```JS
let jsonData = pm.response.json();
```

4. Спарсить request.

```JS
let req = pm.request.url.query.toObject();
```
* Создадим переменные req_name, req_age, req_salary.

```JS
let req_name = req.name;

let req_age = req.age;

let req_salary = req.salary;

```

5. Проверить, что name в ответе равно name s request (name забрать из request).

Тест: 
```JS
pm.test("name в ответе равно name s request", function () {
    pm.expect(jsonData.name).to.eql(req_name);
});
```
6. Проверить, что age в ответе равно age s request (age забрать из request).

Тест: 
```JS
pm.test("age в ответе равно age s request", function () {
    pm.expect(jsonData.age).to.eql(req_age);
});
```
7. Проверить, что salary в ответе равно salary s request (salary забрать из request).

Тест: 
```JS
pm.test("salary в ответе равно salary s request", function () {
    pm.expect(jsonData.salary).to.eql(+req_salary);
});
```
8. Вывести в консоль параметр family из response.
 
```JS
console.log(jsonData.family);
```
![](https:github.com/Ilya-Tsatsuro/Postman_HW_2/blob/main/family_from_esponse.png?raw=true)

9. Проверить, что у параметра dog есть параметры name.

Тест: 
```JS
pm.test("у параметра dog есть параметры name", function () {
    pm.expect(jsonData.family.pets.dog).to.have.property("name"); 
}); 
```

10. Проверить, что у параметра dog есть параметры age.

Тест: 
```JS
pm.test("у параметра dog есть параметры age", function () {
    pm.expect(jsonData.family.pets.dog).to.have.property("age"); 
});
```

11. Проверить, что параметр name имеет значение Luky.

Тест: 
```JS
pm.test("name имеет значение Luk", function () {
    pm.expect(jsonData.family.pets.dog.name).to.eql("Luky");
});

```
12. Проверить, что параметр age имеет значение 4.

Тест: 
```JS
pm.test("параметр age имеет значение 4", function () {
    pm.expect(jsonData.family.pets.dog.age).to.eql(4);
});
```

## Все тесты пройдены!
![](https:github.com/Ilya-Tsatsuro/Postman_HW_2/blob/main/:object_info_3.png?raw=true)

------------

## Задание №4

 1. Отправить запрос методом GET на URL: http:162.55.220.72:5005/object_info_4.
 2. Проверить, что статус код 200.

 Тест:
```JavaScript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```

 3. Спарсить response body в json.
```JS
let jsonData = pm.response.json();
```

 4. Спарсить request.
 ```JS
let req = pm.request.url.query.toObject();
```

* Создадим переменные req_name, req_age, req_salary.
```JS
let req_name = req.name;

let req_age = req.age;  

let req_salary = req.salary;  
```

* Проверим типы данных в запросе и ответе.
```JS
console.log("req_name = " + typeof req_name);  проверили тип переменной req_name

console.log("resp_name = " + typeof jsonData.name);  проверили тип переменной resp_name

console.log("req_age = " + typeof req_age);  проверили тип переменной req_age

console.log("resp_age = " + typeof jsonData.age);  проверили тип переменной resp_age

console.log("req_salary = " + typeof req_salary);  проверили тип переменной req_salary

console.log("resp_salary = " + typeof jsonData.salary);  проверили тип переменной resp_salary
```

 5. Проверить, что name в ответе равно name s request (name забрать из request).

 Тест:
```JavaScript
pm.test("name в ответе равно name s requese", function () {
    pm.expect(jsonData.name).to.eql(req_name);
});
```

 6. Проверить, что age в ответе равно age из request (age забрать из request).

 Тест:
```JavaScript
pm.test("age в ответе равно age из request", function () {
    pm.expect(jsonData.age).to.eql(+req_age);
});
```

 7. Вывести в консоль параметр salary из request.
```JS
console.log("salary из request = " + req.salary);
```

 8. Вывести в консоль параметр salary из response.
```JS
console.log("salary из response = " + jsonData.salary);
```

 9. Вывести в консоль 0-й элемент параметра salary из response.
```JS
console.log("0-й элемент параметра salary из response = " + jsonData.salary[0]);
```

 10. Вывести в консоль 1-й элемент параметра salary параметр salary из response.
```JS
console.log("1-й элемент параметра salary из response = " + jsonData.salary[1]);
```

 11. Вывести в консоль 2-й элемент параметра salary параметр salary из response.
```JS
console.log("2-й элемент параметра salary из response = " + jsonData.salary[2]);
```

![](https:github.com/Ilya-Tsatsuro/Postman_HW_2/blob/main/Consol_task_4.png?raw=true)

 12. Проверить, что 0-й элемент параметра salary равен salary из request (salary забрать из request).

 Тест:
```JavaScript
pm.test("0-й элемент параметра salary равен salary из request", function () {
    pm.expect(jsonData.salary[0]).to.eql(+req_salary);
});
```

 13. Проверить, что 1-й элемент параметра salary равен salary*2 из request (salary забрать из request).

 Тест:
```JavaScript
pm.test("1-й элемент параметра salary равен salary*2", function () {
    pm.expect(+jsonData.salary[1]).to.eql(req_salary*2);
});
```

 14. Проверить, что 2-й элемент параметра salary равен salary*3 из request (salary забрать из request).

 Тест:
```JavaScript
pm.test("2-й элемент параметра salary равен salary*3", function () {
    pm.expect(+jsonData.salary[2]).to.eql(req_salary*3);
});
```

 15. Создать в окружении переменную name.
 16. Создать в окружении переменную age.
 17. Создать в окружении переменную salary.
 
![](https:github.com/Ilya-Tsatsuro/Postman_HW_2/blob/main/Environments.png?raw=true)

 18. Передать в окружение переменную name.

```JavaScript
pm.environment.set("name", req_name);

 19. Передать в окружение переменную age.
pm.environment.set("age", req_age);
```
 20. Передать в окружение переменную salary.

```JavaScript
pm.environment.set("salary", req_salary);
```

 21. Написать цикл который выведет в консоль по порядку элементы списка из параметра salary.
```JavaScript 
for (salary of jsonData.salary) console.log(salary);
```
![](https:github.com/Ilya-Tsatsuro/Postman_HW_2/blob/main/Consol_task_4.png?raw=true)

## Все тесты пройдены!
![](https:github.com/Ilya-Tsatsuro/Postman_HW_2/blob/main/:object_info_4.png?raw=true)
-------------

## Задание №5

 1. Вставить параметр salary из окружения в request.
 2. Вставить параметр age из окружения в age.
 3. Вставить параметр name из окружения в name.
 
 ![](https://github.com/Ilya-Tsatsuro/Postman_HW_2/blob/main/Environment_task_5.png?raw=true)

 4. Отправить запрос методом POST на URL:http:162.55.220.72:5005/user_info_2.

 5. Проверить, что статус код 200.

Тест:
```JavaScript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```

 6. Спарсить response body в json.

```JavaScript
let jsonData = pm.response.json();
```

 7. Спарсить request.

```JavaScript
let req = request.data;
```

 Создадим переменные req_name, req_age, req_salary.

```JavaScript
let req_name = req.name; 

let req_age = req.age;

let req_salary = req.salary; 
```

 8. Проверить, что json response имеет параметр start_qa_salary.

Тест:
```JavaScript
pm.test("json response имеет параметр start_qa_salary", function () {
    pm.expect(jsonData).to.have.property("start_qa_salary"); 
});
```

 9. Проверить, что json response имеет параметр qa_salary_after_6_months.

Тест:
```JavaScript
pm.test("json response имеет параметр qa_salary_after_6_months", function () {
    pm.expect(jsonData).to.have.property("qa_salary_after_6_months"); 
});
```

 10. Проверить, что json response имеет параметр qa_salary_after_12_months.

Тест:
```JavaScript
pm.test("json response имеет параметр qa_salary_after_12_months", function () {
    pm.expect(jsonData).to.have.property("qa_salary_after_12_months"); 
});
```

 11. Проверить, что json response имеет параметр qa_salary_after_1.5_year.

Тест:
```JavaScript
pm.test("json response имеет параметр qa_salary_after_1.5_year", function () {
    pm.expect(jsonData).to.have.property("qa_salary_after_1.5_year"); 
});
```

 12. Проверить, что json response имеет параметр qa_salary_after_3.5_years.

Тест:
```JavaScript
pm.test("json response имеет параметр qa_salary_after_3.5_years", function () {
    pm.expect(jsonData).to.have.property("qa_salary_after_3.5_years"); 
});
```

 13. Проверить, что json response имеет параметр person.

Тест:
```JavaScript
pm.test("json response имеет параметр person", function () {
    pm.expect(jsonData).to.have.property("person"); 
});
```

 14. Проверить, что параметр start_qa_salary равен salary из request (salary забрать из request).

Тест:
```JavaScript
pm.test("start_qa_salary равен salary из request", function () {
    pm.expect(jsonData.start_qa_salary).to.eql(+req_salary);
});
```

 15. Проверить, что параметр qa_salary_after_6_months равен salary*2 из request (salary забрать из request).

Тест:
```JavaScript
pm.test("qa_salary_after_6_months равен salary*2 из requestt", function () {
    pm.expect(jsonData.qa_salary_after_6_months).to.eql(+req_salary*2);
});
```

 16. Проверить, что параметр qa_salary_after_12_months равен salary*2.7 из request (salary забрать из request).

Тест:
```JavaScript
pm.test("qa_salary_after_12_months равен salary*2.7 из request", function () {
    pm.expect(jsonData.qa_salary_after_12_months).to.eql(+req_salary*2.7);
});
```

 17. Проверить, что параметр qa_salary_after_1.5_year равен salary*3.3 из request (salary забрать из request).

Тест:
```JavaScript
pm.test("qa_salary_after_1.5_year равен salary*3.3 из request", function () {
    pm.expect(jsonData["qa_salary_after_1.5_year"]).to.eql(+req_salary * 3.3);
});
```

 18. Проверить, что параметр qa_salary_after_3.5_years равен salary*3.8 из request (salary забрать из request).

Тест:
```JavaScript
pm.test("qa_salary_after_3.5_years равен salary*3.8 из request", function () {
    pm.expect(jsonData["qa_salary_after_3.5_years"]).to.eql(+req_salary * 3.8);
});
```

 19. Проверить, что в параметре person, 1-й элемент из u_name равен salary из request (salary забрать из request).

Тест:
```JavaScript
pm.test("в параметре person, 1-й элемент из u_name равен salary из request", function () {
    pm.expect(jsonData.person.u_name[1]).to.eql(+ req_salary);
});
```

 20. Проверить, что что параметр u_age равен age из request (age забрать из request).

Тест:
```JavaScript
pm.test("параметр u_age равен age из request", function () {
    pm.expect(jsonData.person.u_age).to.eql(+ req_age);
});
```

 21. Проверить, что параметр u_salary_5_years равен salary*4.2 из request (salary забрать из request).

Тест:
```JavaScript
pm.test("u_salary_5_years равен salary*4.2 из reques", function () {
    pm.expect(jsonData.person.u_salary_5_years).to.eql(+ req_salary * 4.2);
});
```

 22. ***Написать цикл который выведет в консоль по порядку элементы списка из параметра person.


```JavaScript
for (let key_value in jsonData.person) {
    console.log(key_value + ' = ' + jsonData.person[key_value])};
```
![](https://github.com/Ilya-Tsatsuro/Postman_HW_2/blob/main/Console_task_5.png?raw=true)

## Все тесты пройдены!
![](https://github.com/Ilya-Tsatsuro/Postman_HW_2/blob/main/:user_info_2.png?raw=true)

--------
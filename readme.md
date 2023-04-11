### Задача. ETL. Xml -> Json

### Необходимо

##### Написать ETL приложение, которое:

* Забирает файлы в формате XML из папки `src/main/resources/xml`
* Каждый файл парсит в доменный объект `Person` (классы этого объекта должны генерироваться автоматически)
* Проверяет каждый `Person`, принадлежит ли он компании Liga (`<company>Liga</company>`)
* Каждый `Person` компании "Liga", преобразует в доменный объект `User`
* Каждый `User` сериализует в JSON объект, сохраняет его в файл в папке `liga_users` (имя файла равно id)

> PS
>
> Необходимые зависимости и плагины включены в проект
>
> Для сериализации/десериализации json используется зависимость `<artifactId>jackson-databind</artifactId>`
>
> Пример использования:
>

```java
public class Car {

    private String color;
    private String type;
    // standard getters setters
}

public class App {
    private void toJson() {
        ObjectMapper objectMapper = new ObjectMapper();
        Car car = new Car("yellow", "renault");
        objectMapper.writeValue(new File("target/car.json"), car);
    }

    private void toJsonString() {
        ObjectMapper objectMapper = new ObjectMapper();
        Car car = new Car("yellow", "renault");
        String carAsString = objectMapper.writeValueAsString(car);
    }

    private void toObjectFromFile() {
        ObjectMapper objectMapper = new ObjectMapper();
        Car car = objectMapper.readValue(new File("src/test/resources/json_car.json"), Car.class);
    }

    private void toObjectFromString() {
        ObjectMapper objectMapper = new ObjectMapper();
        String json = "{ \"color\" : \"Black\", \"type\" : \"BMW\" }";
        Car car = objectMapper.readValue(json, Car.class);
    }
}
```
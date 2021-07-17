# Отчёт о тестировании 

## Тестирование фунциональности валидации номеров банковских карт

## В ходе тестирования были проверены валидные номера карт на функциональность валидации номера.
Тип валидных карты - Visa , MasterCard , Discover , AmericanExpress ,
JCB 

12.07.2021 - 13.07.2021 было проведено Функциональное тестирование

На тестирование затрачено: 3 часа

В результате тестирования выявлены следующие дефекты:
* Все валидные карты тип - AmericanExpress не валидируются- FAIL

![Ошибка валидации валидных банковских карт тип - AmericanExpress](https://github.com/ElenaTyutina/java/issues/1)
  

## Описание процесса тестирования

Тестирование производилось в програмном коде 

``` public class Main {
    public static void main(String[] args) {
        // TODO: подставлять номер карты нужно сюда между двойными кавычками, без пробелов
        String number = "373461041398135";
        System.out.println(String.format("Result is %s", isValidCardNumber(number) ? "OK" : "FAIL"));
    }

    public static boolean isValidCardNumber(String number) {
        if (number == null) {
            return false;
        }

        if (number.length() != 16) {
            return false;
        }

        long result = 0;
        for (int i = 0; i < number.length(); i++) {
            int digit;
            try {
                digit = Integer.parseInt(number.charAt(i) + "");
            } catch (NumberFormatException e) {
                return false;
            }

            if (i % 2 == 0) {
                digit *= 2;
                if (digit > 9) {
                    digit -= 9;
                }
            }
            result += digit;
        }

        return (result != 0) && (result % 10 == 0);
    }
}
```
Производился запуск программы с разными типами карт , номер карты менялся в 4 строке кода

В процессе тестирования использовались следующие артефакты :
* Smoke-test 

 
В качестве тестовых данных валидных карт типа - Visa , MasterCard , Discover , AmericanExpress ,
JCB AmericanExpress использовались данные https://creditcardgenerator.in/ 
 


Тестирование производилось в следующем окружении:
*  Linux x64 ОС.
*  Java 11.0.11 2021-04-20

# TelegramStreamGame
Руководство по игре TelegramStreamGame

## Введение
Ваша задача написать наиумнейшие мозги для танка.

Если появится ошибка в вашем скрипте, бот вам об этом обязательно скажет и обездвижит ваш танк.
Максимально допустимое время выполнения скрипта = 100 мс.
Скрипт выполняется каждый такт. В одной секунде 30 тактов.

## Краткая спецификация

| Наименование | Тип | Описание |
|-|-|-|
| move(speed) | Функция | Движение танка вперёд/назад |
| turn(speed) | Функция | Поворот танка вправо/влево |
| turnHead(speed) | Функция | Поворот башни танка вправо/влево |
| fire() | Функция | Выстрел |
| log(obj) | Функция | Выводит значение переменной в чат бота |
| getEnemies() | Функция | Получает массив танков противников |
| Tick | Переменная | Кол-во прошедших тиков с момента начала игры |
| Position | Переменная | Координаты танка |
| Rotation | Переменная | Угол поворота корпуса танка в градусах |
| RotationHead | Переменная | Угол поворота башни танка в градусах |

Более подробнее о функциях и переменных можно узнать разделами ниже.

## Функции

### Перемещение танка `move(speed: number)`
Танк может двигаться только вперёд или назад.

Функция принимает один параметр.
* speed - скорость

| Значение | Действие |
|-|-|
| > 0 | Движение прямо по направлению корпуса танка с указанной скоростью, но не больше допустимой |
| < 0 | Движение назад по направлению корпуса танка с указанной скоростью, но не больше допустимой |

Пример:
```js
move(1); // танк движется вперёд
move(-1); // танк движется назад
```

### Поворот копуса танка `turn(speed: number)`
Вращение танка происходит вместе с башней.

Функция принимает один параметр.
* speed - скорость

| Значение | Действие |
|-|-|
| > 0 | Движение в правую сторону относительно направления корпуса танка с указанной скоростью, но не больше допустимой |
| < 0 | Движение в левую сторону относительно направления корпуса танкас указанной скоростью, но не больше допустимой |

Пример:
```js
turn(-1); // танк будет поворачиваться в левую сторону
turn(1); // танк будет поворачиваться в правую сторону
```

### Поворот башни танка `turnHead(speed: number)`
У башни есть свой угол поворота и он никак не зависит от угла поворота корпуса танка.

Функция принимает один параметр.
* speed - скорость

| Значение | Действие |
|-|-|
| > 0 | Движение в правую сторону относительно направления корпуса танка с указанной скоростью, но не больше допустимой |
| < 0 | Движение в левую сторону относительно направления корпуса танка с указанной скоростью, но не больше допустимой |

Пример:
```js
turnHead(-1); // башня танка будет поворачиваться в левую сторону
turnHead(1); // башня танка будет поворачиваться в правую сторону
```

### Выстрел относительно башни `fire()`
Производится выстрел по направлению башни. Между выстрелами есть небольшая пауза.

У функции нет параметров.

Пример:
```js
fire(); // выстрелит по направлению башни
```

### Простое логирование `log(obj: any)`
Даёт вам возможность узнать что находится в переменной прямо в чате с ботом.
Кол-во вызовов данной функции за один такт в коде не ограничено.
Отправляет логи 1 раз в секунду.

Пример:
```js
let a = 1;
let b = 2;
let c = a + b;
log(c); // выведет в окно чата с ботом значение переменной c
```

### Получения массива противников `getEnemies(): any`
Получение массива из танков других игроков, которые сейчас находятся на поле боя.

У функции нет параметров.

Структура объекта танка выглядит следующим образом:
```js
{
    // координаты танка
    Position: {
        X: number;
        Y: number;
    };

    // угол поворота корпуса танка в градусах
    Rotation: number;

    // угол поворота башни танка в градусах
    RotationHead: number;
}
```

Пример, в котором пожно получить координаты 3-го игрока:
```js
const enemies = getEnemies();
if (enemies.length >= 2) {
    const pos = enemies[2].Position;
    // остальная логика
}
```

## Переменные
```js
// кол-во прошедших тиков с момента начала игры
Tick: number;

// координаты танка
Position: {
    X: number;
    Y: number;
};

// угол поворота корпуса танка в градусах
Rotation: number;

// угол поворота башни танка в градусах
RotationHead: number;
```

## Пример простого скрипта:
```js
move(1);
turn(1);
turnHead(-1);
fire();
```

## Заключение
Удачи! Да выйграет умнейший танк!

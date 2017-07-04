# Sea_battle_python
Python project of the "Sea battle" game, using sockets. Uni practice 2017.

Проект программы "Морской бой"

===================================

Общее описание работы

1) Игрок1 запускает у себя программу, 
она ждет подключения по сети другого пользователя.
2) Игрок2 на компёютере, соедененным по сети с комп-ом игрока1, 
запускает программу и посылает запрос на поключения.
3) В случае успешного подключения игроки получают возможность расставлять корабли на
своих полях. Расстановка происходит путем выбора корабля из радиогруппы ( 1-, 2-, 3- и 4-трубные корабли ).
Горизонтальное или вертикальное расположение контролируется кнопкой "поворот", корабль
вращается вокруг своего левого конца. Происходит контроль, 
чтобы корабль не вышел за пределы поля.
4) После расстановки программы посылвет другому игроку сигнал о том, что тот игрок готов к бою.
Когда оба игрока расставили корабли, можно начать игру.
5) Игроки поочередно или если прошлое попадание было успешным, выбирают клетку на поле противника
и жмут нопку "огонь". При нажатии происходит проверка программой, "принадлежит" ли данная клетка
какому то кораблю. Если да, то отмечается попадание и клетка окрашивается в красный цвет.
Иначе цвет синий ( промах ).
6) Когда один из игроков совершил попадания по всем клеткам на которых были корабли, 
он - победил и игра завершена.

==================================

Основные элементы программы и этапы разработки

1) Обмен командами по сети между двумя компёютерами используя сокеты.
Необходимо дляя проверки, что тот или инной игрок готов к бою, обмен команадми после 
выбора клетки для обстрела ( d4, f5) для понимания программы противника, куда был совершен выстрел.

2) Создания GUI - форма, содержащая два поля - игрока и противника, радиогруппу для выбора
кораблей, основные кнопки управления.

3) Создания классов, соотв. кораблям, класс "поле" - для себя и поля противника,
"соединение" GUI с программой, тестирование.


classes: COneTubeShip, CTwoTubeShip, CThreeTubeShip, CFourTubeShip,
Количество объектов будет соотв. кол-ву кораблей.
Каждый объект содержит в себе координаты клеток, на которых находиться.
Содержит счетчик попаданий попаданий по себе. 
Имеет метод, при последнем попадание который шлет сигнал программе, что кораблю потоплен.

При каждом выстреле происходит сверение координат каждого корабля с координатами выстрела.


class CField.

Количество объектов - 2. "Свое" плоле и поле противника. 
Содержат матрицу, на которой выполняэться "бой".
Также содержат список кораблей, историю попаданий,
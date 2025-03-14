# Zombie Shooter

## Перед началом

### Установка

Клонировать репозиторий
```
git clone https://github.com/notrurs/zombie_shooter_025.git
```

Установить зависимости
```
pip install -r requirements.txt
```

### Запуск

Запускать игру командой
```
python main.py
```

ВНИМАНИЕ! Для корректного запуска игры, нужно, чтобы в переменной PYTHONPATH был путь до папки `zombie_shooter_025`!

## Как играть

### Управление

Управление на клавиши `WASD`, `ЛКМ` - стрелять.


### Настройки игры

Почти каждый параметр игры можно настроить под себя, воспользовавшись конфигурационным файлом 
[config.py](shooter/config.py), который находится в пакете `shooter`.

### Редактор карт

В игру встроен простой [редактор карт](shooter/resources/levels), который можно найти по пути `shooter/resources/levels`. 
Каждый уровень игры представляет собой обычный `.txt` файл, где специальными символами обозначены
игровые объекты. На данный момент используются следующие обозначения:

* `-` - камень, сквозь который нельзя пройти
* `P` - игрок, может быть только один (технически, можно добавить второго, но тогда игрок будет управлять сразу двумя)
* `Z` - зомби, может быть сколько угодно

Абсолютно под каждым игровым объектом создаётся кусок земли.

#### Как редактировать уровни

При желании, можно отредактировать уже созданный уровень `level.txt`, либо добавить новый следующим образом:

1. Создаём новый txt-файл в папке `levels`
2. В `config.py` прописываем путь к новому уровню, например:
```
LEVEL_2 = _LEVELS_DIR / 'level2.txt'
```
3. В `main.py` импортируем созданный уровень по аналогии с `LEVEL_1`, например:
```
from config import LEVEL_2
```   
4. В `main.py` в классе `GameLogic`, в параметрах вызываемого родительского конструктора меняем `LEVEL_1` на свой 
   импортированный уровень, например:
```
Было:
super().__init__(..., LEVEL_1)

Стало:
super().__init__(..., LEVEL_2)
```
5. Готово! Теперь можно запускать игру

## Помощь в разработке

Каждый может поучаствовать в совершенствовании игры и создать:

* Новые объекты окружения: земля, другие камни, деревья, лужицы и т.д.
* Нового врага
* Ещё один уровень
* Можно объединить три пункта выше и создать уровень с новым контентом!

**Пожалуйста, не изменяйте уже написанный код и уже добавленные объекты!**

## Известные проблемы

1. Иногда персонаж может пройти сквозь препятствие, если он одновременно коснётся двумя сторонами другие препятствия

2. В некоторых случаях зомби может пройти сквозь препятсвие, если он одновременно коснётся двумя сторонами другие 
   препятствия, однако, это происходит довольно редко.

3. Если в редакторе карт расположить препятствия рядом с "живыми" (игрок, зомби и т.д.) игровыми персонажами, 
   они в них могут застрять, поэтому лучше так не делать

## Планы на разработку

1. Добавить меню с упрощенным выбором уровней
2. Добавить музыку и прочие звуковые эффекты
3. Добавить новый контент (уровни и прочие игровые объекты)
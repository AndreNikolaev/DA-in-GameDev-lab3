Отчет по лабораторной работе #3 выполнил(а):
- Николаев Андрей Ильич
- НМТ-233319

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

## Цель работы
Разработать оптимальный баланс нанесения урона оружием для игры Save RTF.

## Задание 1
### Расширить варианты доступного оружия в игре.
Я проанализировал имеющиеся оружие и понял, что не хватает оружия для массовых сражений, а также необходимо разнообразить ближний бой.
Добавленное оружие : бензопила, гранатомет, бита. Необходимо прописать оружию его характеристики.
![image](https://github.com/user-attachments/assets/b179efe7-b442-4cdc-8174-dc7a5a9cc78b)
![image](https://github.com/user-attachments/assets/d3e1739f-5c2b-4c2c-b39f-54e83fd7814d)


## Задание 2
### Визуализируйте параметры оружия в таблице. Используйте шаблон таблицы для визуализации оружия игры Save RTF. Постройте примеры для следующих математических величин:
Мы расписали СКО, Разброс урона оружия и Вариативность времени отклика игрока, благодаря презентации:
- Среднеквадратическое отклонение (СКО)
- Разброс урона оружия
- Вариативность времени отклика игрока (реакция на события)

![image](https://github.com/user-attachments/assets/31d6f2bf-45cf-47e6-9c92-795817fffbee)

Среднеквадратическое отклонение (СКО)

```pу
import numpy as np
import matplotlib.pyplot as plt

# Генерируем 10 случайных выстрелов с отклонениями по x и y
np.random.seed(42)  # Фиксируем рандом для воспроизводимости
shots = np.random.normal(loc=0, scale=5, size=(10, 2))  # Отклонения (x, y)

# Вычисляем отклонения (расстояния от центра цели)
distances = np.linalg.norm(shots, axis=1)

# Среднеквадратическое отклонение
std_dev = np.std(distances)

print(f"СКО отклонений: {std_dev:.2f} пикселей")

# Визуализация попаданий
plt.figure(figsize=(6, 6))
plt.scatter(shots[:, 0], shots[:, 1], color='red', label='Попадания')
plt.scatter(0, 0, color='blue', label='Цель', s=100)
plt.xlim(-20, 20)
plt.ylim(-20, 20)
plt.axhline(0, color='black', lw=0.5)
plt.axvline(0, color='black', lw=0.5)
plt.legend()
plt.title("Модель разброса выстрелов")
plt.gca().set_aspect('equal', adjustable='box')
plt.show()
```
Разброс урона оружия
```ру
import numpy as np
import matplotlib.pyplot as plt

# Генерация случайных значений урона с нормальным распределением
np.random.seed(123)
damage = np.random.normal(loc=50, scale=10, size=100)  # Средний урон = 50, СКО = 10

# Визуализация гистограммы урона
plt.figure(figsize=(8, 6))
plt.hist(damage, bins=10, color='purple', alpha=0.7, edgecolor='black')
plt.axvline(damage.mean(), color='red', linestyle='dashed', linewidth=2, label=f'Среднее: {damage.mean():.2f}')
plt.axvline(damage.mean() + np.std(damage), color='green', linestyle='dotted', label=f'СКО: {np.std(damage):.2f}')
plt.axvline(damage.mean() - np.std(damage), color='green', linestyle='dotted')
plt.legend()
plt.title('Распределение урона оружия')
plt.xlabel('Урон')
plt.ylabel('Частота')
plt.show()
```
Вариативность времени отклика игрока (реакция на события)

```ру
reaction_times = np.random.normal(loc=300, scale=50, size=20)  # Среднее время = 300 мс

plt.figure(figsize=(8, 6))
plt.plot(reaction_times, 'o-', color='teal')
plt.axhline(reaction_times.mean(), color='red', linestyle='dashed', label=f'Среднее: {reaction_times.mean():.2f} мс')
plt.fill_between(range(20),
                 reaction_times.mean() - np.std(reaction_times),
                 reaction_times.mean() + np.std(reaction_times),
                 color='lightgreen', alpha=0.3, label=f'СКО: ±{np.std(reaction_times):.2f} мс')
plt.legend()
plt.title('Время реакции игрока')
plt.xlabel('Событие')
plt.ylabel('Время (мс)')
plt.show()
```
## Задание 3
### Визуализировать данные из google-таблицы, и с помощью Python передавать переменные в проект Unity. В Python данные также должны быть визуализированы.
Ранее с помощью jupyter lab мы записали значения в таблицу СКО (Среднеквадратическое отклонение), Разброс урона оружия и Вариативность времни отклика игрока (реакция на события), теперь необходимо их визуализировать.

![image](https://github.com/user-attachments/assets/e7dd923b-0161-47b4-915c-49ba7fa66aaa)

Ссылка на документ : https://1drv.ms/x/c/348701f34e72ab83/EfoAkugJ66tGhJH1Le1NuVMBSyYujjzYYEByvWhHfUBvuA?e=RyydEr


## Выводы
В данной лабораторной работе мы поняли как работает разработка оптимального баланса нанесения урона оружием в игре Save RTF, попробовали поработать с ним, а также поняли как визиализируют параметры оружие в таблицах и их роль в решении вопроса об оптимальном балансе.

## Powered by
Николаев Андрей Ильич

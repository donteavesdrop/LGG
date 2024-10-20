# LGG
# README

## Описание проекта

Этот проект реализует линейный конгруэнтный генератор случайных чисел (LCG) и анализирует сгенерированные последовательности, используя математические методы, такие как расчет математического ожидания, дисперсии и критерия Пирсона. Проект также визуализирует распределение случайных чисел с помощью гистограмм.

## Структура кода

### 1. Линейный конгруэнтный генератор (LCG)

Функция `random_sequence(n, a, b, m)` генерирует последовательность случайных чисел длиной `n` по методу Линейного конгруэнтного генератора (LCG). 
Параметры:
- `a`: множитель (по умолчанию 22695477)
- `b`: приращение (по умолчанию 1)
- `m`: модуль (по умолчанию 2^32)
- `n`: длина последовательности.

Пример вызова:
```python
random_sequence(5)
```

### 2. Генерация и анализ последовательностей

Для различных значений длины последовательностей `N_values = [10^2, 10^3, 10^4, 10^5]`, код генерирует последовательности случайных чисел, затем масштабирует их для получения значений в пределах от 0 до 10. В каждой последовательности вычисляются:
- Математическое ожидание
- Дисперсия
- Период последовательности (разница между длиной последовательности и количеством уникальных чисел)

### 3. Анализ последовательности

Функция `analyze_sequence(sequence, num_intervals)`:
- Вычисляет относительные частоты для случайной последовательности по интервалам
- Строит гистограмму
- Рассчитывает значение критерия Пирсона для проверки гипотезы равномерности распределения.

#### Пример использования:
```python
analyze_sequence(random_sequence, 10)
```

### 4. Генерация случайной последовательности с использованием встроенного генератора Python

Для сравнения используется встроенный генератор случайных чисел Python, который генерирует последовательность из 1000 чисел с равномерным распределением в диапазоне от 0 до 10:
```python
random_sequence = [random.uniform(0, 10) for _ in range(1000)]
```

### 5. Критерий Пирсона

Функция `chi_squared_test(observed, expected)` реализует критерий Пирсона для проверки равномерности распределения сгенерированных случайных чисел.

### Визуализация

Гистограмма относительных частот случайных чисел строится с помощью библиотеки Matplotlib:
```python
plt.bar(intervals[:-1], relative_freqs, width=interval_width, align='edge')
plt.show()
```

## Зависимости

Для корректной работы кода необходимо установить следующие библиотеки:
- **numpy** для математических вычислений
- **matplotlib** для построения гистограмм

Установка зависимостей:
```bash
pip install numpy matplotlib
```

## Как использовать

1. Клонируйте проект на свой компьютер.
2. Убедитесь, что все зависимости установлены.
3. Запустите файл с кодом для генерации и анализа последовательностей:
```bash
python main.py
```
## ### Результаты выполнения задач

#### Задание 1: Линейный конгруэнтный генератор (LCG)

При генерации последовательности длиной 5 с использованием Линейного конгруэнтного генератора (LCG), были получены следующие числа:
```
[22695478, 2156045615, 2867233980, 71484141, 2911408402]
```
Эта последовательность демонстрирует, как начальное значение преобразуется с использованием коэффициентов генератора для получения новых случайных чисел.

#### Задание 2: Генерация и анализ последовательностей случайных чисел

##### Длина последовательности N = 100:
- **Математическое ожидание**: 4.8447
- **Дисперсия**: 8.1042
- **Период последовательности**: 0

Анализ этой последовательности показывает, что математическое ожидание находится чуть ниже середины диапазона (5.0 для диапазона [0, 10]), а дисперсия близка к значению для равномерного распределения, что указывает на более равномерное распределение чисел.

##### Длина последовательности N = 1000:
- **Математическое ожидание**: 5.0828
- **Дисперсия**: 8.1195
- **Период последовательности**: 0

С увеличением длины последовательности математическое ожидание приближается к 5.0, что подтверждает тенденцию к равномерному распределению. Дисперсия также остается стабильной.

##### Длина последовательности N = 10 000:
- **Математическое ожидание**: 4.9970
- **Дисперсия**: 8.3072
- **Период последовательности**: 0

При анализе 10 000 чисел видно, что математическое ожидание практически идеально близко к 5.0, что свидетельствует о равномерности распределения. Дисперсия чуть выше, но все еще в допустимых пределах.

##### Длина последовательности N = 100 000:
- **Математическое ожидание**: 4.9923
- **Дисперсия**: 8.3443
- **Период последовательности**: 0

Для самой длинной последовательности из 100 000 чисел наблюдается высокая точность: математическое ожидание практически равно 5.0, а дисперсия продолжает расти незначительно, указывая на стабильное распределение чисел.

#### Задание 4: Период последовательности

Для всех последовательностей, независимо от их длины, период равен нулю. Это означает, что в сгенерированных последовательностях не было повторений в пределах заданного количества чисел, что является хорошим признаком для качественного генератора случайных чисел.

#### Общий вывод

Результаты показывают, что генератор случайных чисел, основанный на Линейном конгруэнтном методе, успешно генерирует последовательности с равномерным распределением. Математическое ожидание стабильно приближается к 5.0, а дисперсия остается близкой к теоретическим значениям.

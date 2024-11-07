# pathon-project
Описание проекта
Данный проект посвящен анализу данных о недвижимости в Калифорнии, используя набор данных "kc_house_data.csv". Цель проекта — провести визуализацию и анализ различных аспектов недвижимости, таких как цена, площадь, количество спален, этажей и состояние домов. Проект включает в себя создание графиков и диаграмм, которые помогают выявить основные тренды и зависимости в данных.

Ваша роль в проекте
Я являлся разработчиком и аналитиком данных в этом проекте. Моя задача заключалась в загрузке и обработке данных, а также в создании визуализаций, которые помогают лучше понять распределение и взаимосвязи между различными характеристиками недвижимости.

Использованные технологии
Python
Pandas
Matplotlib
Seaborn
Инструкция по запуску приложения
Для того чтобы запустить проект и проверить его работоспособность, выполните следующие шаги:

Установите необходимые библиотеки:
Убедитесь, что у вас установлены Python и необходимые библиотеки. Вы можете установить их с помощью pip:
pip install pandas matplotlib seaborn
Скачайте данные:
Скачайте файл kc_house_data.csv и поместите его в ту же директорию, где находится ваш скрипт.
Запустите скрипт:
Сохраните код, представленный ниже, в файл с расширением .py, например real_estate_analysis.py и выполните его:
python real_estate_analysis.py
Просмотр результатов:
После выполнения скрипта вы сможете увидеть различные графики и диаграммы, которые иллюстрируют результаты анализа данных.
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
# Загрузка данных
df = pd.read_csv('kc_house_data.csv', sep=',')
# Анализ цен на недвижимость
plt.hist(df['price'], bins=30, edgecolor='black')
plt.xlabel('Цена')
plt.ylabel('Частота')
plt.title('Распределение цен на недвижимость')
plt.show()
# Анализ квадратуры жилой площади
plt.hist(df['sqft_living'], bins=30, edgecolor='black')
plt.xlabel('Квадратура жилой площади')
plt.ylabel('Частота')
plt.title('Распределение квадратуры жилой площади')
plt.show()
# Анализ года постройки
plt.hist(df['yr_built'], bins=30, edgecolor='black')
plt.xlabel('Год постройки')
plt.ylabel('Частота')
plt.title('Распределение года постройки')
plt.show()
# Анализ наличия вида на набережную
with_view_count = df[df['waterfront'] == 1].shape[0]
without_view_count = df[df['waterfront'] == 0].shape[0]
labels = ['С видом на набережную', 'Без вида на набережную']
counts = [with_view_count, without_view_count]
plt.bar(labels, counts)
plt.xlabel('Наличие вида на набережную')
plt.ylabel('Количество домов')
plt.title('Распределение домов от наличия вида на набережную')
plt.show()
# Анализ количества этажей
floors = df['floors']
plt.hist(floors, bins='auto', edgecolor='black')
plt.xlabel('Количество этажей')
plt.ylabel('Количество домов')
plt.title('Распределение этажей домов')
plt.show()
# Анализ состояния домов
condition = df['condition']
sns.countplot(x=condition)
plt.xlabel('Состояние домов')
plt.ylabel('Количество домов')
plt.title('Распределение состояния домов')
plt.show()
# Анализ связи между жилой площадью и ценой недвижимости
living_area = df['sqft_living']
price = df['price']
plt.scatter(living_area, price)
plt.xlabel('Жилая площадь')
plt.ylabel('Цена недвижимости')
plt.title('Связь между жилой площадью и ценой недвижимости')
plt.show()
# Анализ зависимости цены от количества спален
bedrooms = df['bedrooms']
sns.boxplot(x=bedrooms, y=price)
plt.xlabel('Количество спален')
plt.ylabel('Цена недвижимости')
plt.title('Распределение стоимости недвижимости в зависимости от количества спален')
plt.show()
# Анализ средней цены в зависимости от этажей
grouped_data = df.groupby('floors')['price'].mean().reset_index()
plt.bar(grouped_data['floors'], grouped_data['price'])
plt.xlabel('Этажи')
plt.ylabel('Средняя цена')
plt.title('Зависимость этажей от цены')
plt.show()
# Анализ соотношения недвижимости с видом на воду
waterfront = df['waterfront']
count_by_waterfront = df.groupby(waterfront).size()
count_by_waterfront.plot(kind='pie', autopct='%1.1f%%')
plt.title('Соотношение недвижимости с видом на воду')
plt.show()
# Анализ распределения стоимости недвижимости в зависимости от года постройки
year_built = df['yr_built']
plt.hist(year_built, bins='auto', edgecolor='black')
plt.xlabel('Год постройки')
plt.ylabel('Количество домов')
plt.title('Распределение стоимости недвижимости в зависимости от года постройки')
plt.show()
Найти еще
Заключение
Данный проект демонстрирует, как можно использовать Python и библиотеки для анализа данных для визуализации и извлечения полезной информации из набора данных о недвижимости. Выводы, сделанные на основе анализа, могут помочь в принятии решений относительно покупки или продажи недвижимости.

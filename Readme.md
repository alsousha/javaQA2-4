# Отчет о выполнении Задача №1 - Синдром 100%

## Легенда
Вы попали в команду максималистов, которые хотят, чтобы те авто-тесты, которые вы пишете, покрывали код на 100%.

Но вот незадача:

* Непонятно, что такое 100%
* Непонятно, как это сделать
* Вспоминаем: покрытием кода у нас занимается JaCoCo, но он просто "сигнализирует" о том, что конкретно пошло не так.

Большинство подобных плагинов помимо целей отчётности (report) содержат ещё цель check, которая обрушает сборку, если не выполнены определённые проверки.

*Что вам нужно:*

* Изучить документацию на плагин (а конкретно на цель check)
* Внедрить эту цель в фазу verify (обратите внимание, что эта цель итак публикуется в эту фазу)
* Настроить правила по покрытию на 100% (при этом нужно изучить разницу между счётчиками INSTRUCTION, LINE, BRANCH, COMPLEXITY)
* Выбрать один из счётчиков и добиться 100% покрытия тестами
    
Важно: использовать можно только один из следующих:

        INSTRUCTION
        LINE
        BRANCH

*По шагам:*

* Скачиваете проект с лекции
* Изучаете документацию, экспериментируете со счётчиками (INSTRUCTION, LINE, BRANCH, COMPLEXITY)
* Выбираете один из счётчиков (на ваше усмотрение из первых трёх: INSTRUCTION, LINE, BRANCH)
* Запускаете, удостоверяетесь, что сборка падает, делаете push в GitHub (так, чтобы в логах осталось, что сборка падала в CI)
* Дописываете тесты, чтобы обеспечить 100% по выбранному счётчику, делаете push в GitHub (так, чтобы в логах осталось, что сборка зелёная в CI)

Итого: у вас должен быть репозиторий на GitHub, в котором расположен ваш Java-код + файлик README.md, в котором кратко описано, какой из счётчиков за что отвечает.

В рамках задачи проводилось изучение следующих счетчиков плагина jacoco-maven-plugin:

    INSTRUCTION
    LINE
    BRANCH
    COMPLEXITY
    
## INSTRUCTION

Инструкция байт-кода Java - наименьшая единица измерения JaCoCo. Покрытие описывается как процент выполненных и пропущенных инструкций кода. Независит от форматирования файла исходного кода. Доступен даже при отсутствии отладочной информации.

## LINE
Покрытие описывается как процент выполненных и пропущенных строк исходного кода. Зависит от форматирования исходного кода, в следствии чего одна строка может включать в себя несколько инструкций байт-кода. Результат анализа каждой строки подсвечивается в зависимости от количества инструкций покрытых тестом:

* Красный: Не выполнено ни одной инструкции;
* Желтый: Выполнено часть инструкций;
* Зеленый: Выполнены все инструкции. Для работы необходимо компилировать файл с включением отладочной информации.
    
## BRANCH

Вычисляется процент покрытия веток кода определенных операторами if и switch. Счетчик вычисляет количество веток определенное этими операторами и определяет количество выполненных и пропущенных. Поскольку одна ветка может включать в себя несколько инструкций байт-кода результат анализа каждой строки подсвечивается в зависимости от количества инструкций покрытых тестом:

* Красный: Не выполнено ни одной инструкции ветки;
* Желтый: Выполнено часть инструкций ветки;
* Зеленый: Выполнены все инструкции ветки. Доступен даже при отсутствии отладочной информации.

## COMPLEXITY

Циклическая сложность - минимальное количество путей исполнения кода методов, которое принимается как количество возможных тестовых случаев. Таким образом счетчик вычисляет количество выполненных и пропущенных тестовых случаев для каждого метода. Доступен даже при отсутствии отладочной информации.

В процессе выполнения задачи выполнялись тесты со всеми счетчиками. В GitHub выложена сборка со счетчиком LINE.

Выполнение задачи производилось в следующем окружении:

* ОС: Windows 10
* Java: openjdk version "11.0.6" 

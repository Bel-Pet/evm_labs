# CacheMemoryAssotiationDegree

Для экспериментального определения степени ассоциативности кэш-
памяти в программе организуется обход данных в памяти, который вызывает
«буксование» кэш-памяти. Для этого предлагается организовать доступ в
память по адресам, отображаемым на одно и то же множество в кэш-памяти.
Будем увеличивать количество таких конфликтующих обращений. Когда оно
превысит степень ассоциативности кэш-памяти, то данные начнут
вытесняться из кэш-памяти, и возникнет кэш-буксование. Буксование кэш-
памяти приводит к увеличению времени выполнения программы, благодаря
чему можно определить степень ассоциативности кэш-памяти.
Например, для кэш-памяти, представленной на рис. 1, размер банка
составляет 4 КБ, а степень ассоциативности равна четырем. Таким образом,
если многократно выполнять обращения по пяти и более адресам, отстоящим
друг от друга на расстояние, кратное 4 КБ, то мы получим эффект кэш-
буксования.

Чтобы адреса отображались на одно и то же множество в кэш-памяти,
необходимо, чтобы смещение между ними было кратно размеру банка кэш-
памяти. Так как размер банка кэш-памяти не всегда известен, то рассмотрим,
как его можно оценить. Размер кэш-памяти кратен размеру банка, поэтому,
если известен размер кэш-памяти, то расстояние между началами фрагментов
можно взять равным ему. Если же размер кэш-памяти неизвестен, то можно
использовать тот факт, что размеры банков кэш-памяти практически всегда
являются степенью двойки. Для современных процессоров подходящим
смещением между фрагментами будет 224 Б = 16 МБ.

Обход фрагментов данных организуем таким образом, чтобы подряд
происходили обращения к элементам разных фрагментов, отстоящим на
заданное смещение. Сначала последовательно производится чтение всех
первых элементов во всех фрагментах, затем всех вторых, затем – всех
третьих и т.д.

Для проведения эксперимента предлагается выделить массив
достаточно большого размера, чтобы вместить все необходимые фрагменты с
требуемым смещением. Элементы массива образуют связанный список, где
значение каждого элемента является индексом следующего (как в
предыдущей лабораторной работе).

ЗАДАНИЕ К ЛАБОРАТОРНОЙ РАБОТЕ
1. Написать программу, выполняющую обход памяти в соответствии с
заданием.
2. Измерить среднее время доступа к одному элементу массива (в тактах
процессора) для разного числа фрагментов: от 1 до 32. Построить
график зависимости времени от числа фрагментов.
3. По полученному графику определить степень ассоциативности кэш-
памяти, сравнить с реальными характеристиками исследуемого
процессора.

В данной лабораторной работе необходимо было выполнить сложение векторов [код](https://colab.research.google.com/drive/1Ww28XUxTXQSPrPv22u8bl95-elzHKsIQ?usp=sharing) на cpu gpu, произвести замеры времени работ и провести анализ полученных результатов.
Исходный код был написан на языке программирования Python, для использования графического процессора применялась библиотека Numba.

# Ход работы:
1. Генерируем вектора с рандомными целочислкенными значениями (от 0 до 10), заданной размерности (`def generateRandomVector`)
2. Производим сложение векторов на центральном процессоре при помощи функции (`def cpuVectorSum`)
3. Производим подсчет времени работы
4. Производим сложение векторов на графическом процессоре при помощи (`def gpuVectorSum`)
5. Производим подсчет времени работы
6. Сравниваем результаты сложения (равенство двух векторов, полученных разными способами)
7. Усредняем результаты для каждой размерности векторов
8. Строим графики зависимости времени работы программы от размерности векторов (для CPU и GPU)
9. Строим графики зависимости ускорения программы от размерности векторов

Распараллеливанию подлежали математические операции (сложение) для поиска элементов результирующего вектора. Для этого данные двух входных векторов передавались
на девайс, чтобы все созданные нити могли выполнить функцию ядра (`def vectorSum`) над данными. Полученные данные возвращались обратно на хост.
Распараллеливание операций производилось по следующему принципу: каждый поток (ядро cuda) вычислял единственный элемент результирующего вектора.
# Полученные результаты:
![image](https://github.com/Kusakina/high-perfomance-computing/assets/74459357/8cfda038-10a7-447e-857e-3e389b8ed9be)
![image](https://github.com/Kusakina/high-perfomance-computing/assets/74459357/6dec9f5b-ce0f-4f99-ae12-d07558083e27)



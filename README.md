# GAME "Bools and Cows"
Игра "Быки и Коровы" (вариант с числами), реализованная в консоли VisualStudio

## Инструменты
Приложение написано с использованием технологий Console Application и языка программирования C#

## Документация
“Быки и Коровы” - это классическая игра, в которой игрок должен угадать секретное число, состоящее из уникальных цифр. 
Игра предоставляет подсказки в виде “быков” (угаданы цифры и их позиции) и “коров” (угаданы цифры, но не их позиции).
Правила игры:
1. Компьютер генерирует секретное число, состоящее из четырёх уникальных цифр.
2. Игрок вводит свои предположения о числе.
3. Компьютер анализирует предположение и даёт подсказки:
4. “Бык”: если цифра в предположении правильная и находится на правильной позиции.
5. “Корова”: если цифра в предположении правильная, но находится не на правильной позиции.
6. Игрок продолжает вводить предположения, пока не угадает секретное число.

## Поддержка
Если у вас возникли сложности или вопросы по использованию пакета, напишите на [электронную почту](https://mail.google.com/mail)

## Описание генерации загаданного числа
Генерация случайного числа осуществляется в методе RandNumb(). Данный метод создает 4-х значное число, в котором все цифры различны. Полный код метода:
```
static string RandNumb()
        {
            List<int> output = new List<int>();
            int next = 0;
            Random rand = new Random();
            for (int i = 0; i < 4; i++)
            {
                next = rand.Next(0, 10);
                while (output.Contains(next))
                {
                    next = rand.Next(0, 10);
                }
                output.Add(next);
            }
            return string.Join("", output);
        }
```
Теперь поподробнее:
1. Вначале мы создаем список для хранения цифр итогового числа и объект для генерации случайных цифр
   `List<int> output = new List<int>();
   Random rand = new Random();`
2. Затем в цикле с параметром (который выполняется ровно 4 раза) генерируем случайное число.
   `for (int i = 0; i < 4; i++)
            {
                next = rand.Next(0, 10);`
3. Проверяем, содержит ли список итогового числа новую сгенерированную цифру. Если содержит, генерируем её заного в цикле while.
   Действие повторяется до тех пор, пока не будет сгенерирована цифра, не содержащаяся в списке.
   `while (output.Contains(next))
                {
                    next = rand.Next(0, 10);
                }`
4. Добавляем новую сгенерированную цифру в список
   `output.Add(next);`
5. В конце метод возвращает итоговое число (метод string.Join() объединяет все цифры в списке в итоговое число)
   `return string.Join("", output);`
<!--описание коммитов-->
## Описание методов
| Название         | Описание метода                                                       |
|------------------|-----------------------------------------------------------------------|
| Main	           | Основной метод программы, в нём выполняются остальные методы          |
| RandNumb         | Генерация случайного 4-х значного числа для игры                      |
| Durak            | Проверка введённой пользователем строки на предмет лишних символов    |
| GameStart        | Основная логика игры (проверка правильности введённого числа          |
| Win	           | Подсчёт в какой % попыток всех игроков попала попытка текущего игрока |
| WriteDictToFile  | Сохранение аккаунтов пользователей в файл                             |
| ReadDictFromFile | Загрузка всех аккаунтов пользователей из файла                        |

Конец,
Играйте с удовольствием!
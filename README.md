# Отчет по лабораторной работе №2: Управляющие конструкции

## Инструкции по запуску проекта

1. Установите PHP (если не установлен).
2. Скачайте файлы `index_part_one.php` и `index_part_two.php`, `styles.css` по желанию, для стилизации таблицы.
3. Откройте нужный файл в `Visual Studio Code`
4. Откройте терминал и запустите локальный сервер с помощью команды:
   ```sh
   php -S localhost:8000 index_part_one.php
   ```
   ```sh
   php -S localhost:8000 index_part_two.php
   ```
5. Откройте браузер и перейдите по адресу `http://localhost:8000`.

## Описание лабораторной работы

Цель работы – освоить использование условных конструкций и циклов в PHP. В рамках работы реализуется расписание работы сотрудников на основе текущего дня недели и несколько вариантов циклов.

## Краткая документация к проекту

1. Файл `index_part_one.php` содержит код генерация таблицы с расписанием сотрудников на основе текущего дня недели.
2. Файл `index_part_two.php` содержит демонстрацию работы циклов `for`, `while` и `do-while`.

## Фрагменты кода, описание выполнения заданий

  ### Условие `index_part_one.php`:
  ```php
   	<?php
	print ("Today is " . date("l") . "<br><br>");

	$dayOfWeekToday = date("l");

	$dataBase = [
		'1' => [
			'fullname' => 'John Styles',
			'workDays' => ['Monday', 'Wednesday', 'Friday'],
			'workTime' => '8:00-12:00'
		],
		'2' => [
			'fullname' => 'Jane Doe',
			'workDays' => ['Tuesday', 'Thursday', 'Saturday'],
			'workTime' => '12:00-16:00'
		]
	];
	?>
   ```
   Код для первой части лабораторной я вписывал в структру HTML страницы. В предстваленном коде выше я вывел на странице какой сегодня день `print("Today is ".date("l")."<br><br>");`.
   
   Обьявил и инициализировал переменную `$dayOfWeekToday` днем недели, который поулчаю из функции `date("l")` с аргументом `l`.
   
   Далее создаю ассоцированный массив для удобного добавления новых работников в таблицу, массив состоит из ключей `id` сотрудников, значением которых является информация о конкертнои сотруднике, а именно: полное имя, массив из дней в которые работает сотрудник, и график работы.
   
   ```php
   	<table>
		<tr>
			<th>№</th>
			<th>Фамилия Имя</th>
			<th>График работы</th>
		</tr>

		<?php foreach ($dataBase as $workerId => $workerInfo) {
			if (in_array($dayOfWeekToday, $workerInfo['workDays'])) {
				$workTime = $workerInfo['workTime'];
			} else {
				$workTime = "Нерабочий день";
			}
			echo "
					<tr>
					<td>$workerId</td>
					<td>{$workerInfo['fullname']}</td>
					<td>$workTime</td>
					</tr>
				";
		}

		?>

	</table>
  ```
   Создаю таблицу, прописываю первую строку таблицы в HTML, а последующие строки получаю из массива `$dataBase` и вывожу данные о сотруднике, при этом проверяю работает ли он сегодня , если работает вывожу график работы, если не работает, то вывожу `Нерабочий день`.

  ### Циклы `index_part_two.php`:

  ```php
   <?php

$a = 0;
$b = 0;

for ($i = 0; $i <= 5; $i++) {
    $a += 10;
    echo "a = ", $a, " ";
    $b += 5;
    echo "b = ", $b, "<br>";
}
echo "End of the loop: a = $a, b = $b <br><br>";

$a = 0;
$b = 0;
$i = 0;

while ($i <= 5) {
    $a += 10;
    echo "a = ", $a, " ";
    $b += 5;
    echo "b = ", $b, "<br>";
    $i++;
}
echo "End of the loop: a = $a, b = $b <br><br>";

$a = 0;
$b = 0;
$i = 0;

do {
    $a += 10;
    echo "a = ", $a, " ";
    $b += 5;
    echo "b = ", $b, "<br>";
    $i++;
} while ($i <= 5);
echo "End of the loop: a = $a, b = $b <br><br>";
   ```
Демонстрирую работу `for`, `while`, `do while` в php.

## Ответы на контрольные вопросы

1. **Разница между циклами `for`, `while` и `do-while`:**  
   - **`for`** используется, когда известно количество повторений. В нем сразу задаются начальные значения, условие и шаг.  
   - **`while`** выполняет цикл, пока условие истинно. Сначала проверяет условие, а потом выполняет тело цикла.  
   - **`do-while`** всегда выполняет тело цикла хотя бы один раз, так как проверка условия идет после выполнения.

2. **Когда лучше использовать каждый цикл:**  
   - **`for`** — для счетных циклов, когда известен диапазон итераций.  
   - **`while`** — когда неизвестно количество повторений и нужно выполнить цикл до достижения условия.  
   - **`do-while`** — когда нужно, чтобы тело цикла выполнилось хотя бы один раз, независимо от условия.

3. **Как работает тернарный оператор `? :` в PHP:**  
   Тернарный оператор — это короткая форма условного оператора `if-else`. Он проверяет условие и возвращает одно значение, если условие истинно, и другое — если ложно.
   `условие ? значение_если_истинно : значение_если_ложно;`
   
4. **Что произойдет, если в `do-while` условие изначально ложно:**  
   Цикл выполнится один раз, даже если условие с самого начала ложно, потому что проверка идет после выполнения тела цикла.

## Список использованных источников

[www.w3schools.com](https://www.w3schools.com/)

[www.php.net](https://www.php.net/manual/en/)

[github.com/MSU-Courses/advanced-web-programming/](https://github.com/MSU-Courses/advanced-web-programming/blob/main)

[chatgpt.com](https://chatgpt.com/)

## Дополнительные важные аспекты
`                               `

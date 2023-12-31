# 👋 go-assignment-8-election-day

## 🤓 Что делаем?
Закрепляем пройденный материал по конкурентности в go и каналах в частности.

Представим на секунду, что буквально на днях прошли выборы президента и перед нами стоит ответственная задача - автоматизировать процесс подсчета голосов.  
Мы бы могли, конечно, лично подсчитать голоса в каждом избирательном участке, но это бы заняло огромное количество времени. С точки зрения оптимизации процесса было принято решение распараллелить подсчет голосов по областям.  

### Задача

- Реализовать функционал параллельного подсчета голосов для каждой из областей;
- Дождаться завершения исполнения всех горутинг и подсчитать итоговое количество голосов для каждого кандидата. Результат вывести в формате `Кандидат [%s] набрал [%d] голосов`
- **[ADVANCED]** Реализовать программу использую только один `buffered channel`.

## Решение

- Для запуска параллельного исполнения функций используем `go`;
- Для сохранения результата исполнения горутины мы создаем канал и записываем результат в него. Для записи в канал используется направление стрелки `chan<-`;
- В функции `calcVotes` мы принимаем все каналы наших горутин, читаем значения из них и делает итоговый подсчет. Для чтения значения из канала используем направление стрелки `<-chan`
- **[ADVANCED]** Эту программу можно решить используя всего один `buffered channel`.

## 📝 Результаты

Вывод программы в консоль при синхронизации завершения потоков:
```
Идет подсчет голосов в Алматинской области...
Идет подсчет голосов в Жамбылской области...
Идет подсчет голосов в Акмолинской области...
Подсчет голосов в Жамбылской области завершен
Подсчет голосов в Алматинской области завершен
Кандидат [Нурислам] набрал [489] голосов
Кандидат [Ваня] набрал [228] голосов
Кандидат [Рустам] набрал [196] голосов
Кандидат [Куаныш] набрал [317] голосов
```

---
layout: default
title: Метод Audio.Search
permalink: audio/search/
comments: true
---
# Метод Audio.Search
Возвращает список аудиозаписей в соответствии с заданным критерием поиска.

# Синтаксис
```csharp

```

## Параметры
+ **query** - Строка поискового запроса.
+ **totalCount** - Общее количество аудиозаписей удовлетворяющих запросу.
+ **autoComplete** - Если этот параметр равен true, возможные ошибки в поисковом запросе будут исправлены. Например, при поисковом запросе **Иуфдуы** поиск будет осуществляться по строке **Beatles**.
+ **sort** - Вид сортировки.
+ **findLyrics** - Будет ли производиться только по тем аудиозаписям, которые содержат тексты.
+ **count** - Количество возвращаемых аудиозаписей (максимум 200).
+ **offset** - Смещение относительно первой найденной аудиозаписи для выборки определенного подмножества.

## Результат
Возвращает количество аудиозаписей, найденных в соответствии с указанной строкой запроса query, и массив соответствующих им объектов.

## Исключения
+ **AccessTokenInvalidException** - не задан или используется неверный AccessToken.
+ **InvalidParamException** - строка поискового запроса пуста или равна значению null.

## Пример
```csharp
// Ищем аудиозаписи про The Beatles.
int totalCount;
var audios = vk.Audio.Search("Beatles", out totalCount);

// Ищем аудиозаписи про The Beatles, но ошибаясь и выбирая только три записи начиная с пятой, сортированных по длительности.
int totalCount;
var audios = vk.Audio.Search("иуфедуы", out totalCount, true, AudioSort.Duration, true, 3, 5);
```
# Описание языка

* Терминалы - последовательность ASCII-символов, окружённая знаком `"`, например `"terminal"`
* Нетерминалы - последовательность ASCII-символов, окружённая знаком `$`, например `$non_terminal$`
* Пустая строка будет записываться как `EPS`
* Чтобы использовать наши специальные символы как названия будем экранировать их с помощью `\`
* Правило записывается как `$non_terminal$ = {expr}`, где `expr` - последовательность из терминалов, нетерменалов и пустых строк `EPS`
* Вначале файла должна быть строчка `STARTING_NON_TERMINAL = $non_terminal$`, так мы будем задавать стартовый нетерминал
* Также `;` будет символом разделения правил

## Примеры
1. Битовые строки вида 1111...10...000
```python
STARTING_NON_TERMINAL = $S$;
$S$ = { "1" $S$ }; $S$ = { $T$ };
$T$ = { "0" $T$ }; $T$ = { EPS };
```

2. ПСП
```python
STARTING_NON_TERMINAL = $S$;
$S$ = { "(" $S$ ")" $S$ }; $S$ = { EPS };
```

3. Строки состоящие из символов a, b, c
```python
STARTING_NON_TERMINAL = $S$;
$S$ = { "a" $S$ }; $S$ = { "b" $S$ };
$S$ = { "c" $S$ }; $S$ = { EPS };
```
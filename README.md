# Анализ загрузки страницы `https://kmept.ru/...` через Chrome DevTools

## 1. 📂 Network

- **HAR-файл**: ![[kmept.ru 1.har]]

### 📌 Неоптимальные места (со скриншотами):

- **Дублирующиеся ресурсы**:
![](Pasted%20image%2020250629135335.png)
дублируется файл style.css (3 раза)

![](Pasted%20image%2020250629135636.png)
дублируется файл react-with-dom-and-polyfills.min.js

![](Pasted%20image%2020250629140425.png)
vendors.chunk.bundle.js

![](Pasted%20image%2020250629140506.png)
watch.js

![](Pasted%20image%2020250629140901.png)
advert.gif


- **Большой размер ресурса**:
  
  ![](Pasted%20image%2020250629141458.png)огромные размеры изображений
  
  ![](Pasted%20image%2020250629141700.png)файлы watch.js, advanced...js и так большие, так еще и загружаюся сразу несколько раз. зачем-то light и dark загружаются одновременно, хотя пользователю нужно только одно. также файлы tag.js и core.js большие

- **Медленные ресурсы**:
  
  ![](Pasted%20image%2020250629142204.png)
  изображения маленькие, но загружаются неоправданно долго
  
  ![](Pasted%20image%2020250629142515.png)
  крупные скрипты main.js react-with-dom-and-polyfills.js tag.js watch.js тормозят рендер
  
  ![](Pasted%20image%2020250629142647.png)слишком долго для шрифтов

- **Блокирующие ресурсы**:
  ![](Pasted%20image%2020250629161152.png)
  эти css файлы загрузаются и блокируют отрисовку

## 2. ⏱ Performance

- **Файл профиля**: _прикреплён: `performance.json`_

### ⏳ Метрики загрузки:

| Событие                  | Время (мс) |
| ------------------------ | ---------- |
| First Contentful Paint   | 8,369.4    |
| Largest Contentful Paint | 8,369.4    |
| DOMContentLoaded         | 128,452.5  |
| Load                     | 143,827.0  |
![](Pasted%20image%2020250629175805.png)
- **LCP DOM-элемент**: `<h1>Web-дизайнер: особенности профессии, как поступить и какие экзамены сдавать</h1>`

### 📊 Этапы обработки документа:

| Этап      | Время (мс) |
| --------- | ---------- |
| Loading   | 21         |
| Scripting | 3,616      |
| Rendering | 531        |
| Painting  | 191        |
![](Pasted%20image%2020250629180350.png)
## 3. 📉 Coverage

- **Скриншот вкладки Coverage**:
  ![](Pasted%20image%2020250629180952.png)

### 📦 Неиспользованные ресурсы:

| Тип | Использовано (KB) | Всего (KB) | Неиспользовано (KB) |
| --- | ----------------- | ---------- | ------------------- |
| CSS | 300.33            | 228.77     | **71.57 KB**        |
| JS  | 1777.31           | 889.0      | **881.31 KB**       |

---


# Весь DOM (Document Object Model) в JavaScript

## Базовые понятия
1. **DOM (Document Object Model)** — программный интерфейс для HTML/XML документов, представляющий страницу в виде дерева объектов.
2. **DOM-дерево** — иерархическая структура всех узлов документа.
3. **Узел (Node)** — базовый элемент DOM-дерева (документ, элемент, текст, атрибут, комментарий).
4. **Элемент (Element)** — HTML-тег (например, `<div>`, `<p>`, `<a>`).
5. **Текстовый узел (Text Node)** — текстовое содержимое внутри элемента.
6. **Атрибут (Attribute)** — характеристики элемента (`class`, `id`, `src`).
7. **Документ (Document)** — корневой объект, представляющий всю страницу.
8. **window** — глобальный объект браузера, содержащий `document` и другие API.

## Типы узлов (Node Types)
9. **Node.ELEMENT_NODE (1)** — элемент (тег).
10. **Node.ATTRIBUTE_NODE (2)** — атрибут (устаревший).
11. **Node.TEXT_NODE (3)** — текстовый узел.
12. **Node.CDATA_SECTION_NODE (4)** — CDATA секция (XML).
13. **Node.ENTITY_REFERENCE_NODE (5)** — ссылка на сущность (устаревший).
14. **Node.ENTITY_NODE (6)** — сущность (устаревший).
15. **Node.PROCESSING_INSTRUCTION_NODE (7)** — инструкция обработки (XML).
16. **Node.COMMENT_NODE (8)** — комментарий (`<!-- comment -->`).
17. **Node.DOCUMENT_NODE (9)** — корневой документ.
18. **Node.DOCUMENT_TYPE_NODE (10)** — тип документа (`<!DOCTYPE html>`).
19. **Node.DOCUMENT_FRAGMENT_NODE (11)** — фрагмент документа (для batch-операций).
20. **Node.NOTATION_NODE (12)** — нотация (устаревший).

## Навигация по дереву
21. **parentNode** — родительский узел.
22. **parentElement** — родительский элемент (без текстовых узлов).
23. **childNodes** — все дочерние узлы (включая текст, комментарии).
24. **children** — все дочерние элементы (только теги, без текста).
25. **firstChild** — первый дочерний узел.
26. **lastChild** — последний дочерний узел.
27. **firstElementChild** — первый дочерний элемент.
28. **lastElementChild** — последний дочерний элемент.
29. **previousSibling** — предыдущий узел-сосед.
30. **nextSibling** — следующий узел-сосед.
31. **previousElementSibling** — предыдущий элемент-сосед.
32. **nextElementSibling** — следующий элемент-сосед.
33. **ownerDocument** — документ, которому принадлежит узел.
34. **rootNode** — корневой узел (документ или фрагмент).
35. **nodeName** — имя узла (для элементов — тег в верхнем регистре).
36. **nodeType** — числовой код типа узла.
37. **nodeValue** — значение узла (для текстовых, комментариев).

## Поиск элементов
38. **document.getElementById(id)** — поиск элемента по id.
39. **document.getElementsByClassName(className)** — поиск по классу (HTMLCollection).
40. **document.getElementsByTagName(tagName)** — поиск по тегу (HTMLCollection).
41. **document.getElementsByName(name)** — поиск по атрибуту name (HTMLCollection).
42. **document.querySelector(selector)** — поиск первого элемента по CSS-селектору.
43. **document.querySelectorAll(selector)** — поиск всех элементов по CSS-селектору (NodeList).
44. **element.querySelector(selector)** — поиск внутри элемента.
45. **element.querySelectorAll(selector)** — поиск всех внутри элемента.
46. **element.matches(selector)** — проверка, соответствует ли элемент селектору.
47. **element.closest(selector)** — поиск ближайшего предка (включая себя) по селектору.
48. **document.all** — устаревшая коллекция всех элементов.
49. **document.forms** — коллекция всех форм.
50. **document.images** — коллекция всех изображений.
51. **document.links** — коллекция всех ссылок.
52. **document.scripts** — коллекция всех скриптов.
53. **document.styleSheets** — коллекция всех CSS-стилей.

## Свойства элементов
54. **element.id** — ID элемента.
55. **element.className** — строка с классами (через пробел).
56. **element.classList** — объект DOMTokenList для работы с классами.
57. **element.tagName** — имя тега (в верхнем регистре).
58. **element.nodeName** — имя узла.
59. **element.innerHTML** — HTML-содержимое элемента (включая теги).
60. **element.innerText** — текст внутри элемента (без тегов, с учётом стилей).
61. **element.textContent** — текст внутри элемента (все текстовые узлы, без стилей).
62. **element.outerHTML** — HTML элемента вместе с самим элементом.
63. **element.outerText** — текст элемента и его потомков (с заменой).
64. **element.hidden** — булевое свойство скрытости.
65. **element.title** — всплывающая подсказка (tooltip).
66. **element.dir** — направление текста (ltr, rtl).
67. **element.lang** — язык элемента.
68. **element.tabIndex** — порядок фокусировки.
69. **element.draggable** — возможность перетаскивания.
70. **element.contentEditable** — редактируемость содержимого.

## Работа с классами (classList)
71. **classList.add(className)** — добавляет класс.
72. **classList.remove(className)** — удаляет класс.
73. **classList.toggle(className, force)** — переключает класс.
74. **classList.contains(className)** — проверяет наличие класса.
75. **classList.replace(oldClass, newClass)** — заменяет класс.
76. **classList.item(index)** — возвращает класс по индексу.
77. **classList.toString()** — возвращает строку с классами.

## Работа с атрибутами
78. **element.getAttribute(name)** — возвращает значение атрибута.
79. **element.setAttribute(name, value)** — устанавливает атрибут.
80. **element.removeAttribute(name)** — удаляет атрибут.
81. **element.hasAttribute(name)** — проверяет наличие атрибута.
82. **element.hasAttributes()** — проверяет, есть ли атрибуты.
83. **element.getAttributeNames()** — возвращает массив имён атрибутов.
84. **element.attributes** — коллекция всех атрибутов (NamedNodeMap).
85. **element.dataset** — объект для работы с data-атрибутами.
86. **element.dataset.userId** — доступ к `data-user-id`.
87. **element.dataset.userName** — доступ к `data-user-name` (camelCase).
88. **element.dataset['userId']** — доступ через квадратные скобки.
89. **delete element.dataset.userId** — удаление data-атрибута.
90. **element.style** — объект CSSStyleDeclaration для inline-стилей.
91. **element.style.color = 'red'** — установка CSS-свойства (camelCase).
92. **element.style.setProperty('color', 'red')** — установка свойства.
93. **element.style.getPropertyValue('color')** — получение значения.
94. **element.style.removeProperty('color')** — удаление свойства.
95. **element.style.cssText** — строка со всеми inline-стилями.

## Создание и вставка элементов
96. **document.createElement(tagName)** — создаёт новый элемент.
97. **document.createTextNode(text)** — создаёт текстовый узел.
98. **document.createComment(text)** — создаёт комментарий.
99. **document.createDocumentFragment()** — создаёт фрагмент (для batch-вставки).
100. **document.createAttribute(name)** — создаёт атрибут.
101. **element.cloneNode(deep)** — клонирует элемент (true = с потомками).
102. **parent.appendChild(child)** — добавляет дочерний элемент в конец.
103. **parent.append(...nodes)** — добавляет элементы или строки в конец.
104. **parent.prepend(...nodes)** — добавляет элементы или строки в начало.
105. **parent.insertBefore(newNode, referenceNode)** — вставляет перед узлом.
106. **parent.insertAdjacentElement(position, element)** — вставка элемента.
107. **parent.insertAdjacentHTML(position, html)** — вставка HTML.
108. **parent.insertAdjacentText(position, text)** — вставка текста.
109. **element.replaceWith(...nodes)** — заменяет элемент другими.
110. **element.replaceChild(newNode, oldNode)** — заменяет дочерний узел.
111. **parent.removeChild(child)** — удаляет дочерний узел.
112. **element.remove()** — удаляет элемент из DOM.
113. **element.before(...nodes)** — вставляет элементы перед элементом.
114. **element.after(...nodes)** — вставляет элементы после элемента.
115. **element.replaceChildren(...nodes)** — заменяет всех детей (ES2022).

## Позиции для insertAdjacent
116. **'beforebegin'** — перед элементом.
117. **'afterbegin'** — внутри элемента, в начало.
118. **'beforeend'** — внутри элемента, в конец.
119. **'afterend'** — после элемента.

## Размеры и позиции элементов
120. **element.offsetParent** — ближайший позиционированный родитель.
121. **element.offsetLeft** — смещение от offsetParent (влево).
122. **element.offsetTop** — смещение от offsetParent (вверх).
123. **element.offsetWidth** — ширина элемента (с padding, border).
124. **element.offsetHeight** — высота элемента (с padding, border).
125. **element.clientLeft** — ширина левой границы + скролл.
126. **element.clientTop** — ширина верхней границы + скролл.
127. **element.clientWidth** — ширина видимой области (с padding, без border).
128. **element.clientHeight** — высота видимой области (с padding, без border).
129. **element.scrollLeft** — горизонтальная прокрутка.
130. **element.scrollTop** — вертикальная прокрутка.
131. **element.scrollWidth** — полная ширина (с прокручиваемой областью).
132. **element.scrollHeight** — полная высота (с прокручиваемой областью).
133. **element.getBoundingClientRect()** — координаты относительно окна.
134. **element.getClientRects()** — список прямоугольников (для многострочных).
135. **element.scrollIntoView(options)** — прокрутка к элементу.
136. **element.scrollTo(x, y)** — прокрутка к координатам.
137. **element.scrollBy(x, y)** — прокрутка на смещение.

## События (Events)
138. **element.addEventListener(event, handler, options)** — добавляет слушатель.
139. **element.removeEventListener(event, handler)** — удаляет слушатель.
140. **element.dispatchEvent(event)** — искусственно вызывает событие.
141. **Event** — базовый объект события.
142. **event.type** — тип события ('click', 'keydown').
143. **event.target** — элемент, на котором произошло событие.
144. **event.currentTarget** — элемент, на который навешен слушатель.
145. **event.eventPhase** — фаза события (1=захват, 2=цель, 3=всплытие).
146. **event.bubbles** — всплывает ли событие.
147. **event.cancelable** — можно ли отменить событие.
148. **event.preventDefault()** — отменяет поведение по умолчанию.
149. **event.stopPropagation()** — останавливает всплытие/захват.
150. **event.stopImmediatePropagation()** — останавливает все слушатели.
151. **event.composed** — может ли событие проходить через shadow DOM.
152. **event.isTrusted** — событие сгенерировано пользователем (true) или скриптом (false).
153. **MouseEvent** — свойства кликов (clientX, clientY, pageX, pageY, button, buttons, shiftKey и др.).
154. **KeyboardEvent** — свойства клавиатуры (key, code, altKey, ctrlKey, shiftKey, metaKey).
155. **FocusEvent** — события фокуса (relatedTarget).
156. **InputEvent** — события ввода (data, inputType).
157. **ClipboardEvent** — буфер обмена (clipboardData).
158. **DragEvent** — перетаскивание (dataTransfer).
159. **TouchEvent** — касания (touches, targetTouches, changedTouches).
160. **WheelEvent** — прокрутка колесиком (deltaX, deltaY, deltaZ).
161. **UIEvent** — пользовательские события (view, detail).
162. **CustomEvent** — пользовательские события с данными (detail).

## События мыши
163. **click** — клик (левый).
164. **dblclick** — двойной клик.
165. **mousedown** — нажатие кнопки мыши.
166. **mouseup** — отпускание кнопки мыши.
167. **mouseenter** — вход курсора в элемент (не всплывает).
168. **mouseleave** — выход курсора из элемента (не всплывает).
169. **mouseover** — вход курсора в элемент (всплывает).
170. **mouseout** — выход курсора из элемента (всплывает).
171. **mousemove** — движение курсора.
172. **contextmenu** — вызов контекстного меню (правый клик).
173. **wheel** — вращение колесика мыши.
174. **drag** — перетаскивание (элемент).
175. **dragstart** — начало перетаскивания.
176. **dragend** — конец перетаскивания.
177. **dragenter** — вход в область дропа.
178. **dragleave** — выход из области дропа.
179. **dragover** — перетаскивание над областью дропа.
180. **drop** — сброс в область дропа.

## События клавиатуры
181. **keydown** — нажатие клавиши (повторяется при зажатии).
182. **keyup** — отпускание клавиши.
183. **keypress** — нажатие символа (устаревший, не использовать).
184. **event.key** — значение клавиши ('Enter', 'a', 'ArrowUp').
185. **event.code** — физическая клавиша ('Enter', 'KeyA', 'ArrowUp').

## События формы
186. **submit** — отправка формы.
187. **reset** — сброс формы.
188. **change** — изменение значения (после потери фокуса).
189. **input** — изменение значения (немедленно).
190. **focus** — получение фокуса.
191. **blur** — потеря фокуса.
192. **focusin** — получение фокуса (всплывает).
193. **focusout** — потеря фокуса (всплывает).
194. **select** — выделение текста в input/textarea.
195. **invalid** — невалидность формы.

## События документа и окна
196. **DOMContentLoaded** — DOM дерево загружено (не ждёт картинки).
197. **load** — вся страница загружена (включая ресурсы).
198. **beforeunload** — перед закрытием страницы.
199. **unload** — страница закрывается (не использовать).
200. **pagehide** — страница скрывается (для bfcache).
201. **pageshow** — страница показывается (из bfcache).
202. **resize** — изменение размера окна.
203. **scroll** — прокрутка.
204. **hashchange** — изменение hash (#).
205. **popstate** — изменение истории (навигация).
206. **online** — появление интернета.
207. **offline** — пропадание интернета.
208. **error** — ошибка (на window, изображениях, скриптах).
209. **abort** — прерывание загрузки.
210. **beforeunload** — перед уходом (можно показать предупреждение).

## События медиа
211. **play** — воспроизведение начато.
212. **pause** — воспроизведение приостановлено.
213. **ended** — воспроизведение завершено.
214. **volumechange** — изменение громкости.
215. **timeupdate** — обновление времени воспроизведения.
216. **loadeddata** — данные загружены.
217. **canplay** — можно начать воспроизведение.
218. **canplaythrough** — можно воспроизвести без остановок.
219. **seeking** — начат поиск.
220. **seeked** — поиск завершён.

## События анимации
221. **animationstart** — анимация началась.
222. **animationend** — анимация завершилась.
223. **animationiteration** — итерация анимации.
224. **transitionstart** — переход начался.
225. **transitionend** — переход завершился.
226. **transitioncancel** — переход отменён.

## События буфера обмена
227. **copy** — копирование.
228. **cut** — вырезание.
229. **paste** — вставка.

## События сенсоров
230. **touchstart** — касание начато.
231. **touchmove** — касание перемещается.
232. **touchend** — касание завершено.
233. **touchcancel** — касание отменено.
234. **deviceorientation** — ориентация устройства.
235. **devicemotion** — движение устройства.

## События скролла
236. **scroll** — прокрутка.
237. **scrollend** — прокрутка завершена (экспериментальный).

## Форма и элементы ввода
238. **document.forms** — коллекция форм.
239. **form.elements** — коллекция элементов формы.
240. **form.submit()** — программная отправка формы.
241. **form.reset()** — программный сброс формы.
242. **input.value** — значение input/textarea.
243. **input.checked** — состояние checkbox/radio.
244. **input.files** — список файлов (file input).
245. **input.selectionStart** — начало выделения.
246. **input.selectionEnd** — конец выделения.
247. **input.select()** — выделение текста.
248. **input.setSelectionRange(start, end)** — установка выделения.
249. **input.setRangeText(replacement)** — замена выделенного текста.
250. **input.stepUp()** — увеличение значения (number).
251. **input.stepDown()** — уменьшение значения (number).
252. **select.options** — коллекция опций.
253. **select.selectedIndex** — индекс выбранной опции.
254. **select.value** — значение выбранной опции.
255. **select.add(option)** — добавление опции.
256. **select.remove(index)** — удаление опции.
257. **option.selected** — выбрана ли опция.
258. **option.value** — значение опции.
259. **option.text** — текст опции.

## Форматы и стилизация
260. **window.getComputedStyle(element)** — вычисленные стили.
261. **element.style** — inline-стили.
262. **element.cssText** — все inline-стили одной строкой.
263. **element.className** — строка классов.
264. **element.classList** — объект DOMTokenList.
265. **element.tagName** — тег.
266. **element.nodeName** — имя узла.
267. **element.nodeType** — тип узла.

## Shadow DOM
268. **element.attachShadow(mode)** — создаёт Shadow DOM.
269. **element.shadowRoot** — ссылка на Shadow DOM.
270. **mode: 'open'** — доступно извне.
271. **mode: 'closed'** — недоступно извне.
272. **slot** — элемент для распределения содержимого.
273. **assignedNodes()** — узлы, распределённые в слот.

## Custom Elements
274. **customElements.define(name, class)** — регистрация кастомного элемента.
275. **customElements.get(name)** — получение класса кастомного элемента.
276. **customElements.whenDefined(name)** — Promise при регистрации.
277. **connectedCallback()** — элемент добавлен в DOM.
278. **disconnectedCallback()** — элемент удалён из DOM.
279. **adoptedCallback()** — элемент перемещён в другой документ.
280. **attributeChangedCallback(name, old, new)** — изменение атрибута.
281. **observedAttributes** — список наблюдаемых атрибутов.

## MutationObserver
282. **MutationObserver(callback)** — наблюдение за изменениями DOM.
283. **observer.observe(target, options)** — начало наблюдения.
284. **observer.disconnect()** — остановка наблюдения.
285. **observer.takeRecords()** — получение записей.
286. **childList** — изменения детей.
287. **attributes** — изменения атрибутов.
288. **characterData** — изменения текста.
289. **subtree** — наблюдение за поддеревом.
290. **attributeOldValue** — сохранение старого значения атрибута.
291. **characterDataOldValue** — сохранение старого текста.

## IntersectionObserver
292. **IntersectionObserver(callback, options)** — наблюдение за видимостью.
293. **observer.observe(element)** — начало наблюдения.
294. **observer.unobserve(element)** — остановка наблюдения.
295. **observer.disconnect()** — остановка всех наблюдений.
296. **options.root** — контейнер для проверки.
297. **options.rootMargin** — отступы контейнера.
298. **options.threshold** — порог видимости (0-1).
299. **entry.isIntersecting** — элемент видим.
300. **entry.intersectionRatio** — процент видимости.

## ResizeObserver
301. **ResizeObserver(callback)** — наблюдение за изменением размера.
302. **observer.observe(element)** — начало наблюдения.
303. **observer.unobserve(element)** — остановка наблюдения.
304. **observer.disconnect()** — остановка всех наблюдений.
305. **entry.contentRect** — размеры элемента.
306. **entry.borderBoxSize** — размер с border.
307. **entry.contentBoxSize** — размер с padding.

## Performance Observer
308. **PerformanceObserver(callback)** — наблюдение за производительностью.
309. **observer.observe({ entryTypes: [] })** — начало наблюдения.
310. **observer.disconnect()** — остановка наблюдения.
311. **entryTypes** — типы записей ('paint', 'navigation', 'resource').

## ReportingObserver
312. **ReportingObserver(callback, options)** — наблюдение за отчётами.
313. **observer.observe()** — начало наблюдения.
314. **observer.disconnect()** — остановка наблюдения.
315. **options.types** — типы отчётов ('deprecation', 'intervention').

## DOMTokenList (classList)
316. **classList.add()** — добавляет класс.
317. **classList.remove()** — удаляет класс.
318. **classList.toggle()** — переключает класс.
319. **classList.contains()** — проверяет наличие.
320. **classList.replace()** — заменяет класс.
321. **classList.item()** — возвращает класс по индексу.
322. **classList.toString()** — строка классов.
323. **classList.length** — количество классов.

## NodeList vs HTMLCollection
324. **NodeList** — коллекция узлов (querySelectorAll, childNodes).
325. **HTMLCollection** — коллекция элементов (getElementsByTagName, children).
326. **NodeList.forEach()** — итерация.
327. **HTMLCollection** — нет forEach (только for...of или Array.from).
328. **NodeList.length** — количество узлов.
329. **HTMLCollection.length** — количество элементов.
330. **NodeList.item(index)** — узел по индексу.
331. **HTMLCollection.item(index)** — элемент по индексу.
332. **NodeList.namedItem(name)** — узел по имени.
333. **HTMLCollection.namedItem(name)** — элемент по имени.

## window объект
334. **window.innerWidth** — ширина окна (с прокруткой).
335. **window.innerHeight** — высота окна (с прокруткой).
336. **window.outerWidth** — ширина окна (включая UI).
337. **window.outerHeight** — высота окна (включая UI).
338. **window.scrollX** — горизонтальная прокрутка.
339. **window.scrollY** — вертикальная прокрутка.
340. **window.pageXOffset** — то же, что scrollX.
341. **window.pageYOffset** — то же, что scrollY.
342. **window.screenX** — положение окна по X.
343. **window.screenY** — положение окна по Y.
344. **window.screen** — объект с информацией об экране.
345. **window.screen.width** — ширина экрана.
346. **window.screen.height** — высота экрана.
347. **window.screen.availWidth** — доступная ширина (без панелей).
348. **window.screen.availHeight** — доступная высота (без панелей).
349. **window.location** — объект с URL.
350. **window.location.href** — полный URL.
351. **window.location.protocol** — протокол (https:).
352. **window.location.host** — хост (example.com:8080).
353. **window.location.hostname** — имя хоста (example.com).
354. **window.location.port** — порт (8080).
355. **window.location.pathname** — путь (/page).
356. **window.location.search** — строка запроса (?a=1).
357. **window.location.hash** — хэш (#section).
358. **window.location.origin** — происхождение (https://example.com).
359. **window.location.assign(url)** — переход на URL.
360. **window.location.replace(url)** — замена URL (без истории).
361. **window.location.reload()** — перезагрузка страницы.
362. **window.history** — объект истории.
363. **window.history.length** — количество записей.
364. **window.history.back()** — назад.
365. **window.history.forward()** — вперёд.
366. **window.history.go(n)** — переход на n записей.
367. **window.history.pushState(state, title, url)** — добавление записи.
368. **window.history.replaceState(state, title, url)** — замена записи.
369. **window.navigator** — информация о браузере.
370. **window.navigator.userAgent** — строка user agent.
371. **window.navigator.language** — язык браузера.
372. **window.navigator.cookieEnabled** — включены ли cookies.
373. **window.navigator.onLine** — есть ли интернет.
374. **window.navigator.platform** — платформа ('Win32', 'MacIntel').
375. **window.navigator.geolocation** — геолокация.
376. **window.navigator.mediaDevices** — медиа-устройства.
377. **window.navigator.clipboard** — буфер обмена.
378. **window.navigator.serviceWorker** — Service Worker.
379. **window.navigator.storage** — хранилище.

## document объект
380. **document.documentElement** — корневой элемент (html).
381. **document.head** — элемент head.
382. **document.body** — элемент body.
383. **document.title** — заголовок страницы.
384. **document.URL** — полный URL.
385. **document.documentURI** — URI документа.
386. **document.domain** — домен страницы.
387. **document.referrer** — источник перехода.
388. **document.cookie** — cookies (строка).
389. **document.cookie = 'name=value'** — установка cookie.
390. **document.readyState** — состояние загрузки ('loading', 'interactive', 'complete').
391. **document.characterSet** — кодировка.
392. **document.contentType** — тип содержимого ('text/html').
393. **document.activeElement** — элемент в фокусе.
394. **document.hasFocus()** — есть ли фокус.
395. **document.designMode** — режим редактирования.
396. **document.execCommand(command, showUI, value)** — выполнение команды (устаревший).
397. **document.createEvent(eventType)** — создание события (устаревший).
398. **document.createRange()** — создание Range.
399. **document.getSelection()** — текущее выделение.
400. **document.adoptNode(node)** — перенос узла в документ.
401. **document.importNode(node, deep)** — импорт узла.
402. **document.normalize()** — объединение текстовых узлов.

## Range и Selection
403. **Range** — объект для работы с диапазонами текста.
404. **range.setStart(node, offset)** — установка начала.
405. **range.setEnd(node, offset)** — установка конца.
406. **range.selectNode(node)** — выбор узла.
407. **range.selectNodeContents(node)** — выбор содержимого узла.
408. **range.collapse(toStart)** — схлопывание диапазона.
409. **range.deleteContents()** — удаление содержимого.
410. **range.extractContents()** — извлечение содержимого.
411. **range.insertNode(node)** — вставка узла.
412. **range.surroundContents(node)** — обёртывание содержимого.
413. **range.cloneContents()** — клонирование содержимого.
414. **range.comparePoint(node, offset)** — сравнение точки с диапазоном.
415. **range.intersectsNode(node)** — пересечение с узлом.
416. **Selection** — объект для работы с выделением.
417. **window.getSelection()** — получение выделения.
418. **selection.anchorNode** — узел начала.
419. **selection.anchorOffset** — смещение начала.
420. **selection.focusNode** — узел конца.
421. **selection.focusOffset** — смещение конца.
422. **selection.isCollapsed** — схлопнуто ли выделение.
423. **selection.rangeCount** — количество диапазонов.
424. **selection.getRangeAt(index)** — получение диапазона.
425. **selection.addRange(range)** — добавление диапазона.
426. **selection.removeRange(range)** — удаление диапазона.
427. **selection.removeAllRanges()** — очистка выделения.
428. **selection.selectAllChildren(node)** — выделение всех потомков.
429. **selection.setBaseAndExtent(anchorNode, anchorOffset, focusNode, focusOffset)** — установка выделения.
430. **selection.deleteFromDocument()** — удаление выделенного.

## API форм и валидация
431. **form.checkValidity()** — проверка валидности всей формы.
432. **form.reportValidity()** — проверка с отображением ошибок.
433. **form.requestSubmit()** — отправка формы.
434. **input.checkValidity()** — проверка валидности поля.
435. **input.reportValidity()** — проверка с отображением ошибки.
436. **input.setCustomValidity(message)** — установка кастомной валидации.
437. **input.validationMessage** — сообщение об ошибке.
438. **input.validity** — объект ValidityState.
439. **input.validity.valueMissing** — обязательное поле пусто.
440. **input.validity.typeMismatch** — неверный тип (email, url).
441. **input.validity.patternMismatch** — не соответствует паттерну.
442. **input.validity.tooLong** — слишком длинное.
443. **input.validity.tooShort** — слишком короткое.
444. **input.validity.rangeUnderflow** — значение ниже минимума.
445. **input.validity.rangeOverflow** — значение выше максимума.
446. **input.validity.stepMismatch** — не соответствует шагу.
447. **input.validity.badInput** — некорректный ввод.
448. **input.validity.customError** — кастомная ошибка.
449. **input.validity.valid** — поле валидно.

## Web Components
450. **CustomElementRegistry** — реестр кастомных элементов.
451. **ShadowRoot** — корень Shadow DOM.
452. **HTMLTemplateElement** — элемент template.
453. **template.content** — содержимое шаблона.
454. **slot** — элемент слота.
455. **slotchange** — событие изменения слота.
456. **Element.attachShadow()** — создание Shadow DOM.
457. **Element.shadowRoot** — доступ к Shadow DOM.
458. **Event.composed** — событие проходит через Shadow DOM.

## DOM Manipulation Performance
459. **DocumentFragment** — для batch-вставки (меньше рефлоу).
460. **element.cloneNode(true)** — глубокое клонирование.
461. **element.remove()** — удаление элемента.
462. **element.replaceChildren()** — замена детей.
463. **requestAnimationFrame** — синхронизация с рендерингом.
464. **Avoiding layout thrashing** — чтение и запись по отдельности.
465. **Batch DOM updates** — группировка изменений.
466. **Offscreen DOM** — работа вне DOM-дерева.
467. **Virtual DOM** — React, Vue, Svelte (не встроенный).
468. **`el.innerHTML = ''`** — быстрая очистка (но удаляет слушатели).
469. **`el.textContent = ''`** — очистка текста (сохраняет слушатели).

## DOM Event Flow
470. **Capture phase** — от окна к цели.
471. **Target phase** — цель события.
472. **Bubble phase** — от цели к окну.
473. **event.stopPropagation()** — остановка всплытия/захвата.
474. **event.stopImmediatePropagation()** — остановка всех слушателей.
475. **addEventListener(..., { capture: true })** — слушатель на фазе захвата.
476. **addEventListener(..., { once: true })** — слушатель срабатывает один раз.
477. **addEventListener(..., { passive: true })** — предотвращает scroll (для touch).
478. **addEventListener(..., { signal: abortController.signal })** — автоматическое удаление.

## DOM Security
479. **XSS (Cross-Site Scripting)** — инъекция скриптов.
480. **CSP (Content Security Policy)** — защита от XSS.
481. **Sanitization** — очистка HTML (DOMPurify).
482. **innerHTML vs textContent** — textContent безопаснее.
483. **iframe sandbox** — изоляция контента.
484. **Event listener limits** — ограничение слушателей.
485. **Cross-origin** — ограничения по происхождению.

## Cross-Origin
486. **same-origin policy** — политика одного источника.
487. **CORS (Cross-Origin Resource Sharing)** — заголовки для кросс-домена.
488. **document.domain** — изменение домена для iframe.
489. **postMessage** — обмен данными между окнами/iframe.
490. **window.origin** — происхождение окна.
491. **message event** — приём сообщений postMessage.

## iframe
492. **document.iframe** — создание iframe.
493. **iframe.contentWindow** — window внутри iframe.
494. **iframe.contentDocument** — document внутри iframe.
495. **iframe.src** — URL загруженного документа.
496. **iframe.sandbox** — ограничения для iframe.
497. **iframe.allow** — разрешения (геолокация, камера).
498. **iframe.load** — событие загрузки.

## Cookies и Storage
499. **document.cookie** — чтение cookies.
500. **document.cookie = 'name=value; path=/'** — установка cookie.
501. **cookie options** — expires, max-age, path, domain, secure, httpOnly, sameSite.
502. **localStorage.setItem(key, value)** — сохранение в LocalStorage.
503. **localStorage.getItem(key)** — чтение из LocalStorage.
504. **localStorage.removeItem(key)** — удаление из LocalStorage.
505. **localStorage.clear()** — очистка LocalStorage.
506. **localStorage.length** — количество записей.
507. **sessionStorage** — аналогично, но на сессию.
508. **StorageEvent** — событие изменения Storage.

## IndexedDB
509. **indexedDB.open(name, version)** — открытие БД.
510. **db.createObjectStore(name, options)** — создание хранилища.
511. **store.add(value, key)** — добавление записи.
512. **store.put(value, key)** — обновление/добавление записи.
513. **store.delete(key)** — удаление записи.
514. **store.clear()** — очистка хранилища.
515. **store.get(key)** — получение записи.
516. **store.getAll()** — получение всех записей.
517. **transaction** — транзакция для операций.
518. **index** — индекс для поиска.
519. **cursor** — курсор для перебора.

## File API
520. **input.files** — список файлов (FileList).
521. **File** — объект файла (name, size, type, lastModified).
522. **FileReader** — чтение файлов (readAsText, readAsDataURL, readAsArrayBuffer).
523. **reader.onload** — событие загрузки.
524. **reader.onerror** — событие ошибки.
525. **Blob** — бинарные данные.
526. **blob.slice(start, end, type)** — извлечение части.
527. **URL.createObjectURL(blob)** — создание URL для блоба.
528. **URL.revokeObjectURL(url)** — освобождение URL.

## Drag and Drop
529. **dragstart** — начало перетаскивания.
530. **dragenter** — вход в область дропа.
531. **dragover** — движение над областью.
532. **dragleave** — выход из области.
533. **drop** — сброс.
534. **dragend** — конец перетаскивания.
535. **dataTransfer.setData(format, data)** — установка данных.
536. **dataTransfer.getData(format)** — получение данных.
537. **dataTransfer.effectAllowed** — разрешённые эффекты (copy, move, link).
538. **dataTransfer.dropEffect** — эффект сброса.

## Clipboard API
539. **navigator.clipboard.writeText(text)** — запись текста в буфер.
540. **navigator.clipboard.readText()** — чтение текста из буфера.
541. **navigator.clipboard.write(data)** — запись произвольных данных.
542. **navigator.clipboard.read()** — чтение произвольных данных.
543. **clipboard-item** — объект для clipboard (types, getType).
544. **permissions** — запрос разрешений для буфера.

## Fullscreen API
545. **element.requestFullscreen()** — вход в полноэкранный режим.
546. **document.exitFullscreen()** — выход из полноэкранного режима.
547. **document.fullscreenElement** — элемент в полноэкранном режиме.
548. **document.fullscreenEnabled** — доступен ли полноэкранный режим.
549. **fullscreenchange** — событие изменения режима.
550. **fullscreenerror** — ошибка входа в режим.

## Battery API
551. **navigator.getBattery()** — получение информации о батарее.
552. **battery.level** — уровень заряда (0-1).
553. **battery.charging** — заряжается ли.
554. **battery.chargingTime** — время до полной зарядки.
555. **battery.dischargingTime** — время до разрядки.
556. **battery.onlevelchange** — изменение уровня.
557. **battery.onchargingchange** — изменение состояния зарядки.

## Geolocation API
558. **navigator.geolocation.getCurrentPosition(success, error, options)** — текущее положение.
559. **navigator.geolocation.watchPosition(success, error, options)** — постоянное отслеживание.
560. **navigator.geolocation.clearWatch(id)** — остановка отслеживания.
561. **position.coords.latitude** — широта.
562. **position.coords.longitude** — долгота.
563. **position.coords.accuracy** — точность.
564. **position.coords.altitude** — высота.
565. **position.coords.speed** — скорость.
566. **position.coords.heading** — направление.

## Media Devices
567. **navigator.mediaDevices.getUserMedia(constraints)** — доступ к камере/микрофону.
568. **navigator.mediaDevices.enumerateDevices()** — список устройств.
569. **navigator.mediaDevices.getDisplayMedia()** — захват экрана.
570. **MediaStream** — поток медиаданных.
571. **mediaStream.getTracks()** — список дорожек.
572. **mediaTrack.stop()** — остановка дорожки.

## Web Audio API
573. **AudioContext** — контекст аудио.
574. **context.createOscillator()** — создание осциллятора.
575. **context.createGain()** — создание регулятора громкости.
576. **context.createBufferSource()** — источник из буфера.
577. **oscillator.connect(gainNode)** — соединение узлов.
578. **gainNode.connect(context.destination)** — подключение к выходу.
579. **oscillator.start()** — начало звука.
580. **oscillator.stop()** — остановка звука.
581. **context.decodeAudioData(buffer)** — декодирование аудио.

## Web Speech API
582. **SpeechRecognition** — распознавание речи.
583. **recognition.start()** — начало распознавания.
584. **recognition.stop()** — остановка распознавания.
585. **recognition.onresult** — событие результата.
586. **recognition.onerror** — событие ошибки.
587. **SpeechSynthesis** — синтез речи.
588. **speechSynthesis.speak(utterance)** — произнесение.
589. **speechSynthesis.cancel()** — отмена речи.
590. **SpeechSynthesisUtterance** — объект сообщения.

## Canvas API
591. **canvas.getContext('2d')** — получение контекста.
592. **canvas.getContext('webgl')** — контекст WebGL.
593. **context.fillRect(x, y, w, h)** — закрашенный прямоугольник.
594. **context.strokeRect(x, y, w, h)** — контур прямоугольника.
595. **context.clearRect(x, y, w, h)** — очистка области.
596. **context.fillStyle** — цвет заливки.
597. **context.strokeStyle** — цвет контура.
598. **context.lineWidth** — ширина линии.
599. **context.beginPath()** — начало пути.
600. **context.moveTo(x, y)** — перемещение.
601. **context.lineTo(x, y)** — линия к точке.
602. **context.arc(x, y, r, startAngle, endAngle)** — дуга.
603. **context.fill()** — заливка фигуры.
604. **context.stroke()** — обводка фигуры.
605. **context.drawImage(image, x, y)** — отрисовка изображения.
606. **context.putImageData(data, x, y)** — отрисовка пикселей.
607. **context.getImageData(x, y, w, h)** — получение пикселей.
608. **context.transform(a, b, c, d, e, f)** — матрица трансформации.
609. **context.rotate(angle)** — поворот.
610. **context.scale(x, y)** — масштабирование.
611. **context.translate(x, y)** — смещение.
612. **canvas.toDataURL(type, quality)** — сохранение в URL.
613. **canvas.toBlob(callback, type, quality)** — сохранение в Blob.

## RequestAnimationFrame
614. **requestAnimationFrame(callback)** — запрос анимации.
615. **cancelAnimationFrame(id)** — отмена анимации.
616. **callback(timestamp)** — функция с меткой времени.
617. **frame rate** — синхронизация с частотой обновления экрана.
618. **Задержка** — автоматическая оптимизация.

## IntersectionObserver (подробно)
619. **observer.observe(el)** — наблюдение за элементом.
620. **observer.unobserve(el)** — остановка наблюдения.
621. **observer.disconnect()** — остановка всех наблюдений.
622. **options.root** — контейнер (по умолчанию viewport).
623. **options.rootMargin** — отступы ('10px 20px').
624. **options.threshold** — порог видимости (0-1) или массив.
625. **entry.boundingClientRect** — размеры элемента.
626. **entry.rootBounds** — размеры контейнера.
627. **entry.intersectionRect** — пересечение с контейнером.
628. **entry.isIntersecting** — видим ли элемент.
629. **entry.intersectionRatio** — доля видимости (0-1).
630. **entry.target** — наблюдаемый элемент.

## ResizeObserver (подробно)
631. **entry.contentRect** — размер содержимого.
632. **entry.borderBoxSize** — размер с border.
633. **entry.contentBoxSize** — размер с padding.
634. **entry.devicePixelContentBoxSize** — размер с учётом DPR.

## MutationObserver (подробно)
635. **entry.addedNodes** — добавленные узлы.
636. **entry.removedNodes** — удалённые узлы.
637. **entry.attributeName** — изменённый атрибут.
638. **entry.oldValue** — старое значение.
639. **entry.nextSibling** — следующий сосед.
640. **entry.previousSibling** — предыдущий сосед.

## Performance API
641. **performance.now()** — высокоточное время.
642. **performance.mark(name)** — установка метки.
643. **performance.measure(name, startMark, endMark)** — измерение.
644. **performance.getEntries()** — все записи.
645. **performance.getEntriesByName(name)** — записи по имени.
646. **performance.getEntriesByType(type)** — записи по типу.
647. **performance.clearMarks(name)** — очистка меток.
648. **performance.clearMeasures(name)** — очистка измерений.
649. **performance.memory** — память (Chrome).
650. **performance.timing** — времена загрузки (устаревший, используйте Navigation Timing 2).
651. **performance.navigation** — информация о навигации (устаревший).

## User Timing API
652. **performance.mark(name)** — отметка времени.
653. **performance.measure(name, startMark, endMark)** — измерение времени.
654. **performance.clearMarks()** — очистка всех меток.
655. **performance.clearMeasures()** — очистка всех измерений.

## Navigation Timing API (Level 2)
656. **performance.getEntriesByType('navigation')[0]** — информация о навигации.
657. **entry.domComplete** — DOM готов.
658. **entry.domInteractive** — DOM интерактивен.
659. **entry.loadEventStart** — начало load.
660. **entry.loadEventEnd** — конец load.
661. **entry.fetchStart** — начало запроса.
662. **entry.domainLookupStart** — начало DNS.
663. **entry.domainLookupEnd** — конец DNS.
664. **entry.connectStart** — начало соединения.
665. **entry.connectEnd** — конец соединения.
666. **entry.requestStart** — начало запроса.
667. **entry.responseStart** — начало ответа.
668. **entry.responseEnd** — конец ответа.
669. **entry.domContentLoadedEventStart** — начало DOMContentLoaded.
670. **entry.domContentLoadedEventEnd** — конец DOMContentLoaded.

## Resource Timing API
671. **performance.getEntriesByType('resource')** — ресурсы.
672. **entry.name** — URL ресурса.
673. **entry.initiatorType** — тип ('script', 'img', 'css').
674. **entry.duration** — время загрузки.
675. **entry.transferSize** — размер переданных данных.
676. **entry.encodedBodySize** — размер тела (сжатого).
677. **entry.decodedBodySize** — размер тела (распакованного).
678. **entry.nextHopProtocol** — протокол (h2, h3).

## Paint Timing API
679. **performance.getEntriesByType('paint')** — метки отрисовки.
680. **entry.name === 'first-paint'** — первая отрисовка.
681. **entry.name === 'first-contentful-paint'** — первая содержательная отрисовка.

## Web Animations API
682. **element.animate(keyframes, options)** — создание анимации.
683. **animation.play()** — воспроизведение.
684. **animation.pause()** — пауза.
685. **animation.cancel()** — отмена.
686. **animation.finish()** — завершение.
687. **animation.onfinish** — событие завершения.
688. **animation.oncancel** — событие отмены.
689. **animation.currentTime** — текущее время.
690. **animation.playbackRate** — скорость воспроизведения.
691. **animation.effect** — эффект анимации.

## CSS Object Model (CSSOM)
692. **document.styleSheets** — коллекция CSS-таблиц.
693. **styleSheet.cssRules** — правила CSS.
694. **styleSheet.insertRule(rule, index)** — вставка правила.
695. **styleSheet.deleteRule(index)** — удаление правила.
696. **cssRule.cssText** — текст правила.
697. **cssRule.selectorText** — селектор.
698. **cssRule.style** — объект стилей.
699. **window.getComputedStyle(element)** — вычисленные стили.
700. **getComputedStyle(element).getPropertyValue('color')** — значение свойства.

## DOMParser и XML
701. **new DOMParser().parseFromString(html, 'text/html')** — парсинг HTML.
702. **new DOMParser().parseFromString(xml, 'text/xml')** — парсинг XML.
703. **new DOMParser().parseFromString(svg, 'image/svg+xml')** — парсинг SVG.
704. **XMLSerializer().serializeToString(node)** — сериализация в строку.

## URL API
705. **new URL(url, base)** — создание URL объекта.
706. **url.href** — полный URL.
707. **url.protocol** — протокол.
708. **url.host** — хост.
709. **url.hostname** — имя хоста.
710. **url.port** — порт.
711. **url.pathname** — путь.
712. **url.search** — строка запроса.
713. **url.hash** — хэш.
714. **url.searchParams** — объект URLSearchParams.
715. **url.origin** — происхождение.
716. **url.username** — имя пользователя.
717. **url.password** — пароль.
718. **URLSearchParams** — работа с параметрами.
719. **params.get(name)** — получение параметра.
720. **params.set(name, value)** — установка параметра.
721. **params.append(name, value)** — добавление параметра.
722. **params.delete(name)** — удаление параметра.
723. **params.has(name)** — проверка наличия.
724. **params.toString()** — строка запроса.
725. **params.forEach(callback)** — итерация.

## Fetch API
726. **fetch(url, options)** — сетевой запрос.
727. **options.method** — метод (GET, POST, PUT, DELETE).
728. **options.headers** — заголовки.
729. **options.body** — тело запроса.
730. **options.mode** — режим (cors, no-cors, same-origin).
731. **options.credentials** — учётные данные (include, same-origin, omit).
732. **options.cache** — кэширование.
733. **options.redirect** — редиректы.
734. **options.referrer** — referrer.
735. **options.signal** — AbortSignal.
736. **options.keepalive** — сохранение после ухода со страницы.
737. **response.ok** — статус 200-299.
738. **response.status** — код статуса.
739. **response.statusText** — текст статуса.
740. **response.headers** — заголовки ответа.
741. **response.json()** — парсинг JSON.
742. **response.text()** — парсинг текста.
743. **response.blob()** — парсинг Blob.
744. **response.arrayBuffer()** — парсинг ArrayBuffer.
745. **response.formData()** — парсинг FormData.

## WebSocket
746. **new WebSocket(url, protocols)** — создание соединения.
747. **socket.onopen** — событие открытия.
748. **socket.onmessage** — событие сообщения.
749. **socket.onerror** — событие ошибки.
750. **socket.onclose** — событие закрытия.
751. **socket.send(data)** — отправка данных.
752. **socket.close(code, reason)** — закрытие соединения.
753. **socket.readyState** — состояние (0=CONNECTING, 1=OPEN, 2=CLOSING, 3=CLOSED).
754. **socket.bufferedAmount** — количество буферизированных данных.

## EventSource (Server-Sent Events)
755. **new EventSource(url)** — создание соединения.
756. **source.onopen** — событие открытия.
757. **source.onmessage** — событие сообщения.
758. **source.onerror** — событие ошибки.
759. **source.close()** — закрытие соединения.
760. **source.readyState** — состояние (0=CONNECTING, 1=OPEN, 2=CLOSED).

## Notifications API
761. **Notification.requestPermission()** — запрос разрешения.
762. **new Notification(title, options)** — создание уведомления.
763. **notification.onclick** — клик по уведомлению.
764. **notification.onclose** — закрытие уведомления.
765. **notification.onerror** — ошибка уведомления.

## Payment Request API
766. **new PaymentRequest(methods, details, options)** — создание платежа.
767. **request.show()** — показ платёжного интерфейса.
768. **request.abort()** — отмена платежа.
769. **request.onpaymentmethodchange** — изменение метода оплаты.

## Screen Orientation
770. **screen.orientation** — объект ориентации.
771. **screen.orientation.lock(type)** — блокировка ориентации.
772. **screen.orientation.unlock()** — разблокировка.
773. **screen.orientation.type** — тип ('portrait-primary', 'landscape-primary').
774. **orientationchange** — событие изменения ориентации.

## Vibration API
775. **navigator.vibrate(pattern)** — вибрация устройства.
776. **navigator.vibrate(0)** — остановка вибрации.
777. **pattern** — массив длительностей (вкл/выкл).

## Network Information API
778. **navigator.connection** — объект информации о сети.
779. **connection.downlink** — скорость загрузки.
780. **connection.effectiveType** — тип ('slow-2g', '2g', '3g', '4g').
781. **connection.saveData** — режим экономии данных.
782. **connection.rtt** — время задержки (RTT).

## Permission API
783. **navigator.permissions.query(options)** — запрос разрешения.
784. **permission.state** — состояние ('granted', 'denied', 'prompt').
785. **permission.onchange** — событие изменения состояния.

## Storage API
786. **navigator.storage.estimate()** — оценка использования хранилища.
787. **navigator.storage.persist()** — запрос на постоянное хранилище.
788. **navigator.storage.persisted()** — является ли хранилище постоянным.

## Content Security Policy (CSP)
789. **meta http-equiv="Content-Security-Policy"** — политика в HTML.
790. **csp-violation** — событие нарушения CSP.
791. **securitypolicyviolation** — объект нарушения.
792. **violation.blockedURI** — заблокированный URI.
793. **violation.violatedDirective** — нарушенная директива.

## Trusted Types
794. **trustedTypes** — защита от XSS через типизацию.
795. **trustedTypes.createPolicy(name, rules)** — создание политики.
796. **trustedTypes.isHTML** — проверка TrustedHTML.
797. **trustedTypes.isScript** — проверка TrustedScript.
798. **trustedTypes.isScriptURL** — проверка TrustedScriptURL.

## Sanitizer API
799. **new Sanitizer()** — создание санитайзера.
800. **sanitizer.sanitizeFor(element, html)** — очистка HTML.
801. **sanitizer.sanitize(html)** — очистка (без контекста).

## DOMError
802. **DOMError** — объект ошибки DOM.
803. **error.name** — имя ошибки.
804. **error.message** — сообщение.

## DOMException
805. **DOMException** — исключение DOM.
806. **exception.code** — код ошибки.
807. **exception.name** — имя (NotFoundError, TypeError).

## DOMStringList
808. **DOMStringList** — список строк.
809. **list.item(index)** — строка по индексу.
810. **list.contains(string)** — проверка наличия.

## HTMLCollection методы
811. **collection.namedItem(name)** — элемент по имени.
812. **collection.item(index)** — элемент по индексу.
813. **collection.length** — количество элементов.

## NodeList методы
814. **nodeList.forEach(callback)** — итерация.
815. **nodeList.item(index)** — узел по индексу.
816. **nodeList.keys()** — итератор индексов.
817. **nodeList.values()** — итератор значений.
818. **nodeList.entries()** — итератор пар.

## DOMTokenList (дополнительно)
819. **tokenList.supports(token)** — поддержка токена.
820. **tokenList.value** — строка значений.
821. **tokenList.length** — количество токенов.
822. **tokenList.forEach(callback)** — итерация.

## Настройки браузера
823. **window.matchMedia(mediaQuery)** — проверка медиа-запроса.
824. **matchMedia.addEventListener('change', callback)** — слушатель изменений.
825. **window.devicePixelRatio** — коэффициент пикселей.
826. **window.screen.orientation** — ориентация экрана.

## Адаптивность и Media Queries
827. **window.matchMedia('(max-width: 600px)')** — проверка ширины.
828. **window.matchMedia('(prefers-color-scheme: dark)')** — тёмная тема.
829. **window.matchMedia('(prefers-reduced-motion: reduce)')** — уменьшение анимации.
830. **window.matchMedia('(orientation: portrait)')** — ориентация.

## Инспекция и отладка DOM
831. **console.log(element)** — вывод элемента.
832. **console.dir(element)** — вывод свойств элемента.
833. **console.table(collection)** — вывод таблицы.
834. **inspect(element)** — переход в Elements.
835. **$0** — выбранный элемент в DevTools.
836. **$('selector')** — выбор элемента в консоли.
837. **$$('selector')** — выбор всех элементов в консоли.
838. **debugger** — точка останова.

## Безопасность DOM
839. **CSP** — защита от XSS.
840. **Sanitization** — очистка HTML (DOMPurify, sanitize-html).
841. **TrustedHTML** — безопасные HTML-строки.
842. **Строгий режим** — защита от ошибок.
843. **Еслиrame sandbox** — изоляция.
844. **Same-origin policy** — защита от кросс-домена.

## Советы по производительности DOM
845. **Batch DOM updates** — группировка изменений.
846. **DocumentFragment** — для batch-вставки.
847. **Use textContent вместо innerHTML** — быстрее и безопаснее.
848. **Avoid layout thrashing** — чтение и запись по отдельности.
849. **Debounce/Throttle** — ограничение частоты событий.
850. **Virtual DOM** — React, Vue.
851. **Lazy loading** — отложенная загрузка.
852. **IntersectionObserver** — для lazy loading.
853. **ResizeObserver** — для адаптивности.
854. **requestAnimationFrame** — синхронизация с рендерингом.
855. **OffscreenCanvas** — отрисовка в фоне.

## События и дебаггинг
856. **event.preventDefault()** — отмена поведения.
857. **event.stopPropagation()** — остановка всплытия.
858. **event.stopImmediatePropagation()** — остановка всех слушателей.
859. **event.isTrusted** — пользовательское или программное.
860. **event.composed** — проходит через Shadow DOM.
861. **event.target vs event.currentTarget** — цель vs слушатель.
862. **event.eventPhase** — фаза (1=capture, 2=target, 3=bubble).

## Вспомогательные методы
863. **element.scrollIntoView({ behavior: 'smooth' })** — плавная прокрутка.
864. **element.focus()** — фокус на элементе.
865. **element.blur()** — потеря фокуса.
866. **element.click()** — программный клик.
867. **element.submit()** — отправка формы.
868. **element.reset()** — сброс формы.
869. **element.select()** — выделение текста.
870. **element.setSelectionRange(start, end)** — выделение диапазона.
871. **element.contains(node)** — проверка вхождения.
872. **element.compareDocumentPosition(node)** — сравнение позиции.
873. **element.isEqualNode(node)** — глубокое сравнение узлов.
874. **element.isSameNode(node)** — сравнение ссылок.
875. **element.getRootNode()** — корневой узел (документ или shadow root).
876. **element.normalize()** — объединение текстовых узлов.
877. **element.replaceChildren(...nodes)** — замена всех детей.
878. **element.after(...nodes)** — вставка после.
879. **element.before(...nodes)** — вставка перед.
880. **element.append(...nodes)** — вставка в конец.
881. **element.prepend(...nodes)** — вставка в начало.
882. **element.replaceWith(...nodes)** — замена элемента.
883. **element.remove()** — удаление элемента.

## Еслиrame взаимодействие
884. **iframe.contentWindow** — window внутри iframe.
885. **iframe.contentDocument** — document внутри iframe.
886. **window.parent** — родительское окно.
887. **window.top** — самое верхнее окно.
888. **window.frameElement** — элемент iframe (изнутри).
889. **window.opener** — окно, открывшее текущее.
890. **postMessage** — обмен данными с iframe.
891. **message** — событие получения сообщения.

## Web Messaging
892. **window.postMessage(data, targetOrigin)** — отправка сообщения.
893. **message event** — приём сообщения.
894. **event.data** — данные сообщения.
895. **event.origin** — происхождение отправителя.
896. **event.source** — источник (window).

## Broadcast Channel API
897. **new BroadcastChannel(channelName)** — создание канала.
898. **channel.postMessage(data)** — отправка сообщения.
899. **channel.onmessage** — приём сообщения.
900. **channel.close()** — закрытие канала.

## Работа с медиа
901. **audio.play()** — воспроизведение.
902. **audio.pause()** — пауза.
903. **audio.volume** — громкость (0-1).
904. **audio.currentTime** — текущее время.
905. **audio.duration** — длительность.
906. **video.requestPictureInPicture()** — режим "картинка в картинке".
907. **video.getVideoPlaybackQuality()** — статистика воспроизведения.

## WebRTC
908. **RTCPeerConnection** — соединение для медиа.
909. **RTCDataChannel** — канал данных.
910. **getUserMedia** — доступ к устройствам.
911. **getDisplayMedia** — захват экрана.
912. **createOffer** — создание SDP-оферты.
913. **createAnswer** — создание SDP-ответа.
914. **setLocalDescription** — установка локального SDP.
915. **setRemoteDescription** — установка удалённого SDP.
916. **addIceCandidate** — добавление ICE-кандидата.

## Web Crypto API
917. **crypto.randomUUID()** — генерация UUID.
918. **crypto.randomBytes(n)** — генерация случайных байтов (Node.js).
919. **crypto.subtle** — криптографические операции.
920. **subtle.digest(algorithm, data)** — хэширование.
921. **subtle.encrypt(algorithm, key, data)** — шифрование.
922. **subtle.decrypt(algorithm, key, data)** — дешифрование.
923. **subtle.generateKey(algorithm, extractable, keyUsages)** — генерация ключа.
924. **subtle.importKey(format, keyData, algorithm, extractable, keyUsages)** — импорт ключа.
925. **subtle.exportKey(format, key)** — экспорт ключа.
926. **subtle.sign(algorithm, key, data)** — подпись.
927. **subtle.verify(algorithm, key, signature, data)** — проверка подписи.

## Web Storage
928. **localStorage** — постоянное хранилище.
929. **sessionStorage** — хранилище на сессию.
930. **storage** — событие изменения хранилища.

## Service Workers
931. **navigator.serviceWorker.register(scriptURL)** — регистрация SW.
932. **navigator.serviceWorker.ready** — Promise готовности.
933. **navigator.serviceWorker.controller** — активный SW.
934. **serviceWorker.onmessage** — получение сообщения.
935. **serviceWorker.postMessage(data)** — отправка сообщения.
936. **fetch event** — перехват запросов.
937. **install event** — установка SW.
938. **activate event** — активация SW.
939. **push event** — получение push-уведомлений.
940. **sync event** — фоновый синхронизация.
941. **Cache API** — кэширование запросов.
942. **cache.match(request)** — поиск в кэше.
943. **cache.put(request, response)** — добавление в кэш.
944. **cache.delete(request)** — удаление из кэша.
945. **cache.keys()** — список ключей.
946. **caches.open(cacheName)** — открытие кэша.
947. **caches.delete(cacheName)** — удаление кэша.
948. **caches.has(cacheName)** — проверка наличия кэша.

## Push API
949. **pushManager.subscribe(options)** — подписка на push.
950. **pushManager.getSubscription()** — получение подписки.
951. **pushManager.unsubscribe()** — отписка от push.
952. **pushManager.permissionState()** — состояние разрешения.

## Cache API
953. **Cache** — объект кэша.
954. **cache.match(request)** — поиск.
955. **cache.matchAll(request, options)** — поиск всех.
956. **cache.add(request)** — добавление.
957. **cache.addAll(requests)** — добавление всех.
958. **cache.put(request, response)** — сохранение.
959. **cache.delete(request, options)** — удаление.
960. **cache.keys()** — список ключей.

## Payment Request
961. **PaymentRequest** — запрос платежа.
962. **PaymentResponse** — ответ платежа.
963. **paymentResponse.complete(status)** — завершение платежа.
964. **paymentResponse.details** — детали платежа.
965. **paymentResponse.methodName** — метод оплаты.

## Web Share API
966. **navigator.share(data)** — открытие системного шеринга.
967. **navigator.canShare(data)** — проверка возможности шеринга.
968. **data.title** — заголовок.
969. **data.text** — текст.
970. **data.url** — URL.

## Credential Management API
971. **navigator.credentials.get(options)** — получение учётных данных.
972. **navigator.credentials.store(credential)** — сохранение.
973. **navigator.credentials.create(options)** — создание учётных данных.
974. **navigator.credentials.preventSilentAccess()** — отключение бесшумного доступа.

## Payment Handler API
975. **PaymentHandler** — обработка платежей.
976. **canMakePayment()** — возможность оплаты.

## Contact Picker API
977. **navigator.contacts.select(properties, options)** — выбор контактов.

## WebAuthn (Web Authentication)
978. **navigator.credentials.get({ publicKey: ... })** — аутентификация.
979. **navigator.credentials.create({ publicKey: ... })** — регистрация.
980. **PublicKeyCredential** — объект учётных данных.

## Virtual Keyboard API
981. **navigator.virtualKeyboard** — управление виртуальной клавиатурой.
982. **virtualKeyboard.show()** — показать клавиатуру.
983. **virtualKeyboard.hide()** — скрыть клавиатуру.
984. **virtualKeyboard.overlaysContent** — перекрывает контент.

## Device Orientation API
985. **window.ondeviceorientation** — событие ориентации.
986. **event.alpha** — поворот вокруг Z (0-360).
987. **event.beta** — наклон вперёд/назад (-180 - 180).
988. **event.gamma** — наклон влево/вправо (-90 - 90).

## Device Motion API
989. **window.ondevicemotion** — событие движения.
990. **event.acceleration** — ускорение (x, y, z).
991. **event.accelerationIncludingGravity** — ускорение с гравитацией.
992. **event.rotationRate** — скорость вращения (alpha, beta, gamma).

## Ambient Light Sensor
993. **new AmbientLightSensor()** — датчик освещённости.
994. **sensor.reading** — событие чтения.
995. **sensor.illuminance** — уровень освещённости (lux).

## Proximity Sensor
996. **new ProximitySensor()** — датчик приближения.
997. **sensor.distance** — расстояние до объекта.
998. **sensor.near** — близко ли объект.

## Accelerometer / Gyroscope
999. **Accelerometer** — акселерометр.
1000. **Gyroscope** — гироскоп.
1001. **Magnetometer** — магнитометр.
1002. **OrientationSensor** — датчик ориентации.

## Battery Status
1003. **navigator.getBattery()** — информация о батарее.

## Дополнительные API
1004. **PerformanceObserver** — наблюдение за производительностью.
1005. **ReportingObserver** — наблюдение за отчётами.
1006. **ResizeObserver** — наблюдение за изменением размера.
1007. **MutationObserver** — наблюдение за изменением DOM.
1008. **IntersectionObserver** — наблюдение за видимостью.
1009. **PerformanceObserver** — наблюдение за производительностью.
1010. **ReportingObserver** — наблюдение за отчётами.
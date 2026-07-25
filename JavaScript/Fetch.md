# Весь Fetch API в JavaScript

## Базовые понятия
1. **Fetch API** — современный интерфейс для выполнения сетевых запросов (замена XMLHttpRequest).
2. **fetch(url, options)** — глобальная функция для отправки запросов. Возвращает Promise.
3. **Response** — объект ответа на запрос.
4. **Request** — объект запроса (создаётся автоматически или вручную).
5. **Headers** — объект для работы с заголовками.
6. **Body** — тело запроса или ответа (данные).
7. **AbortController** — управление отменой запросов.
8. **CORS** — политика кросс-доменных запросов.

## Основной синтаксис
9. **fetch(url)** — GET-запрос по умолчанию.
10. **fetch(url, { method: 'POST' })** — POST-запрос.
11. **fetch(url, { headers: { 'Content-Type': 'application/json' } })** — с заголовками.
12. **fetch(url, { body: JSON.stringify(data) })** — с телом запроса.
13. **fetch(url, { credentials: 'include' })** — с отправкой cookies.
14. **fetch(url, { mode: 'cors' })** — CORS-режим.
15. **fetch(url, { cache: 'no-cache' })** — управление кэшированием.
16. **fetch(url, { redirect: 'follow' })** — управление редиректами.
17. **fetch(url, { signal: controller.signal })** — с сигналом отмены.
18. **fetch(url, { keepalive: true })** — запрос после ухода со страницы.

## Параметры fetch (options)
19. **method** — HTTP-метод ('GET', 'POST', 'PUT', 'DELETE', 'PATCH', 'HEAD', 'OPTIONS').
20. **headers** — объект или Headers с заголовками.
21. **body** — тело запроса (string, FormData, Blob, ArrayBuffer, URLSearchParams).
22. **mode** — режим ('cors', 'no-cors', 'same-origin').
23. **credentials** — учетные данные ('omit', 'same-origin', 'include').
24. **cache** — кэширование ('default', 'no-store', 'reload', 'no-cache', 'force-cache', 'only-if-cached').
25. **redirect** — редиректы ('follow', 'error', 'manual').
26. **referrer** — referrer ('no-referrer', 'client', или URL).
27. **referrerPolicy** — политика referrer.
28. **integrity** — проверка целостности (SRI).
29. **keepalive** — выполнение после ухода со страницы.
30. **signal** — AbortSignal для отмены.
31. **window** — (устаревший) контекст окна.

## HTTP-методы
32. **GET** — получение данных.
33. **POST** — создание ресурса.
34. **PUT** — полное обновление ресурса.
35. **PATCH** — частичное обновление ресурса.
36. **DELETE** — удаление ресурса.
37. **HEAD** — получение только заголовков.
38. **OPTIONS** — получение информации о сервере.

## Обработка ответа (Response)
39. **response.ok** — статус в диапазоне 200-299 (boolean).
40. **response.status** — числовой код статуса (200, 404, 500).
41. **response.statusText** — текст статуса ('OK', 'Not Found').
42. **response.headers** — объект Headers с заголовками.
43. **response.url** — URL ответа (с учётом редиректов).
44. **response.redirected** — был ли редирект.
45. **response.type** — тип ответа ('basic', 'cors', 'opaque', 'opaqueredirect').
46. **response.body** — ReadableStream для чтения потока данных.

## Методы Response для чтения тела
47. **response.json()** — парсинг тела как JSON.
48. **response.text()** — парсинг тела как текст.
49. **response.blob()** — парсинг тела как Blob.
50. **response.arrayBuffer()** — парсинг тела как ArrayBuffer.
51. **response.formData()** — парсинг тела как FormData.
52. **response.clone()** — клонирование ответа (для многократного чтения).
53. **response.bodyUsed** — было ли тело прочитано (boolean).

## Объект Headers
54. **new Headers(init)** — создание объекта заголовков.
55. **headers.set(name, value)** — установка заголовка.
56. **headers.append(name, value)** — добавление значения к заголовку.
57. **headers.get(name)** — получение значения заголовка.
58. **headers.getAll(name)** — все значения заголовка.
59. **headers.has(name)** — проверка наличия заголовка.
60. **headers.delete(name)** — удаление заголовка.
61. **headers.forEach(callback)** — итерация по заголовкам.
62. **headers.keys()** — итератор по именам заголовков.
63. **headers.values()** — итератор по значениям заголовков.
64. **headers.entries()** — итератор по парам [имя, значение].
65. **headers[Symbol.iterator]** — итератор по парам.

## Объект Request
66. **new Request(url, options)** — создание объекта запроса.
67. **request.method** — HTTP-метод.
68. **request.url** — URL запроса.
69. **request.headers** — заголовки.
70. **request.body** — тело запроса.
71. **request.mode** — режим.
72. **request.credentials** — учетные данные.
73. **request.cache** — кэширование.
74. **request.redirect** — редиректы.
75. **request.referrer** — referrer.
76. **request.referrerPolicy** — политика referrer.
77. **request.integrity** — целостность.
78. **request.keepalive** — keepalive.
79. **request.signal** — AbortSignal.
80. **request.clone()** — клонирование запроса.

## Объект AbortController
81. **new AbortController()** — создание контроллера.
82. **controller.signal** — сигнал для передачи в fetch.
83. **controller.abort()** — отмена запроса.
84. **controller.abort(reason)** — отмена с причиной.
85. **signal.aborted** — отменён ли запрос.
86. **signal.reason** — причина отмены.
87. **signal.throwIfAborted()** — выбрасывает ошибку, если отменён.
88. **signal.addEventListener('abort', handler)** — слушатель отмены.
89. **signal.removeEventListener('abort', handler)** — удаление слушателя.

## Ошибки и обработка
90. **Network error** — ошибка сети (нет интернета, DNS).
91. **AbortError** — ошибка отмены запроса.
92. **TypeError** — ошибка типа (невалидный URL).
93. **Ошибка парсинга JSON** — невалидный JSON в ответе.
94. **try...catch** — перехват ошибок fetch.
95. **catch(error)** — обработка ошибок в цепочке Promise.
96. **error.message** — сообщение об ошибке.
97. **error.name** — имя ошибки ('AbortError', 'TypeError').
98. **error.cause** — причина ошибки (опционально).

## Заголовки (Headers) — стандартные
99. **Content-Type** — тип содержимого ('application/json', 'text/plain', 'multipart/form-data').
100. **Content-Length** — длина тела.
101. **Authorization** — авторизация ('Bearer token', 'Basic ...').
102. **Accept** — принимаемый тип ('application/json').
103. **Accept-Encoding** — кодировка ('gzip', 'deflate', 'br').
104. **Accept-Language** — язык ('ru-RU', 'en-US').
105. **Cache-Control** — кэширование ('no-cache', 'max-age=3600').
106. **Cookie** — отправка cookies (через credentials).
107. **Set-Cookie** — установка cookies (в ответе).
108. **User-Agent** — информация о клиенте.
109. **Referer** — источник запроса.
110. **Origin** — происхождение запроса.
111. **Host** — хост сервера.
112. **Connection** — управление соединением ('keep-alive').
113. **X-Requested-With** — идентификация AJAX ('XMLHttpRequest').

## Типы тел запроса
114. **JSON** — `JSON.stringify(data)`.
115. **FormData** — данные формы (`new FormData(form)`).
116. **URLSearchParams** — параметры URL (`new URLSearchParams(params)`).
117. **Blob** — бинарные данные (`new Blob([data])`).
118. **ArrayBuffer** — бинарный буфер.
119. **ReadableStream** — поток данных.
120. **String** — обычный текст.

## Обработка JSON
121. **fetch(url).then(res => res.json())** — получение JSON.
122. **fetch(url, { body: JSON.stringify(data) })** — отправка JSON.
123. **headers: { 'Content-Type': 'application/json' }** — указание типа.
124. **headers: { 'Accept': 'application/json' }** — ожидание JSON.
125. **res.json().catch(() => null)** — защита от ошибки парсинга.

## Обработка FormData
126. **new FormData()** — создание FormData.
127. **formData.append(name, value)** — добавление поля.
128. **formData.append(name, file, filename)** — добавление файла.
129. **formData.delete(name)** — удаление поля.
130. **formData.get(name)** — получение значения.
131. **formData.getAll(name)** — все значения.
132. **formData.has(name)** — проверка наличия.
133. **formData.set(name, value)** — установка значения.
134. **formData.keys()** — итератор ключей.
135. **formData.values()** — итератор значений.
136. **formData.entries()** — итератор пар.
137. **fetch(url, { method: 'POST', body: formData })** — отправка FormData.

## Обработка URLSearchParams
138. **new URLSearchParams(params)** — создание параметров.
139. **params.append(name, value)** — добавление параметра.
140. **params.delete(name)** — удаление параметра.
141. **params.get(name)** — получение значения.
142. **params.getAll(name)** — все значения.
143. **params.has(name)** — проверка наличия.
144. **params.set(name, value)** — установка значения.
145. **params.toString()** — строка параметров.
146. **params.keys()** — итератор ключей.
147. **params.values()** — итератор значений.
148. **params.entries()** — итератор пар.
149. **fetch(url, { body: params })** — отправка параметров.
150. **Content-Type: 'application/x-www-form-urlencoded'** — тип для параметров.

## Обработка Blob
151. **res.blob()** — получение Blob.
152. **URL.createObjectURL(blob)** — создание URL для Blob.
153. **new Blob([data], { type: 'image/png' })** — создание Blob.
154. **blob.slice(start, end, type)** — извлечение части.
155. **blob.text()** — чтение Blob как текст.
156. **blob.arrayBuffer()** — чтение Blob как ArrayBuffer.
157. **blob.stream()** — поток Blob.
158. **fetch(url, { body: blob })** — отправка Blob.

## Обработка ArrayBuffer
159. **res.arrayBuffer()** — получение ArrayBuffer.
160. **new Uint8Array(buffer)** — преобразование в TypedArray.
161. **new DataView(buffer)** — представление данных.
162. **fetch(url, { body: buffer })** — отправка ArrayBuffer.

## Прогресс загрузки (Download progress)
163. **res.body** — ReadableStream.
164. **res.body.getReader()** — чтение потока.
165. **reader.read()** — чтение чанка (Promise).
166. **reader.cancel()** — отмена чтения.
167. **reader.releaseLock()** — освобождение блокировки.
168. **Пример прогресса** — суммирование длины чанков.
169. **Total length** — из заголовка `Content-Length`.

## Прогресс отправки (Upload progress)
170. **XMLHttpRequest** — единственный способ отслеживать прогресс отправки.
171. **xhr.upload.onprogress** — событие прогресса.
172. **xhr.upload.onload** — завершение загрузки.
173. **xhr.upload.onerror** — ошибка загрузки.

## Таймауты (Timeouts)
174. **AbortController + setTimeout** — отмена по таймауту.
175. **setTimeout(() => controller.abort(), timeout)** — таймаут.
176. **AbortError** — ошибка при таймауте.
177. **Promise.race** — альтернативный способ таймаута.
178. **fetch(url, { signal: AbortSignal.timeout(ms) })** — встроенный таймаут (экспериментальный).

## Повторные попытки (Retry)
179. **Рекурсивный вызов fetch** — повтор при ошибке.
180. **Задержка между попытками** — `setTimeout`.
181. **Экспоненциальная задержка** — `delay * 2 ** attempt`.
182. **Максимальное количество попыток** — ограничение.
183. **Обработка 5xx ошибок** — повторять.
184. **Обработка 429 Too Many Requests** — повтор с задержкой.
185. **retry-after заголовок** — время ожидания.
186. **Библиотеки с retry** — axios-retry, retry-fetch.

## Кэширование (Cache)
187. **cache: 'default'** — стандартное кэширование.
188. **cache: 'no-store'** — не использовать кэш.
189. **cache: 'reload'** — принудительная загрузка.
190. **cache: 'no-cache'** — проверка актуальности.
191. **cache: 'force-cache'** — всегда из кэша (если есть).
192. **cache: 'only-if-cached'** — только из кэша.
193. **Cache-Control заголовок** — управление кэшем на сервере.
194. **Cache API** — ручное кэширование (Service Worker).

## CORS (Cross-Origin Resource Sharing)
195. **mode: 'cors'** — кросс-доменный запрос (по умолчанию).
196. **mode: 'same-origin'** — только с тем же происхождением.
197. **mode: 'no-cors'** — непрозрачный ответ (ограниченный доступ).
198. **credentials: 'include'** — отправка cookies в CORS.
199. **credentials: 'same-origin'** — только с тем же происхождением.
200. **credentials: 'omit'** — не отправлять cookies.
201. **Access-Control-Allow-Origin** — разрешённое происхождение (сервер).
202. **Access-Control-Allow-Credentials** — разрешение cookies.
203. **Access-Control-Allow-Methods** — разрешённые методы.
204. **Access-Control-Allow-Headers** — разрешённые заголовки.
205. **Access-Control-Expose-Headers** — доступные заголовки.
206. **Preflight request** — OPTIONS запрос перед основным.

## Редиректы (Redirects)
207. **redirect: 'follow'** — автоматический редирект (по умолчанию).
208. **redirect: 'error'** — ошибка при редиректе.
209. **redirect: 'manual'** — ручная обработка редиректа.
210. **response.redirected** — был ли редирект.
211. **response.url** — конечный URL.

## Integrity (SRI)
212. **integrity: 'sha256-...'** — проверка целостности.
213. **Subresource Integrity (SRI)** — защита от подмены ресурсов.
214. **Ошибка при несовпадении** — Promise rejected.

## Keepalive
215. **keepalive: true** — выполнение после ухода со страницы.
216. **Использование для аналитики** — отправка данных при закрытии.
217. **unload / beforeunload** — события, где keepalive полезен.
218. **Ограничения** — максимальный размер тела (64KB).

## AbortSignal методы
219. **AbortSignal.abort()** — создание отменённого сигнала.
220. **AbortSignal.abort(reason)** — с причиной.
221. **AbortSignal.timeout(ms)** — сигнал с таймаутом (экспериментальный).
222. **signal.aborted** — boolean отмены.
223. **signal.reason** — причина отмены.
224. **signal.throwIfAborted()** — выброс ошибки.
225. **signal.addEventListener('abort', handler)** — слушатель.
226. **signal.removeEventListener('abort', handler)** — удаление слушателя.

## Fetch в Node.js
227. **Node.js 18+** — встроенный fetch.
228. **node-fetch** — библиотека для старых версий.
229. **undici** — HTTP-клиент Node.js.
230. **global.fetch** — глобальная функция в Node.js.
231. **headers** — поддерживаются стандартные.
232. **abort** — поддерживается.
233. **Response** — аналогично браузеру.
234. **Request** — аналогично браузеру.

## Streams API
235. **ReadableStream** — поток для чтения.
236. **WritableStream** — поток для записи.
237. **TransformStream** — поток для преобразования.
238. **response.body** — ReadableStream ответа.
239. **request.body** — ReadableStream запроса.
240. **stream.getReader()** — получение ридера.
241. **reader.read()** — чтение чанка.
242. **reader.cancel(reason)** — отмена потока.
243. **reader.releaseLock()** — освобождение блокировки.
244. **stream.pipeTo(writable)** — соединение потоков.
245. **stream.pipeThrough(transform)** — преобразование потока.
246. **stream.tee()** — разветвление потока.

## Библиотеки и альтернативы
247. **Axios** — популярный HTTP-клиент (Promise-based).
248. **KY** — маленький fetch-клиент.
249. **ofetch** — универсальный fetch.
250. **unfetch** — минимальный fetch-полифилл.
251. **isomorphic-fetch** — fetch для браузера и Node.js.
252. **cross-fetch** — универсальный fetch.

## Интерцепторы (Interceptors)
253. **Request interceptor** — модификация запроса.
254. **Response interceptor** — модификация ответа.
255. **Axios interceptors** — встроенные.
256. **Ручная реализация** — обёртка над fetch.

## Паттерны и практики
257. **Обработка ошибок** — единый обработчик.
258. **Переиспользование fetch** — фабрика запросов.
259. **Префикс URL** — базовый URL.
260. **Auth токен** — автоматическое добавление в заголовки.
261. **Refresh token** — обновление токена при 401.
262. **Логирование запросов** — для отладки.
263. **Логирование ответов** — для отладки.
264. **Трансформация ответов** — единый формат.
265. **Валидация ответов** — проверка структуры.
266. **Карта ошибок** — обработка по кодам статуса.
267. **Ретраи с логикой** — умные повторные попытки.
268. **Кэширование** — ручное кэширование результатов.

## Тестирование fetch
269. **Jest** — тестирование с моками.
270. **jest-fetch-mock** — мок для fetch.
271. **Mock Service Worker (MSW)** — перехват запросов.
272. **nock** — моки HTTP в Node.js.
273. **sinon** — шпионы и заглушки.
274. **Тестирование ошибок** — сетевые ошибки, 404, 500.
275. **Тестирование таймаутов** — отмена по таймауту.

## Безопасность
276. **CSP** — политика безопасности.
277. **Защита от XSS** — экранирование данных.
278. **Защита от CSRF** — токены и заголовки.
279. **HTTPS** — использование защищённого протокола.
280. **SRI** — проверка целостности.
281. **Credentials** — осторожное использование.
282. **Санкционирование** — проверка авторизации.

## Производительность
283. **Кэширование** — уменьшение запросов.
284. **Сжатие** — Accept-Encoding: gzip, br.
285. **Сокращение размера** — минификация данных.
286. **Пакетная обработка** — группировка запросов.
287. **Параллельные запросы** — Promise.all.
288. **Отмена запросов** — при уходе со страницы.
289. **keepalive** — для аналитики.

## Советы по использованию
290. **Всегда проверяйте response.ok** — обработка ошибок.
291. **Используйте try...catch** — обработка сетевых ошибок.
292. **Указывайте Content-Type** — для корректной обработки.
293. **Клонируйте ответ** — если нужно прочитать несколько раз.
294. **Отменяйте запросы** — при размонтировании компонента.
295. **Используйте AbortController** — для таймаутов.
296. **Не забывайте про CORS** — настройка сервера.
297. **Используйте async/await** — читаемость кода.
298. **Логируйте ошибки** — для отладки.
299. **Не храните секреты в коде** — использовать переменные окружения.
300. **Используйте интерцепторы** — для глобальной обработки.

## Примеры использования
301. **GET запрос** — `fetch('/api/users').then(res => res.json())`.
302. **POST с JSON** — `fetch('/api/users', { method: 'POST', headers: { 'Content-Type': 'application/json' }, body: JSON.stringify(user) })`.
303. **POST с FormData** — `fetch('/api/upload', { method: 'POST', body: formData })`.
304. **Загрузка файла** — `fetch('/api/file').then(res => res.blob())`.
305. **Отмена запроса** — `controller.abort()`.
306. **Таймаут** — `AbortSignal.timeout(5000)`.
307. **Повторные попытки** — рекурсивный fetch с задержкой.
308. **Прогресс загрузки** — через ReadableStream.
309. **Авторизация** — `headers: { 'Authorization': 'Bearer token' }`.
310. **Обновление токена** — перехват 401 и повтор запроса.
311. **Upload с прогрессом** — XMLHttpRequest.
312. **Параллельные запросы** — `Promise.all([fetch(...), fetch(...)])`.
313. **Последовательные запросы** — `await fetch1(); await fetch2();`.
314. **Фабрика запросов** — `const api = (url) => fetch('/api/' + url)`.

## Форматы данных
315. **application/json** — JSON формат.
316. **application/x-www-form-urlencoded** — параметры URL.
317. **multipart/form-data** — данные формы с файлами.
318. **text/plain** — обычный текст.
319. **application/octet-stream** — бинарные данные.
320. **image/png, image/jpeg** — изображения.
321. **application/pdf** — PDF документы.

## Статусы HTTP (часто используемые)
322. **200 OK** — успех.
323. **201 Created** — создано.
324. **202 Accepted** — принято (асинхронно).
325. **204 No Content** — успех, но нет тела.
326. **301 Moved Permanently** — редирект постоянный.
327. **302 Found** — редирект временный.
328. **303 See Other** — перенаправление на GET.
329. **304 Not Modified** — не изменён (кэш).
330. **307 Temporary Redirect** — временный редирект.
331. **308 Permanent Redirect** — постоянный редирект.
332. **400 Bad Request** — неверный запрос.
333. **401 Unauthorized** — не авторизован.
334. **403 Forbidden** — запрещено.
335. **404 Not Found** — не найдено.
336. **405 Method Not Allowed** — неверный метод.
337. **429 Too Many Requests** — слишком много запросов.
338. **500 Internal Server Error** — ошибка сервера.
339. **502 Bad Gateway** — ошибка шлюза.
340. **503 Service Unavailable** — сервис недоступен.
341. **504 Gateway Timeout** — таймаут шлюза.

## Объекты Fetch в деталях
342. **Response.json()** — возвращает Promise с объектом.
343. **Response.text()** — возвращает Promise со строкой.
344. **Response.blob()** — возвращает Promise с Blob.
345. **Response.arrayBuffer()** — возвращает Promise с ArrayBuffer.
346. **Response.formData()** — возвращает Promise с FormData.
347. **Response.clone()** — копия Response.
348. **Request.clone()** — копия Request.
349. **Headers.set()** — перезаписывает заголовок.
350. **Headers.append()** — добавляет значение к заголовку.

## Полифиллы и поддержка
351. **Полифилл для старых браузеров** — `whatwg-fetch`.
352. **Поддержка в IE** — нет нативной, только полифилл.
353. **Поддержка в Node.js** — с 18 версии.
354. **Проверка поддержки** — `typeof fetch === 'function'`.

## Отладка fetch
355. **Chrome DevTools** — вкладка Network.
356. **Firefox DevTools** — вкладка Network.
357. **console.log** — вывод запросов/ответов.
358. **Логгеры** — перехват и логирование.
359. **Интерцепторы** — глобальное логирование.

## Асинхронность и Promise
360. **fetch возвращает Promise** — используется с then/catch.
361. **async/await** — синтаксический сахар.
362. **Promise.all** — параллельные запросы.
363. **Promise.race** — первый завершённый запрос.
364. **Promise.allSettled** — все запросы (независимо от ошибок).
365. **Promise.any** — первый успешный запрос.
366. **await в цикле** — последовательные запросы.
367. **for...of с await** — итерация запросов.

## Расширенные случаи
368. **Streaming ответ** — получение данных частями.
369. **Server-Sent Events (SSE)** — через EventSource.
370. **WebSocket** — для двусторонней связи.
371. **Long polling** — долгие опросы.
372. **GraphQL** — через fetch с POST.
373. **RESTful API** — стандартные CRUD операции.
374. **SOAP** — через fetch с XML.

## Аутентификация
375. **Basic Auth** — `Authorization: Basic base64(login:password)`.
376. **Bearer Token** — `Authorization: Bearer token`.
377. **JWT** — JSON Web Tokens.
378. **OAuth 2.0** — через токены доступа.
379. **API Key** — заголовок или параметр URL.
380. **Session-based** — через cookies (credentials: 'include').

## Ретрансляция (Proxying)
381. **CORS proxy** — для обхода CORS.
382. **Reverse proxy** — на уровне сервера.
383. **API Gateway** — единая точка входа.

## Защита от CSRF
384. **CSRF token** — в заголовке или теле.
385. **SameSite cookies** — защита cookies.
386. **Origin header** — проверка происхождения.

## Сжатие данных
387. **Content-Encoding: gzip** — сжатие gzip.
388. **Content-Encoding: br** — сжатие Brotli.
389. **Content-Encoding: deflate** — сжатие deflate.
390. **Accept-Encoding** — указание поддерживаемых кодировок.

## Размеры и ограничения
391. **Content-Length** — размер тела.
392. **Transfer-Encoding: chunked** — передача частями.
393. **Максимальный размер** — ограничен сервером и браузером.
394. **Ограничения CORS** — заголовки и методы.

## События и слушатели
395. **Абстракция событий** — через кастомные события.
396. **Обработка ответов** — через then/catch.
397. **Обработка ошибок** — через catch.

## Утилиты
398. **URLSearchParams** — для параметров URL.
399. **FormData** — для данных формы.
400. **Blob** — для бинарных данных.
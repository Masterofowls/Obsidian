# Весь Jest в JavaScript

## Базовые понятия
1. **Jest** — популярный фреймворк для тестирования JavaScript (React, Node.js, TypeScript).
2. **Test runner** — запускает тесты, собирает результаты.
3. **Assertion library** — библиотека ассертов (expect).
4. **Mocking** — создание моков для зависимостей.
5. **Code Coverage** — измерение покрытия кода.
6. **Snapshot testing** — сравнение с сохранённым эталоном.
7. **Watch mode** — автоматический перезапуск тестов.
8. **Parallel execution** — параллельный запуск тестов.

## Установка и настройка
9. **npm install --save-dev jest** — установка.
10. **yarn add --dev jest** — установка через yarn.
11. **pnpm add -D jest** — установка через pnpm.
12. **npx jest --init** — инициализация конфигурации.
13. **jest.config.js** — файл конфигурации.
14. **jest.config.ts** — конфигурация на TypeScript.
15. **package.json** — `"scripts": { "test": "jest" }`.
16. **--watch** — режим наблюдения.
17. **--coverage** — генерация отчёта о покрытии.
18. **--verbose** — детальный вывод.
19. **--silent** — скрыть вывод console.log.
20. **--runInBand** — последовательный запуск.
21. **--maxWorkers** — количество потоков.

## Конфигурация Jest (jest.config.js)
22. **testMatch** — шаблон для тестовых файлов (`['**/__tests__/**/*.js', '**/?(*.)+(spec|test).js']`).
23. **testRegex** — RegExp для тестовых файлов.
24. **testEnvironment** — окружение ('node', 'jsdom').
25. **testEnvironmentOptions** — опции окружения.
26. **testPathIgnorePatterns** — игнорируемые пути.
27. **testTimeout** — таймаут теста (мс).
28. **coverageDirectory** — директория для отчёта.
29. **coveragePathIgnorePatterns** — игнорирование для покрытия.
30. **coverageThreshold** — минимальный порог покрытия.
31. **collectCoverageFrom** — файлы для покрытия.
32. **moduleFileExtensions** — расширения файлов (`['js', 'jsx', 'ts', 'tsx']`).
33. **moduleNameMapper** — маппинг путей (`{ '^@/(.*)$': '<rootDir>/src/$1' }`).
34. **modulePaths** — пути для поиска модулей.
35. **setupFiles** — файлы, выполняемые перед тестами.
36. **setupFilesAfterEnv** — файлы после окружения (для RTL).
37. **globalSetup** — глобальная настройка (один раз).
38. **globalTeardown** — глобальная очистка.
39. **transform** — трансформации (Babel, TypeScript).
40. **transformIgnorePatterns** — игнорирование трансформаций.
41. **verbose** — детальный вывод.
42. **bail** — остановка после N неудачных тестов.
43. **clearMocks** — очистка моков между тестами.
44. **resetMocks** — сброс моков.
45. **restoreMocks** — восстановление моков.
46. **globals** — глобальные переменные.
47. **rootDir** — корневая директория.
48. **roots** — корневые директории.
49. **displayName** — имя проекта (для мульти-проектов).
50. **projects** — несколько проектов в одном Jest.

## Синтаксис тестов
51. **describe(name, fn)** — группировка тестов.
52. **test(name, fn)** — определение теста.
53. **it(name, fn)** — alias для test.
54. **test.skip(name, fn)** — пропуск теста.
55. **test.only(name, fn)** — запуск только этого теста.
56. **test.todo(name)** — тест, который нужно написать.
57. **test.concurrent(name, fn)** — параллельный тест.
58. **test.each(table)(name, fn)** — параметризованный тест.
59. **describe.skip** — пропуск группы.
60. **describe.only** — запуск только этой группы.
61. **describe.concurrent** — параллельные тесты в группе.

## Хуки (Hooks)
62. **beforeAll(fn, timeout)** — один раз перед всеми тестами.
63. **afterAll(fn, timeout)** — один раз после всех тестов.
64. **beforeEach(fn, timeout)** — перед каждым тестом.
65. **afterEach(fn, timeout)** — после каждого теста.
66. **beforeEach(async () => { await ... })** — асинхронный хук.
67. **beforeAll(async () => { await ... })** — асинхронный хук.

## Ожидания (Expect)
68. **expect(value)** — начало ассерта.
69. **expect.extend(matchers)** — создание кастомных матчеров.
70. **expect.addSnapshotSerializer(serializer)** — кастомный сериализатор.
71. **expect.assertions(number)** — проверка числа ассертов.
72. **expect.hasAssertions()** — ожидает хотя бы один ассерт.
73. **expect.getState()** — состояние expect.
74. **expect.setState(state)** — установка состояния.
75. **expect.not** — инвертирование матчера.
76. **expect.anything()** — любое значение (кроме null/undefined).
77. **expect.any(Constructor)** — экземпляр конструктора.
78. **expect.arrayContaining(array)** — массив содержит элементы.
79. **expect.objectContaining(object)** — объект содержит свойства.
80. **expect.stringContaining(string)** — строка содержит подстроку.
81. **expect.stringMatching(regexp)** — строка соответствует RegExp.
82. **expect.closeTo(number, digits)** — число близко к ожидаемому.
83. **expect.throws(fn)** — функция выбрасывает ошибку.
84. **expect.assertions(1)** — проверка, что ассерт вызван.

## Основные матчеры (Matchers)
85. **.toBe(value)** — строгое равенство (`===`).
86. **.toEqual(value)** — глубокое сравнение объектов.
87. **.toStrictEqual(value)** — строгое глубокое сравнение.
88. **.toBeTruthy()** — значение истинно.
89. **.toBeFalsy()** — значение ложно.
90. **.toBeNull()** — значение null.
91. **.toBeUndefined()** — значение undefined.
92. **.toBeDefined()** — значение определено.
93. **.toBeNaN()** — значение NaN.
94. **.toBeInstanceOf(Class)** — экземпляр класса.
95. **.toMatch(regexp)** — соответствует RegExp.
96. **.toMatchObject(object)** — частичное совпадение объекта.
97. **.toHaveProperty(key, value)** — наличие свойства.
98. **.toBeGreaterThan(number)** — больше.
99. **.toBeGreaterThanOrEqual(number)** — больше или равно.
100. **.toBeLessThan(number)** — меньше.
101. **.toBeLessThanOrEqual(number)** — меньше или равно.
102. **.toBeCloseTo(number, digits)** — приблизительное равенство.
103. **.toContain(item)** — содержит элемент.
104. **.toContainEqual(object)** — содержит объект.
105. **.toHaveLength(number)** — длина (строки, массива).
106. **.toThrow(error)** — выбрасывает ошибку.
107. **.toThrowError(error)** — alias для toThrow.
108. **.toThrowErrorMatchingSnapshot()** — снапшот ошибки.
109. **.toMatchSnapshot()** — сравнение со снапшотом.
110. **.toMatchInlineSnapshot()** — встроенный снапшот.
111. **.toHaveBeenCalled()** — функция была вызвана.
112. **.toHaveBeenCalledTimes(number)** — вызвана n раз.
113. **.toHaveBeenCalledWith(...args)** — вызвана с аргументами.
114. **.toHaveBeenLastCalledWith(...args)** — последний вызов с аргументами.
115. **.toHaveBeenNthCalledWith(n, ...args)** — n-й вызов с аргументами.
116. **.toHaveReturned()** — функция вернула результат.
117. **.toHaveReturnedTimes(number)** — вернула результат n раз.
118. **.toHaveReturnedWith(value)** — вернула значение.
119. **.toHaveLastReturnedWith(value)** — последний возврат.
120. **.toHaveNthReturnedWith(n, value)** — n-й возврат.

## Матчеры для Promise
121. **.resolves** — проверка разрешённого Promise.
122. **.rejects** — проверка отклонённого Promise.
123. **await expect(promise).resolves.toBe(value)** — проверка.
124. **await expect(promise).rejects.toThrow(error)** — проверка.

## Матчеры для DOM (@testing-library/jest-dom)
125. **.toBeInTheDocument()** — элемент в DOM.
126. **.toBeVisible()** — элемент видим.
127. **.toBeDisabled()** — элемент отключён.
128. **.toBeEnabled()** — элемент включён.
129. **.toBeChecked()** — чекбокс/радио выбран.
130. **.toBePartiallyChecked()** — частично выбран.
131. **.toHaveClass(...classNames)** — имеет классы.
132. **.toHaveAttribute(attr, value)** — имеет атрибут.
133. **.toHaveStyle(styles)** — имеет стили.
134. **.toHaveFocus()** — в фокусе.
135. **.toHaveValue(value)** — имеет значение.
136. **.toHaveDisplayValue(value)** — отображаемое значение.
137. **.toHaveTextContent(text)** — имеет текст.
138. **.toContainElement(element)** — содержит элемент.
139. **.toContainHTML(html)** — содержит HTML.
140. **.toBeEmptyDOMElement()** — пустой DOM-элемент.
141. **.toBeInvalid()** — невалидный.
142. **.toBeValid()** — валидный.
143. **.toBeRequired()** — обязательный.
144. **.toHaveErrorMessage(text)** — сообщение об ошибке.

## Моки (Mocks)
145. **jest.fn()** — создание мок-функции.
146. **jest.fn(implementation)** — мок с реализацией.
147. **jest.fn().mockName(name)** — имя мока.
148. **mockFn.mock.calls** — массив вызовов.
149. **mockFn.mock.results** — массив результатов.
150. **mockFn.mock.instances** — массив экземпляров (для конструкторов).
151. **mockFn.mock.contexts** — массив контекстов (this).
152. **mockFn.mockClear()** — очистка вызовов.
153. **mockFn.mockReset()** — очистка и сброс реализации.
154. **mockFn.mockRestore()** — восстановление оригинальной реализации.
155. **mockFn.mockImplementation(fn)** — установка реализации.
156. **mockFn.mockImplementationOnce(fn)** — реализация на один вызов.
157. **mockFn.mockReturnValue(value)** — возврат значения.
158. **mockFn.mockReturnValueOnce(value)** — возврат на один вызов.
159. **mockFn.mockResolvedValue(value)** — возврат Promise (resolve).
160. **mockFn.mockResolvedValueOnce(value)** — однократный resolve.
161. **mockFn.mockRejectedValue(error)** — возврат Promise (reject).
162. **mockFn.mockRejectedValueOnce(error)** — однократный reject.
163. **mockFn.mockReturnThis()** — возврат this.
164. **mockFn.getMockName()** — получение имени.
165. **mockFn.mock.calls.length** — число вызовов.

## Моки модулей
166. **jest.mock(moduleName)** — мок модуля.
167. **jest.mock(moduleName, factory)** — мок с фабрикой.
168. **jest.unmock(moduleName)** — отмена мока.
169. **jest.doMock(moduleName, factory)** — динамический мок.
170. **jest.dontMock(moduleName)** — не мокать.
171. **jest.requireActual(moduleName)** — реальный модуль.
172. **jest.createMockFromModule(moduleName)** — автоматический мок.
173. **jest.genMockFromModule(moduleName)** — устаревший аналог.
174. **__mocks__/** — директория для ручных моков.
175. **__mocks__/module.js** — ручной мок модуля.
176. **mock module** — `jest.mock('axios')`.

## Шпионы (Spies)
177. **jest.spyOn(object, method)** — шпион за методом.
178. **jest.spyOn(object, method, 'get')** — шпион за геттером.
179. **jest.spyOn(object, method, 'set')** — шпион за сеттером.
180. **spy.mockRestore()** — восстановление.
181. **spy.mockClear()** — очистка.
182. **spy.mockReset()** — сброс.

## Фейковые таймеры
183. **jest.useFakeTimers()** — включение фейковых таймеров.
184. **jest.useRealTimers()** — возврат к реальным таймерам.
185. **jest.runAllTimers()** — выполнение всех таймеров.
186. **jest.runOnlyPendingTimers()** — выполнение ожидающих таймеров.
187. **jest.advanceTimersByTime(ms)** — продвижение таймеров.
188. **jest.advanceTimersByTimeAsync(ms)** — асинхронное продвижение.
189. **jest.runAllImmediates()** — выполнение setImmediate (Node.js).
190. **jest.clearAllTimers()** — очистка таймеров.
191. **jest.getTimerCount()** — количество активных таймеров.
192. **jest.setSystemTime(time)** — установка системного времени.
193. **jest.getRealSystemTime()** — реальное системное время.

## Снапшоты (Snapshots)
194. **expect(value).toMatchSnapshot()** — сравнение со снапшотом.
195. **expect(value).toMatchInlineSnapshot()** — встроенный снапшот.
196. **expect(error).toThrowErrorMatchingSnapshot()** — снапшот ошибки.
197. **expect(error).toThrowErrorMatchingInlineSnapshot()** — встроенный снапшот ошибки.
198. **jest --updateSnapshot** — обновление снапшотов.
199. **jest -u** — краткая форма.
200. **jest --updateSnapshot --testNamePattern** — обновление по шаблону.
201. **__snapshots__/** — директория для снапшотов.
202. **.snap** — расширение файлов снапшотов.
203. **snapshotSerializers** — кастомные сериализаторы.

## Тестирование асинхронного кода
204. **async/await** — основной способ.
205. **return Promise** — возврат Promise из теста.
206. **done()** — колбэк для асинхронных тестов.
207. **test('async', done => { ... })** — с done.
208. **await expect(promise).resolves.toBe(value)** — проверка resolve.
209. **await expect(promise).rejects.toThrow(error)** — проверка reject.
210. **expect.assertions(1)** — проверка числа ассертов.
211. **try/catch** — обработка ошибок в async/await.

## Параметризованные тесты
212. **test.each(table)(name, fn)** — параметризация.
213. **test.each([[1, 2, 3], [2, 3, 5]])** — массив данных.
214. **test.each([{ a: 1, b: 2, expected: 3 }])** — объекты.
215. **test.each`a | b | expected`** — шаблонная строка.
216. **describe.each(table)(name, fn)** — параметризация группы.

## Покрытие кода (Coverage)
217. **jest --coverage** — генерация отчёта.
218. **--collectCoverageFrom** — файлы для покрытия.
219. **--coverageDirectory** — директория отчёта.
220. **--coverageThreshold** — минимальный порог.
221. **--coveragePathIgnorePatterns** — игнорирование.
222. **coverageReporters** — форматы отчёта ('html', 'lcov', 'text', 'json').
223. **coverageProvider** — провайдер ('babel' или 'v8').
224. **Istanbul** — инструмент для покрытия.
225. **nyc** — CLI для Istanbul.
226. **100% coverage** — покрытие всего кода.

## Watch Mode
227. **jest --watch** — режим наблюдения.
228. **jest --watchAll** — наблюдение за всеми файлами.
229. **jest --watch --onlyChanged** — только изменённые файлы.
230. **Press a** — запустить все тесты.
231. **Press f** — запустить только упавшие тесты.
232. **Press o** — только изменённые файлы.
233. **Press p** — фильтр по имени файла.
234. **Press t** — фильтр по имени теста.
235. **Press q** — выход.
236. **Press Enter** — повторный запуск.

## Отладка тестов
237. **node --inspect-brk node_modules/.bin/jest --runInBand** — запуск с инспектором.
238. **chrome://inspect** — подключение к Node.js.
239. **VS Code debugger** — встроенная отладка.
240. **.vscode/launch.json** — конфигурация отладки.
241. **console.log** — вывод в консоль.
242. **--verbose** — детальный вывод.
243. **--silent** — скрыть console.log.
244. **test.only** — запуск одного теста.
245. **describe.only** — запуск одной группы.

## Интеграция с TypeScript
246. **@types/jest** — типы для Jest.
247. **ts-jest** — трансформация TypeScript.
248. **@jest/globals** — глобальные типы.
249. **jest.config.ts** — конфигурация на TS.
250. **transform: { '^.+\\.tsx?$': 'ts-jest' }** — настройка.
251. **jest --init** — выбор TypeScript.

## Интеграция с Babel
252. **babel-jest** — трансформация через Babel.
253. **@babel/preset-env** — пресет.
254. **@babel/preset-react** — для React.
255. **@babel/preset-typescript** — для TypeScript.

## Интеграция с React
256. **@testing-library/react** — тестирование React.
257. **@testing-library/jest-dom** — DOM-матчеры.
258. **@testing-library/user-event** — симуляция действий.
259. **React Testing Library** — альтернатива Enzyme.
260. **react-test-renderer** — снапшоты для React.
261. **jest-environment-jsdom** — окружение для DOM.

## Интеграция с Vue
262. **@vue/test-utils** — тестирование Vue.
263. **@vue/vue3-jest** — трансформация Vue.
264. **@testing-library/vue** — Testing Library для Vue.

## Интеграция с Angular
265. **jest-preset-angular** — пресет для Angular.
266. **@testing-library/angular** — Testing Library для Angular.

## Интеграция с Next.js
267. **next/jest** — пресет для Next.js.
268. **@testing-library/react** — тестирование компонентов.
269. **jest.setup.js** — настройка.

## Интеграция с Node.js
270. **node** — окружение по умолчанию.
271. **supertest** — тестирование HTTP.
272. **nock** — моки для HTTP.

## Интеграция с CI/CD
273. **jest --ci** — режим CI (без интерактива).
274. **--runInBand** — последовательный запуск.
275. **--maxWorkers=2** — ограничение потоков.
276. **--bail** — остановка после ошибки.
277. **--coverage** — отчёт о покрытии.
278. **--reporters** — кастомные репортёры.
279. **Github Actions** — интеграция с GitHub.
280. **GitLab CI** — интеграция с GitLab.
281. **Jenkins** — интеграция с Jenkins.
282. **CircleCI** — интеграция с CircleCI.

## Репортёры
283. **default** — стандартный репортёр.
284. **jest-silent-reporter** — минимальный вывод.
285. **jest-junit** — отчёт в JUnit формате.
286. **jest-html-reporter** — HTML-отчёт.
287. **jest-json-reporter** — JSON-отчёт.
288. **jest-stare** — расширенный HTML-отчёт.
289. **@jest/reporters** — встроенные репортёры.

## Плагины и утилиты
290. **jest-watch-typeahead** — улучшенный watch.
291. **jest-watch-select-projects** — выбор проектов.
292. **jest-watch-suspend** — приостановка watch.
293. **jest-watch-toggle-config** — переключение конфигурации.
294. **jest-mock-console** — мок для console.
295. **jest-fetch-mock** — мок для fetch.
296. **jest-localstorage-mock** — мок для localStorage.
297. **jest-date-mock** — мок для дат.
298. **jest-axe** — тестирование доступности.

## Кастомные матчеры
299. **expect.extend({ matcher(received, expected) { ... } })** — создание.
300. **matcher.pass** — прошёл ли тест.
301. **matcher.message()** — сообщение об ошибке.
302. **this.utils** — утилиты для матчеров.
303. **this.isNot** — инвертирование.
304. **this.promise** — тип Promise.
305. **this.equals(a, b)** — глубокое сравнение.
306. **this.expand** — развёрнутый вывод.

## Кастомные сериализаторы
307. **expect.addSnapshotSerializer(serializer)** — добавление.
308. **serializer.test(value)** — проверка типа.
309. **serializer.serialize(value)** — сериализация.

## Сборщики (Transforms)
310. **babel-jest** — Babel.
311. **ts-jest** — TypeScript.
312. **esbuild-jest** — esbuild.
313. **@swc/jest** — SWC (быстрая трансформация).
314. **jest-runner-esbuild** — esbuild runner.
315. **@jest/transform** — трансформации.

## Окружения (Environments)
316. **jest-environment-node** — Node.js (по умолчанию).
317. **jest-environment-jsdom** — браузерный DOM.
318. **jest-environment-jsdom-sixteen** — jsdom v16.
319. **custom environment** — кастомное окружение.

## Параллельный запуск
320. **--maxWorkers** — число потоков.
321. **--runInBand** — последовательный (без параллелизации).
322. **test.concurrent** — параллельные тесты.
323. **describe.concurrent** — параллельные группы.

## Фильтрация тестов
324. **--testNamePattern** — фильтр по имени теста.
325. **--testPathPattern** — фильтр по пути.
326. **--testPathIgnorePatterns** — игнорирование путей.
327. **--selectProjects** — выбор проектов.
328. **test.only** — только этот тест.
329. **test.skip** — пропуск теста.
330. **test.todo** — тест для написания.

## Глобальные переменные
331. **globals** — в конфигурации.
332. **__DEV__** — пример глобальной переменной.
333. **process.env** — переменные окружения.
334. **jest --env** — установка окружения.

## Чтение файлов
335. **fs.readFileSync** — синхронное чтение.
336. **require** — импорт JSON.
337. **test.env** — файлы окружения.

## Работа с датами
338. **jest.setSystemTime(date)** — установка системного времени.
339. **jest.useFakeTimers({ now: date })** — фейковые таймеры с началом.
340. **Date.now()** — мок даты.
341. **@sinonjs/fake-timers** — библиотека для таймеров.

## Работа с модулями
342. **jest.mock** — мок модуля.
343. **jest.unmock** — отмена мока.
344. **jest.doMock** — динамический мок.
345. **jest.requireActual** — реальный модуль.
346. **jest.isMockFunction(fn)** — проверка на мок.
347. **jest.replaceProperty(object, key, value)** — замена свойства.

## Чистка моков
348. **jest.clearAllMocks()** — очистка всех моков.
349. **jest.resetAllMocks()** — сброс всех моков.
350. **jest.restoreAllMocks()** — восстановление всех моков.

## Работа с консолью
351. **console.log** — вывод.
352. **console.warn** — предупреждение.
353. **console.error** — ошибка.
354. **spyOn(console, 'log')** — шпион за console.log.
355. **toHaveBeenCalledWith** — проверка вызова.

## Работа с ошибками
356. **expect(fn).toThrow()** — выбрасывает ошибку.
357. **expect(fn).toThrowError('message')** — ошибка с сообщением.
358. **expect(fn).toThrowError(/regex/)** — ошибка с RegExp.
359. **try/catch** — перехват ошибок.
360. **assert.throws** — проверка ошибки.

## Работа с базами данных
361. **setup/teardown** — создание и удаление БД.
362. **beforeAll** — создание таблиц.
363. **afterAll** — удаление таблиц.
364. **beforeEach** — очистка данных.
365. **test database** — отдельная БД для тестов.

## Работа с сетью
366. **nock** — мок HTTP-запросов.
367. **msw** — Mock Service Worker.
368. **supertest** — тестирование HTTP.
369. **fetch-mock** — мок fetch.
370. **axios-mock-adapter** — мок Axios.

## Работа с файлами
371. **fs** — файловая система.
372. **tmp** — временные файлы.
373. **mock-fs** — мок файловой системы.
374. **memfs** — виртуальная файловая система.

## Тестирование доступности
375. **jest-axe** — плагин.
376. **@testing-library/dom** — проверки.
377. **expect(document).toHaveNoViolations()** — проверка доступности.

## Тестирование перформанса
378. **performance.now()** — измерение времени.
379. **console.time** — таймер.
380. **expect(performance.now() - start).toBeLessThan(limit)** — проверка.

## Тестирование безопасности
381. **CSP** — проверка политики.
382. **XSS** — проверка уязвимостей.
383. **CSRF** — проверка защиты.

## Лучшие практики
384. **Test isolation** — каждый тест независим.
385. **Single responsibility** — один тест — одна проверка.
386. **Descriptive names** — описательные имена тестов.
387. **AAA pattern** — Arrange, Act, Assert.
388. **Clean code** — читаемый код тестов.
389. **DRY** — не дублировать код.
390. **Avoid test interdependence** — независимость тестов.
391. **Mock only necessary** — мокать только нужное.
392. **Keep tests fast** — быстрые тесты.
393. **Run tests often** — частый запуск.

## Отладка
394. **node --inspect-brk** — инспектор.
395. **VS Code debugger** — встроенная отладка.
396. **console.log** — простейшая отладка.
397. **test.only** — изоляция теста.
398. **--verbose** — детальный вывод.
399. **--silent** — скрыть вывод.

## CI/CD интеграция
400. **--ci** — режим CI.
401. **--bail** — остановка после ошибки.
402. **--coverage** — отчёт о покрытии.
403. **--maxWorkers=2** — ограничение потоков.
404. **--runInBand** — последовательный запуск.
405. **--reporters** — кастомные репортёры.

## Расширения
406. **jest-cli** — CLI утилита.
407. **jest-config** — конфигурация.
408. **jest-core** — ядро Jest.
409. **jest-environment** — окружения.
410. **jest-message-util** — форматирование сообщений.
411. **jest-regex-util** — утилиты для RegExp.
412. **jest-resolve** — разрешение модулей.
413. **jest-runner** — запуск тестов.
414. **jest-runtime** — выполнение тестов.
415. **jest-snapshot** — снапшоты.
416. **jest-util** — общие утилиты.
417. **jest-validate** — валидация конфигурации.

## Альтернативы Jest
418. **Vitest** — быстрый аналог на Vite.
419. **Mocha** — гибкий фреймворк.
420. **Jasmine** — BDD-фреймворк.
421. **Tape** — минималистичный.
422. **Ava** — конкурентный.
423. **QUnit** — старый, но надёжный.

## Миграция
424. **jasmine** → **jest** — автоматическая миграция.
425. **mocha** → **jest** — ручная миграция.
426. **sinon** → **jest** — замена на моки Jest.
427. **chai** → **jest** — замена ассертов.
428. **enzyme** → **testing-library** — миграция React.

## Ошибки и их решение
429. **Cannot find module** — неправильный путь.
430. **Timeout** — тест слишком долгий.
431. **Mock is not defined** — забыт import.
432. **Snapshot mismatch** — изменение кода.
433. **Coverage low** — недостаточно тестов.
434. **Test failed** — логика неверна.

## Ресурсы
435. **Официальная документация** — jestjs.io.
436. **Awesome Jest** — список утилит.
437. **Jest Cheatsheet** — шпаргалка.
438. **React Testing Library** — документация.
439. **Vue Test Utils** — документация.
440. **TypeScript + Jest** — руководство.
441. **ESLint-plugin-jest** — линтинг тестов.
442. **Prettier** — форматирование.

## Примеры
443. **Простой тест** — `test('adds 1 + 2', () => { expect(1 + 2).toBe(3); })`.
444. **Асинхронный тест** — `test('async', async () => { await expect(fetchData()).resolves.toBe('data'); })`.
445. **Мок функции** — `const mock = jest.fn().mockReturnValue(42)`.
446. **Мок модуля** — `jest.mock('axios')`.
447. **Снапшот** — `expect(component).toMatchSnapshot()`.
448. **Параметризация** — `test.each([[1, 2, 3]])('adds %i + %i = %i', (a, b, expected) => { expect(a + b).toBe(expected); })`.
449. **React компонент** — `render(<Component />); expect(screen.getByText('Hello')).toBeInTheDocument()`.
450. **HTTP тест** — `await request(app).get('/api').expect(200).expect('Content-Type', /json/)`.

## Режимы запуска
451. **jest** — все тесты.
452. **jest --watch** — наблюдение.
453. **jest --watchAll** — наблюдение за всеми.
454. **jest --coverage** — покрытие.
455. **jest --onlyChanged** — только изменённые.
456. **jest --findRelatedTests** — связанные тесты.
457. **jest --passWithNoTests** — успех без тестов.
458. **jest --json** — вывод в JSON.
459. **jest --outputFile** — вывод в файл.

## Настройка для больших проектов
460. **Монорепозиторий** — несколько проектов.
461. **projects** — в конфигурации.
462. **displayName** — имя проекта.
463. **rootDir** — корневая директория.
464. **moduleNameMapper** — маппинг путей.

## Модули и трансформация
465. **ES Modules** — поддержка import/export.
466. **CommonJS** — поддержка require.
467. **transform** — трансформация кода.
468. **transformIgnorePatterns** — игнорирование.
469. **moduleDirectories** — директории модулей.
470. **modulePaths** — пути поиска.

## Производительность
471. **--maxWorkers** — ограничение потоков.
472. **--runInBand** — последовательный запуск.
473. **--cache** — кэширование.
474. **--no-cache** — отключение кэша.
475. **--coverage** — покрытие (замедляет).
476. **--watch** — быстрее.
477. **transform** — быстрые трансформации (SWC, esbuild).

## Пре- и пост-хуки
478. **globalSetup** — глобальная настройка.
479. **globalTeardown** — глобальная очистка.
480. **setupFiles** — файлы перед тестами.
481. **setupFilesAfterEnv** — после окружения.

## Линтинг
482. **eslint-plugin-jest** — плагин для ESLint.
483. **eslint-plugin-testing-library** — плагин для RTL.
484. **prettier** — форматирование.

## Деплой
485. **jest --ci** — режим CI.
486. **jest --bail** — остановка.
487. **jest --coverage** — отчёт.
488. **jest --reporters** — репортёры.

## Файлы конфигурации
489. **jest.config.js** — основной.
490. **jest.config.ts** — TypeScript.
491. **jest.config.json** — JSON.
492. **package.json** — секция "jest".

## Кастомные репортёры
493. **DefaultReporter** — стандартный.
494. **SummaryReporter** — краткий отчёт.
495. **VerboseReporter** — детальный.
496. **NotifyReporter** — уведомления.
497. **GithubActionsReporter** — для GitHub.

## Типы для Jest
498. **@types/jest** — типы.
499. **@jest/globals** — глобальные типы.
500. **jest-mock-extended** — расширенные типы.
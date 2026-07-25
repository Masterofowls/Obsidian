# Весь TypeScript (с переходом с JavaScript)

## Базовые понятия
1. **TypeScript** — надмножество JavaScript, добавляющее статическую типизацию.
2. **TSC (TypeScript Compiler)** — компилятор TypeScript в JavaScript.
3. **Типизация** — указание типов переменных, функций, объектов.
4. **Транспиляция** — преобразование TS в JS для выполнения в браузере/Node.js.
5. **Declaration files (.d.ts)** — файлы с описанием типов для JS-библиотек.
6. **strict mode** — строгий режим типизации (все проверки включены).
7. **Type inference** — автоматическое определение типа.
8. **Structural typing** — совместимость по структуре, а не по имени.

## Установка и настройка
9. **npm install -D typescript** — установка TSC.
10. **npx tsc --init** — создание tsconfig.json.
11. **tsconfig.json** — конфигурация компилятора.
12. **tsc** — компиляция всех файлов.
13. **tsc --watch** — компиляция в режиме наблюдения.
14. **tsc --noEmit** — проверка типов без создания файлов.
15. **tsc --declaration** — генерация .d.ts файлов.
16. **ts-node** — выполнение TS напрямую в Node.js.
17. **@types/node** — типы для Node.js.
18. **@types/react** — типы для React.
19. **@types/jest** — типы для Jest.

## tsconfig.json основные настройки
20. **compilerOptions** — основные настройки компилятора.
21. **target** — версия JS ('ES5', 'ES6', 'ES2020', 'ESNext').
22. **module** — система модулей ('CommonJS', 'ESNext', 'ES2020').
23. **lib** — библиотеки ('DOM', 'ES6', 'ES2020').
24. **outDir** — директория для JS файлов.
25. **rootDir** — корневая директория исходников.
26. **strict** — включение всех строгих проверок.
27. **noImplicitAny** — запрет на неявный any.
28. **strictNullChecks** — строгая проверка null/undefined.
29. **strictFunctionTypes** — строгая проверка типов функций.
30. **strictBindCallApply** — строгая проверка bind/call/apply.
31. **noImplicitThis** — запрет на неявный this.
32. **alwaysStrict** — всегда использовать strict mode.
33. **esModuleInterop** — совместимость с CommonJS.
34. **skipLibCheck** — пропуск проверки библиотек.
35. **forceConsistentCasingInFileNames** — учёт регистра.
36. **resolveJsonModule** — импорт JSON файлов.
37. **isolatedModules** — изоляция модулей.
38. **allowJs** — разрешение JS файлов.
39. **checkJs** — проверка JS файлов.
40. **declaration** — генерация .d.ts файлов.
41. **declarationDir** — директория для .d.ts.
42. **sourceMap** — генерация source map.
43. **noUnusedLocals** — предупреждение о неиспользуемых переменных.
44. **noUnusedParameters** — предупреждение о неиспользуемых параметрах.
45. **noFallthroughCasesInSwitch** — проверка fallthrough в switch.
46. **moduleResolution** — стратегия разрешения модулей ('node', 'classic').
47. **baseUrl** — базовый путь для импортов.
48. **paths** — маппинг путей ('@/*': ['src/*']).
49. **types** — список типов для включения.
50. **exclude** — исключаемые файлы.
51. **include** — включаемые файлы.
52. **extends** — наследование конфигурации.
53. **references** — ссылки на другие проекты.

## Базовые типы
54. **string** — строки.
55. **number** — числа.
56. **boolean** — true/false.
57. **null** — null.
58. **undefined** — undefined.
59. **any** — любой тип (отключает проверку).
60. **unknown** — неизвестный тип (безопаснее any).
61. **never** — тип, который никогда не возвращается (ошибка, бесконечный цикл).
62. **void** — отсутствие возвращаемого значения.
63. **object** — любой не примитивный тип.
64. **bigint** — большие числа.
65. **symbol** — символы.

## Типизация переменных
66. **let name: string = 'John'** — явное указание типа.
67. **let age = 30** — type inference (вывод типа).
68. **const pi: 3.14 = 3.14** — литеральный тип.
69. **let value: any = 'text'** — любой тип.
70. **let value: unknown = 'text'** — безопасный any.
71. **let isDone: boolean** — без инициализации.
72. **let result: void** — void переменная (только undefined).

## Массивы и кортежи
73. **let list: number[] = [1, 2, 3]** — массив чисел.
74. **let list: Array<number> = [1, 2, 3]** — альтернативный синтаксис.
75. **let tuple: [string, number] = ['text', 42]** — кортеж (фиксированная длина).
76. **let tuple: [string, number?] = ['text']** — опциональный элемент.
77. **let tuple: [string, ...number[]] = ['text', 1, 2, 3]** — rest-элемент.
78. **tuple[0]** — доступ по индексу.
79. **tuple.length** — длина кортежа.

## Объекты
80. **let obj: { name: string; age: number }** — анонимный тип объекта.
81. **let obj: { name: string; age?: number }** — опциональное свойство.
82. **let obj: { readonly id: number }** — только для чтения.
83. **let obj: { [key: string]: number }** — индексная сигнатура (все свойства числа).
84. **Object.keys(obj)** — получение ключей.
85. **Object.values(obj)** — получение значений.
86. **Object.entries(obj)** — получение пар.

## Функции
87. **function add(a: number, b: number): number** — типизация функции.
88. **const add = (a: number, b: number): number => a + b** — стрелочная.
89. **function fn(a: number, b?: number): number** — опциональный параметр.
90. **function fn(a: number, b: number = 10): number** — параметр по умолчанию.
91. **function fn(...args: number[]): number** — rest-параметры.
92. **function fn(a: number, b: number): void** — ничего не возвращает.
93. **function fn(): never** — выбрасывает ошибку.
94. **function fn(a: string | number): void** — union тип.
95. **function fn(a: unknown): void** — unknown параметр.
96. **type Fn = (a: number) => number** — тип функции.
97. **const fn: Fn = (a) => a * 2** — функция с типом.

## Union и Intersection типы
98. **string | number** — union (строка или число).
99. **string & { id: number }** — intersection (объединение свойств).
100. **type A = string | number** — объявление типа.
101. **type B = A & { id: number }** — intersection.
102. **let value: string | number** — переменная может быть строкой или числом.
103. **typeof value === 'string'** — type guard.
104. **type Narrowing** — сужение типа через проверки.
105. **value as string** — утверждение типа (cast).
106. **value as unknown as number** — двойное утверждение.

## Literal типы
107. **let x: 'hello' = 'hello'** — только значение 'hello'.
108. **let x: 10 = 10** — только число 10.
109. **let x: true = true** — только true.
110. **type Direction = 'up' | 'down' | 'left' | 'right'** — union литералов.
111. **function move(dir: Direction)** — использование литерального типа.

## Enum (перечисления)
112. **enum Color { Red, Green, Blue }** — числовое перечисление.
113. **enum Color { Red = 1, Green = 2, Blue = 3 }** — с явными значениями.
114. **enum Color { Red = 'RED', Green = 'GREEN' }** — строковое перечисление.
115. **Color.Red** — доступ к значению.
116. **Color[1]** — обратная маппинг (для числовых).
117. **const enum Color { Red, Green }** — константное перечисление (инлайн).
118. **enum Status { Pending, Success, Error }** — статусы.

## Interface (интерфейсы)
119. **interface Person { name: string; age: number }** — объявление интерфейса.
120. **interface Person { readonly id: number }** — только для чтения.
121. **interface Person { age?: number }** — опциональное свойство.
122. **interface Person { [key: string]: any }** — индексная сигнатура.
123. **interface Person { greet(): void }** — метод.
124. **interface Person { greet: () => void }** — метод как свойство.
125. **interface Person extends Animal** — наследование интерфейсов.
126. **interface Person implements Animal** — реализация (для классов).
127. **interface Person { name: string }** — объединение интерфейсов (автоматическое слияние).
128. **type Person = { name: string }** — тип vs interface.

## Type Aliases
129. **type Point = { x: number; y: number }** — объявление типа.
130. **type Point = { x: number } & { y: number }** — intersection.
131. **type Point = { x: number } | { y: number }** — union.
132. **type Point = string | number** — простой alias.
133. **type Point = (x: number) => number** — функция.
134. **type Point<T> = { value: T }** — дженерик.

## Classes (классы)
135. **class Person { name: string }** — класс с полем.
136. **class Person { private name: string }** — приватное поле (только внутри класса).
137. **class Person { protected name: string }** — защищённое поле (доступно в наследниках).
138. **class Person { public name: string }** — публичное поле (по умолчанию).
139. **class Person { readonly id: number }** — только для чтения.
140. **class Person { constructor(name: string) { this.name = name } }** — конструктор.
141. **class Person { name: string; constructor(name: string) { this.name = name } }** — сокращение.
142. **class Person { constructor(public name: string) { } }** — автоматическое поле.
143. **class Person { constructor(public name: string, private age: number) { } }** — смешанные.
144. **class Person { get fullName(): string { return this.name } }** — геттер.
145. **class Person { set fullName(value: string) { this.name = value } }** — сеттер.
146. **class Person { static count: number = 0 }** — статическое поле.
147. **class Person { static getCount(): number { return Person.count } }** — статический метод.
148. **class Student extends Person** — наследование.
149. **class Student { constructor(name: string, public grade: number) { super(name) } }** — super().
150. **class Person { abstract name: string }** — абстрактный класс.
151. **abstract class Person { abstract greet(): void }** — абстрактный метод.
152. **class Person { #privateField: string }** — приватное поле (ES2022).

## Generic (дженерики)
153. **function identity<T>(arg: T): T** — дженерик-функция.
154. **let output = identity<string>('hello')** — явное указание типа.
155. **let output = identity('hello')** — type inference.
156. **function identity<T extends string>(arg: T): T** — ограничение.
157. **class Box<T> { value: T }** — дженерик-класс.
158. **interface KeyValue<K, V> { key: K; value: V }** — дженерик-интерфейс.
159. **type Generic<T> = T[]** — дженерик-тип.
160. **function fn<T, U>(a: T, b: U): void** — несколько дженериков.
161. **T extends keyof U** — ограничение на ключи.
162. **keyof T** — тип ключей объекта.
163. **T[keyof T]** — тип значений.
164. **Partial<T>** — все свойства опциональны.
165. **Required<T>** — все свойства обязательны.
166. **Readonly<T>** — все свойства только для чтения.
167. **Record<K, T>** — объект с ключами K и значениями T.
168. **Pick<T, K>** — выбор свойств.
169. **Omit<T, K>** — исключение свойств.
170. **Exclude<T, U>** — исключение типов.
171. **Extract<T, U>** — извлечение типов.
172. **NonNullable<T>** — исключение null/undefined.
173. **ReturnType<T>** — тип возвращаемого значения.
174. **Parameters<T>** — тип параметров функции.
175. **ConstructorParameters<T>** — тип параметров конструктора.
176. **InstanceType<T>** — тип экземпляра.

## Utility Types
177. **Partial<T>** — все опциональны.
178. **Required<T>** — все обязательны.
179. **Readonly<T>** — все только для чтения.
180. **Record<K, T>** — объект с ключами.
181. **Pick<T, K>** — выбор свойств.
182. **Omit<T, K>** — исключение свойств.
183. **Exclude<T, U>** — исключение типов.
184. **Extract<T, U>** — извлечение типов.
185. **NonNullable<T>** — исключение null/undefined.
186. **ReturnType<T>** — возвращаемый тип.
187. **Parameters<T>** — параметры функции.
188. **ConstructorParameters<T>** — параметры конструктора.
189. **InstanceType<T>** — тип экземпляра.
190. **Uppercase<T>** — строку в верхний регистр.
191. **Lowercase<T>** — строку в нижний регистр.
192. **Capitalize<T>** — первую букву заглавной.
193. **Uncapitalize<T>** — первую букву строчной.

## Type Guards (проверка типов)
194. **typeof value === 'string'** — проверка примитивов.
195. **value instanceof Date** — проверка экземпляра.
196. **'name' in obj** — проверка свойства.
197. **Array.isArray(value)** — проверка массива.
198. **function isString(value: unknown): value is string** — пользовательский type guard.
199. **value as string** — утверждение типа.
200. **if (value !== null && value !== undefined)** — проверка на null/undefined.

## Assertion Functions
201. **function assert(condition: any, msg?: string): asserts condition** — утверждение.
202. **function assertIsNumber(value: unknown): asserts value is number** — утверждение типа.
203. **function assertNotNull<T>(value: T): asserts value is NonNullable<T>** — проверка на null.

## Decorators (декораторы)
204. **@decorator** — декоратор класса.
205. **@decorator** — декоратор метода.
206. **@decorator** — декоратор свойства.
207. **@decorator** — декоратор параметра.
208. **@decorator** — декоратор аксессора.
209. **experimentalDecorators: true** — включение в tsconfig.
210. **@log** — пример декоратора логирования.
211. **@deprecated** — пример декоратора предупреждения.

## Модули
212. **import { fn } from './module'** — именованный импорт.
213. **import * as module from './module'** — импорт всего.
214. **import module from './module'** — импорт по умолчанию.
215. **import type { Type } from './module'** — импорт только типа.
216. **export const fn = () => {}** — именованный экспорт.
217. **export default fn** — экспорт по умолчанию.
218. **export * from './module'** — реэкспорт.
219. **export type { Type }** — экспорт типа.

## Declaration Files (.d.ts)
220. **declare module 'module-name'** — объявление модуля.
221. **declare var globalVar** — объявление глобальной переменной.
222. **declare function fn(arg: string): void** — объявление функции.
223. **declare class ClassName** — объявление класса.
224. **declare namespace Namespace** — объявление пространства имён.
225. **declare module 'module' { export interface Type { } }** — объявление типов.
226. **/// <reference types="node" />** — ссылка на типы.

## DefinitelyTyped (@types)
227. **@types/node** — типы для Node.js.
228. **@types/react** — типы для React.
229. **@types/jest** — типы для Jest.
230. **@types/express** — типы для Express.
231. **@types/lodash** — типы для Lodash.
232. **@types/axios** — типы для Axios.

## Миграция с JavaScript на TypeScript
233. **allowJs: true** — разрешение JS файлов.
234. **checkJs: true** — проверка JS файлов.
235. **// @ts-check** — проверка JS файла.
236. **// @ts-nocheck** — отключение проверки.
237. **// @ts-ignore** — игнорирование ошибки на следующей строке.
238. **// @ts-expect-error** — ожидание ошибки.
239. **.js → .ts** — переименование файлов.
240. **.jsx → .tsx** — для React.
241. **any** — временное использование.
242. **unknown** — безопасная альтернатива any.
243. **Постепенная типизация** — добавление типов постепенно.
244. **Строгий режим** — включение после завершения миграции.

## Особенности для React
245. **React.FC<Props>** — тип функционального компонента.
246. **interface Props { name: string }** — тип пропсов.
247. **React.useState<number>(0)** — типизация хуков.
248. **React.useRef<HTMLDivElement>(null)** — типизация рефов.
249. **React.useReducer<Reducer>(reducer, state)** — типизация useReducer.
250. **React.Context<Type>** — типизация контекста.
251. **React.ReactNode** — тип для children.
252. **React.ReactElement** — тип для элемента.
253. **React.CSSProperties** — тип для CSS.
254. **React.FormEvent<HTMLFormElement>** — типизация событий.
255. **React.MouseEvent<HTMLButtonElement>** — событие мыши.
256. **React.ChangeEvent<HTMLInputElement>** — событие изменения.

## Особенности для Express
257. **Request** — тип запроса.
258. **Response** — тип ответа.
259. **NextFunction** — тип next.
260. **RequestHandler** — тип обработчика.
261. **Request.params** — параметры URL.
262. **Request.query** — параметры запроса.
263. **Request.body** — тело запроса.

## Особенности для Jest
264. **test('name', () => { ... })** — тест.
265. **expect(value).toBe(expected)** — матчеры.
266. **describe('group', () => { ... })** — группировка.
267. **jest.fn<() => number>()** — типизированный мок.
268. **jest.mock('module')** — мок модуля.
269. **@types/jest** — типы для Jest.

## Особенности для Node.js
270. **process.env** — переменные окружения.
271. **__dirname** — путь к директории.
272. **require** — импорт CommonJS.
273. **module.exports** — экспорт CommonJS.
274. **global** — глобальный объект.

## Совместимость с JavaScript
275. **allowJs** — работа с JS файлами.
276. **checkJs** — проверка JS файлов.
277. **JSDoc** — типы через комментарии.
278. **@type {string}** — JSDoc тип.
279. **@param {string} name** — JSDoc параметр.
280. **@returns {number}** — JSDoc возврат.
281. **@typedef** — JSDoc тип.
282. **@import** — JSDoc импорт.

## Есть ли в TypeScript всё из JavaScript?
283. **Да** — TypeScript включает все фичи JavaScript.
284. **ES6+** — все современные фичи.
285. **ES Modules** — import/export.
286. **Async/Await** — асинхронность.
287. **Classes** — классы.
288. **Arrow functions** — стрелочные функции.
289. **Destructuring** — деструктуризация.
290. **Spread/Rest** — операторы.
291. **Optional chaining** — `?.`.
292. **Nullish coalescing** — `??`.
293. **BigInt** — большие числа.
294. **Symbol** — символы.

## Чего нет в TypeScript из JavaScript?
295. **Динамическая типизация** — в TS статическая.
296. **Свободное приведение типов** — TS строже.
297. **Добавление свойств к объектам** — надо объявлять интерфейс.
298. **eval** — не рекомендуется.
299. **with** — запрещён в строгом режиме.

## Инструменты
300. **ESLint** — линтинг TS.
301. **@typescript-eslint/parser** — парсер для ESLint.
302. **@typescript-eslint/eslint-plugin** — плагин для ESLint.
303. **Prettier** — форматирование.
304. **ts-node** — выполнение TS в Node.js.
305. **tsx** — выполнение TS (альтернатива).
306. **ts-jest** — Jest для TS.
307. **vite** — сборщик с TS.
308. **webpack** — сборщик с TS.
309. **rollup** — сборщик с TS.
310. **esbuild** — быстрый сборщик.
311. **swc** — быстрый компилятор.

## Отладка
312. **sourceMap** — карта исходников.
313. **tsc --sourceMap** — генерация sourceMap.
314. **VS Code** — встроенная отладка.
315. **Chrome DevTools** — отладка в браузере.
316. **ts-node --inspect** — отладка Node.js.

## Лучшие практики
317. **Включить strict: true** — все проверки.
318. **Использовать unknown вместо any** — безопасность.
319. **Использовать interface для объектов** — расширяемость.
320. **Использовать type для union/intersection** — гибкость.
321. **Использовать дженерики** — переиспользуемость.
322. **Не использовать any** — теряется типизация.
323. **Использовать readonly** — неизменяемость.
324. **Использовать never** — для недостижимых состояний.
325. **Использовать Utility Types** — Partial, Pick, Omit.
326. **Писать тесты** — на TS.

## Продвинутые техники
327. **Conditional Types** — условные типы (`T extends U ? X : Y`).
328. **Mapped Types** — преобразование свойств (`{ [P in K]: T[P] }`).
329. **Template Literal Types** — строки с шаблонами.
330. **Recursive Types** — рекурсивные типы.
331. **Branded Types** — брендирование типов.
332. **Nominal Types** — номинальные типы (эмуляция).
333. **Type-only imports** — `import type`.
334. **Export type** — экспорт только типа.
335. **Namespace** — пространства имён.
336. **Declaration merging** — слияние деклараций.
337. **Ambient declarations** — объявления окружения.
338. **Triple-slash references** — ссылки на типы.

## Примеры кода
339. **Простая функция** — `function greet(name: string): string { return 'Hello ' + name }`.
340. **Интерфейс** — `interface User { id: number; name: string }`.
341. **Класс** — `class Animal { constructor(public name: string) { } }`.
342. **Дженерик** — `function identity<T>(arg: T): T { return arg }`.
343. **Union** — `type Status = 'pending' | 'success' | 'error'`.
344. **Utility Type** — `type PartialUser = Partial<User>`.
345. **Type Guard** — `function isString(value: unknown): value is string { return typeof value === 'string' }`.
346. **Assertion** — `function assertNotNull<T>(value: T): asserts value is NonNullable<T> { if (value === null || value === undefined) throw new Error() }`.
347. **React Component** — `const Button: React.FC<{ onClick: () => void }> = ({ onClick, children }) => <button onClick={onClick}>{children}</button>`.
348. **Express handler** — `app.get('/api', (req: Request, res: Response) => { res.json({}) })`.
349. **Jest test** — `test('add', () => { expect(add(1, 2)).toBe(3) })`.

## Инструменты для перехода
350. **TypeScript** — официальный компилятор.
351. **ts-migrate** — автоматическая миграция.
352. **typescript-eslint** — линтинг.
353. **JSDoc** — типы в комментариях.

## Частые ошибки
354. **Использование any** — теряется безопасность.
355. **Не обрабатывать null/undefined** — ошибки времени выполнения.
356. **Неправильный тип для this** — конфликты контекста.
357. **Не использовать strict** — пропуск ошибок.
358. **Переопределение типов** — конфликты.
359. **Неправильные импорты** — ошибки модулей.
360. **Игнорирование ошибок** — `// @ts-ignore` без причины.

## TypeScript в больших проектах
361. **Монорепозиторий** — несколько проектов.
362. **Project References** — ссылки на проекты (`references` в tsconfig).
363. **Composite: true** — композитный проект.
364. **Incremental: true** — инкрементальная компиляция.
365. **paths** — маппинг путей.
366. **baseUrl** — базовый путь.

## TypeScript и сборщики
367. **Vite** — `ts` поддержка из коробки.
368. **Webpack** — `ts-loader`, `awesome-typescript-loader`.
369. **esbuild** — быстрая сборка.
370. **SWC** — быстрый компилятор.
371. **Babel** — `@babel/preset-typescript`.

## TypeScript и фреймворки
372. **React** — `@types/react`.
373. **Vue** — `@vue/tsconfig`.
374. **Angular** — встроенная поддержка.
375. **Svelte** — `svelte-preprocess`.
376. **Next.js** — встроенная поддержка.
377. **Nuxt** — встроенная поддержка.
378. **NestJS** — встроенная поддержка.
379. **Express** — `@types/express`.

## Ресурсы
380. **Официальная документация** — typescriptlang.org.
381. **TypeScript Playground** — онлайн-среда.
382. **Awesome TypeScript** — список ресурсов.
383. **TypeScript Deep Dive** — книга.
384. **TypeScript GitHub** — исходники.

## Заключение
385. **TypeScript = JavaScript + типы** — основная формула.
386. **Статическая типизация** — безопасность на этапе компиляции.
387. **Совместимость** — 100% совместимость с JS.
388. **Инструменты** — отличная поддержка в редакторах.
389. **Сообщество** — огромное и активное.
390. **Всё что есть в JS** — доступно в TS.
391. **ES6+** — все современные фичи.
392. **strict mode** — обязателен для больших проектов.
393. **Медленный переход** — можно мигрировать постепенно.
394. **Типизация** — улучшает качество кода.
395. **Документация** — типы как документация.
396. **Рефакторинг** — безопасный и быстрый.
397. **Поддержка** — все основные библиотеки.
398. **Будущее** — TS становится стандартом.
399. **Инструменты** — огромный экосистема.
400. **Сообщество** — постоянно растёт.
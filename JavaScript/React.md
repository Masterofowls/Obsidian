# Весь React в JavaScript (и TypeScript)

## Базовые понятия
1. **React** — библиотека для построения пользовательских интерфейсов.
2. **Компонент** — независимая часть UI (функция или класс).
3. **JSX** — расширение синтаксиса JavaScript для описания UI.
4. **Virtual DOM** — представление UI в памяти для оптимизации обновлений.
5. **Reconciliation** — процесс сравнения Virtual DOM с реальным.
6. **Props** — входные данные, передаваемые компоненту.
7. **State** — внутреннее состояние компонента.
8. **Жизненный цикл** — этапы существования компонента (монтирование, обновление, размонтирование).
9. **React Hooks** — функции для работы с состоянием и эффектами (useState, useEffect).
10. **Context** — способ передачи данных через дерево компонентов без props drilling.
11. **React Server Components** — компоненты, выполняемые на сервере.
12. **Concurrent Mode** — режим конкурентного выполнения для улучшения UX.
13. **Fiber** — переписанный алгоритм рендеринга для поддержки Concurrent Mode.

## Основные методы React
14. **ReactDOM.createRoot(document.getElementById('root')).render(<App />)** — рендеринг компонента (React 18).
15. **ReactDOM.render(<App />, document.getElementById('root'))** — устаревший метод рендеринга.
16. **ReactDOM.createPortal(children, container)** — рендеринг вне текущего компонента.
17. **React.createElement(type, props, children)** — создание элемента без JSX.
18. **React.cloneElement(element, props, children)** — клонирование элемента с новыми props.
19. **React.isValidElement(object)** — проверка, является ли объект React-элементом.
20. **React.Children.map(children, fn)** — итерация по детям с защитой.
21. **React.Children.forEach(children, fn)** — аналогично map, но без возврата.
22. **React.Children.count(children)** — количество детей.
23. **React.Children.only(children)** — проверка, что только один ребенок.
24. **React.Children.toArray(children)** — преобразование в массив.
25. **React.memo(Component, arePropsEqual)** — мемоизация компонента.

## Компоненты
26. **Function Component** — `function MyComponent(props) { return <div /> }`.
27. **Arrow Function Component** — `const MyComponent = (props) => <div />`.
28. **Class Component** — `class MyComponent extends React.Component { render() { return <div /> } }`.
29. **PureComponent** — `class MyComponent extends React.PureComponent { }` (поверхностное сравнение).
30. **React.memo** — мемоизация функционального компонента.
31. **React.forwardRef** — проброс ref к дочернему компоненту.
32. **React.lazy** — ленивая загрузка компонента.
33. **React.Suspense** — компонент для работы с lazy (показ fallback).
34. **React.StrictMode** — строгий режим для обнаружения проблем.
35. **React.Fragment** — компонент без лишнего div (`<>...</>`).

## Props
36. **props.name** — доступ к свойству.
37. **props.children** — дочерние элементы.
38. **props.onClick** — обработчик события (переданный от родителя).
39. **defaultProps** — значения по умолчанию (для классовых компонентов).
40. **defaultProps для функциональных** — `Component.defaultProps = { ... }`.
41. **destructuring props** — `function MyComponent({ name, age }) { }`.
42. **prop-types** — проверка типов (для Runtime).
43. **PropTypes.string** — строка.
44. **PropTypes.number** — число.
45. **PropTypes.bool** — логический.
46. **PropTypes.array** — массив.
47. **PropTypes.object** — объект.
48. **PropTypes.func** — функция.
49. **PropTypes.node** — React-узел (строка, число, элемент).
50. **PropTypes.element** — React-элемент.
51. **PropTypes.oneOf(['a', 'b'])** — один из списка.
52. **PropTypes.oneOfType([PropTypes.string, PropTypes.number])** — один из типов.
53. **PropTypes.arrayOf(PropTypes.string)** — массив конкретного типа.
54. **PropTypes.objectOf(PropTypes.number)** — объект с полями конкретного типа.
55. **PropTypes.shape({ name: PropTypes.string })** — структура объекта.
56. **PropTypes.exact({ name: PropTypes.string })** — точная структура.
57. **PropTypes.isRequired** — обязательное свойство.
58. **PropTypes.elementType** — тип компонента.

## State (Состояние)
59. **useState(initialState)** — хук для состояния (функциональные компоненты).
60. **const [state, setState] = useState(0)** — деструктуризация.
61. **setState(newValue)** — обновление состояния.
62. **setState(prev => prev + 1)** — функциональное обновление.
63. **useState с объектом** — `const [state, setState] = useState({ count: 0 })`.
64. **useState с массивом** — `const [items, setItems] = useState([])`.
65. **useState с функцией** — `const [state, setState] = useState(() => expensiveComputation())` (ленивая инициализация).
66. **Class Component state** — `this.state = { count: 0 }`.
67. **this.setState({ count: 1 })** — обновление состояния в классовых компонентах.
68. **this.setState((prev) => ({ count: prev.count + 1 }))** — функциональное обновление.
69. **this.setState({ count: 1 }, () => { })** — колбэк после обновления.

## Hooks (Хуки)
70. **useState** — состояние.
71. **useEffect** — побочные эффекты (запросы, подписки, DOM-операции).
72. **useEffect(() => { }, [])** — эффект, выполняющийся один раз (при монтировании).
73. **useEffect(() => { return () => { } }, [])** — очистка при размонтировании.
74. **useEffect(() => { }, [deps])** — эффект при изменении зависимостей.
75. **useEffect(() => { })** — эффект при каждом рендере (не рекомендуется).
76. **useContext** — доступ к контексту.
77. **useReducer** — альтернатива useState для сложной логики.
78. **useCallback** — мемоизация функции.
79. **useCallback(() => { }, [deps])** — создание мемоизированной функции.
80. **useMemo** — мемоизация значения.
81. **useMemo(() => expensiveComputation(a, b), [a, b])** — мемоизация вычислений.
82. **useRef** — рефы (доступ к DOM, сохранение значений между рендерами).
83. **useRef(initialValue)** — создание рефа.
84. **useRef(null)** — реф для DOM-элемента.
85. **useRef(0)** — сохранение значения (не вызывает перерендер).
86. **useLayoutEffect** — эффект, выполняющийся синхронно после всех изменений DOM (перед отрисовкой).
87. **useImperativeHandle** — настройка рефа для дочернего компонента.
88. **useDebugValue** — отладка в React DevTools.
89. **useTransition** — отложенные обновления (Concurrent Mode).
90. **useDeferredValue** — отложенное значение (Concurrent Mode).
91. **useId** — генерация уникального ID (для доступности).
92. **useSyncExternalStore** — синхронизация с внешними хранилищами.
93. **useInsertionEffect** — вставка стилей (для CSS-in-JS).

## useEffect подробно
94. **useEffect(() => { fetchData() }, [])** — запрос при монтировании.
95. **useEffect(() => { const interval = setInterval(() => { }, 1000); return () => clearInterval(interval) }, [])** — таймер с очисткой.
96. **useEffect(() => { window.addEventListener('resize', handler); return () => window.removeEventListener('resize', handler) }, [])** — подписка с очисткой.
97. **useEffect(() => { document.title = `Count: ${count}` }, [count])** — синхронизация с DOM.
98. **useEffect(() => { if (count > 5) { /* do something */ } }, [count])** — условный эффект.
99. **useEffect с async** — `useEffect(() => { const fetch = async () => { await ... }; fetch() }, [])`.

## Context (Контекст)
100. **createContext(defaultValue)** — создание контекста.
101. **const MyContext = createContext()** — пример.
102. **<MyContext.Provider value={value}>** — провайдер контекста.
103. **useContext(MyContext)** — использование в функциональном компоненте.
104. **MyContext.Consumer** — использование в классовых компонентах.
105. **ClassComponent.contextType = MyContext** — использование в классовом компоненте.
106. **this.context** — доступ к контексту в классе.
107. **useContext(MyContext)** — хук для контекста.
108. **Context + useReducer** — глобальное состояние.
109. **Context + useMemo** — оптимизация контекста.

## Refs (Рефы)
110. **useRef(null)** — создание рефа.
111. **ref.current** — доступ к DOM-элементу.
112. **<input ref={inputRef} />** — привязка к элементу.
113. **React.forwardRef** — проброс рефа.
114. **useImperativeHandle(ref, () => ({ focus: () => { } }))** — кастомный реф.
115. **createRef()** — создание рефа в классовых компонентах.
116. **this.refName.current** — доступ в классовом компоненте.
117. **ref callback** — `<input ref={el => this.input = el} />`.

## События (Events)
118. **onClick** — событие клика.
119. **onChange** — событие изменения.
120. **onSubmit** — событие отправки.
121. **onKeyDown** — событие нажатия клавиши.
122. **onKeyUp** — событие отпускания клавиши.
123. **onFocus** — событие фокуса.
124. **onBlur** — событие потери фокуса.
125. **onMouseEnter** — наведение мыши.
126. **onMouseLeave** — уход мыши.
127. **onMouseDown** — нажатие кнопки мыши.
128. **onMouseUp** — отпускание кнопки мыши.
129. **onScroll** — событие скролла.
130. **onLoad** — событие загрузки.
131. **onError** — событие ошибки.
132. **onTransitionEnd** — конец CSS-перехода.
133. **onAnimationEnd** — конец CSS-анимации.
134. **onAnimationStart** — начало CSS-анимации.
135. **onAnimationIteration** — повторение CSS-анимации.
136. **onPointerDown** — событие указателя.
137. **onPointerUp** — событие указателя.
138. **onPointerMove** — событие указателя.

## SyntheticEvent (Синтетическое событие)
139. **event.target** — элемент, на котором произошло событие.
140. **event.currentTarget** — элемент, на котором висит обработчик.
141. **event.preventDefault()** — отмена поведения по умолчанию.
142. **event.stopPropagation()** — остановка всплытия.
143. **event.nativeEvent** — нативное событие браузера.
144. **event.persist()** — сохранение события для асинхронного использования (устаревший).
145. **event.type** — тип события.
146. **event.isDefaultPrevented()** — проверка, отменено ли поведение.
147. **event.isPropagationStopped()** — проверка, остановлено ли всплытие.
148. **event.isTrusted** — событие от пользователя.

## Условный рендеринг (Conditional Rendering)
149. **if (condition) { return <Component /> }** — условный рендеринг через if.
150. **return condition ? <Component /> : null** — тернарный оператор.
151. **return condition && <Component />** — логическое И.
152. **return <>{condition && <Component />}</>** — фрагмент с условием.
153. **const element = condition ? <Component /> : null** — присвоение переменной.
154. **switch (type) { case 'a': return <A />; case 'b': return <B />; }** — switch в рендере.

## Списки и ключи (Lists and Keys)
155. **{items.map((item) => <li key={item.id}>{item.name}</li>)}** — рендеринг списка.
156. **key** — уникальный идентификатор для оптимизации (React использует для diffing).
157. **key={item.id}** — использование уникального ключа.
158. **key={index}** — использование индекса (не рекомендуется).
159. **{Object.entries(obj).map(([key, value]) => <li key={key}>{value}</li>)}** — рендеринг объекта.
160. **{Array.from({ length: 10 }, (_, i) => <li key={i}>{i}</li>)}** — создание списка из числа.

## Формы (Forms)
161. **onChange** — изменение формы (контролируемый компонент).
162. **value={value}** — привязка значения.
163. **onSubmit** — отправка формы.
164. **<input type="text" />** — текстовое поле.
165. **<input type="checkbox" />** — чекбокс.
166. **<input type="radio" />** — радио-кнопка.
167. **<select>** — выпадающий список.
168. **<textarea>** — текстовое поле для ввода нескольких строк.
169. **<input type="file" />** — загрузка файлов.
170. **event.target.value** — значение поля.
171. **event.target.checked** — состояние чекбокса/радио.
172. **event.target.files** — файлы (для input type="file").
173. **event.target.name** — имя поля.
174. **event.preventDefault()** — отмена перезагрузки страницы.

## Контролируемые и неконтролируемые компоненты
175. **Controlled component** — значение управляется React (state).
176. **<input value={value} onChange={onChange} />** — контролируемый компонент.
177. **Uncontrolled component** — значение управляется DOM (ref).
178. **<input defaultValue="text" />** — неконтролируемый компонент.
179. **<input ref={inputRef} />** — доступ к значению через ref.
180. **useRef для неконтролируемого** — получение значения.

## Обработка ошибок (Error Boundaries)
181. **Error Boundary** — компонент, ловящий ошибки в дочерних компонентах.
182. **class ErrorBoundary extends React.Component** — классовый компонент.
183. **static getDerivedStateFromError(error)** — обновление состояния при ошибке.
184. **componentDidCatch(error, info)** — логирование ошибки.
185. **componentDidCatch(error, errorInfo)** — доступ к стеку ошибок.
186. **fallback UI** — UI при ошибке.
187. **<ErrorBoundary fallback={<ErrorPage />}>** — использование.
188. **react-error-boundary** — библиотека для Error Boundaries.

## Рендеринг и обновления (Rendering)
189. **Реактивный рендеринг** — автоматическое обновление при изменении состояния.
190. **Рендер-цикл** — вызов render после изменения state.
191. **setState асинхронен** — обновление состояния не сразу видно.
192. **forceUpdate()** — принудительный рендеринг (не рекомендуется).
193. **shouldComponentUpdate** — предотвращение рендеринга (классовый компонент).
194. **React.memo** — предотвращение рендеринга (функциональный компонент).
195. **PureComponent** — автоматическая оптимизация.
196. **React.PureComponent** — поверхностное сравнение props/state.

## Жизненный цикл (Lifecycle) — Class Components
197. **constructor(props)** — инициализация.
198. **render()** — рендеринг компонента.
199. **componentDidMount()** — после монтирования (запросы, подписки).
200. **componentDidUpdate(prevProps, prevState, snapshot)** — после обновления.
201. **componentWillUnmount()** — перед размонтированием (очистка).
202. **shouldComponentUpdate(nextProps, nextState)** — можно ли обновлять.
203. **componentDidCatch(error, info)** — ошибка в дочернем компоненте.
204. **getDerivedStateFromProps(props, state)** — обновление состояния из props (редко).
205. **getSnapshotBeforeUpdate(prevProps, prevState)** — получение информации до обновления.
206. **UNSAFE_componentWillMount()** — устаревший.
207. **UNSAFE_componentWillReceiveProps()** — устаревший.
208. **UNSAFE_componentWillUpdate()** — устаревший.

## Жизненный цикл (Lifecycle) — Functional Components (Hooks)
209. **useEffect(() => { }, [])** — componentDidMount.
210. **useEffect(() => { return () => { } }, [])** — componentWillUnmount.
211. **useEffect(() => { }, [deps])** — componentDidUpdate (частичный).
212. **useLayoutEffect** — componentDidUpdate (синхронный).
213. **useCallback** — предотвращение создания новой функции (аналог shouldComponentUpdate).
214. **useMemo** — мемоизация значений.
215. **useRef** — сохранение значений между рендерами.

## Server Side Rendering (SSR) и Static Site Generation (SSG)
216. **ReactDOMServer.renderToString(element)** — рендеринг в строку.
217. **ReactDOMServer.renderToStaticMarkup(element)** — рендеринг без data-reactid.
218. **ReactDOMServer.renderToPipeableStream(element)** — потоковый рендеринг (React 18).
219. **ReactDOMServer.renderToReadableStream(element)** — ReadableStream (React 18).
220. **Next.js** — фреймворк для SSR/SSG.
221. **Remix** — фреймворк для SSR.
222. **Gatsby** — фреймворк для SSG.
223. **Hydration** — восстановление интерактивности на клиенте.
224. **hydrateRoot()** — гидратация в React 18.
225. **ReactDOM.hydrate()** — устаревшая гидратация.

## React 18
226. **createRoot()** — новый метод рендеринга.
227. **hydrateRoot()** — новый метод гидратации.
228. **useTransition** — хук для отложенных обновлений.
229. **useDeferredValue** — хук для отложенных значений.
230. **useId** — генерация уникальных ID.
231. **useSyncExternalStore** — синхронизация с внешними хранилищами.
232. **useInsertionEffect** — вставка стилей.
233. **startTransition(() => { })** — функция для отложенных обновлений.
234. **isPending** — состояние отложенного обновления.
235. **Automatic batching** — автоматическое группирование обновлений.
236. **Concurrent Rendering** — конкурентный рендеринг.
237. **Suspense** — улучшенная поддержка.
238. **SuspenseList** — управление порядком Suspense.
239. **Server Components** — компоненты на сервере.

## React DOM
240. **ReactDOM.render()** — устаревший рендеринг.
241. **ReactDOM.createRoot()** — новый рендеринг.
242. **ReactDOM.hydrate()** — устаревшая гидратация.
243. **ReactDOM.hydrateRoot()** — новая гидратация.
244. **ReactDOM.createPortal()** — рендеринг вне компонента.
245. **ReactDOM.findDOMNode()** — устаревший поиск DOM-узла.
246. **ReactDOM.unmountComponentAtNode()** — размонтирование компонента.
247. **ReactDOM.renderToReadableStream()** — потоковый рендеринг (React 18).
248. **ReactDOM.renderToString()** — рендеринг в строку.
249. **ReactDOM.renderToStaticMarkup()** — рендеринг без атрибутов.
250. **ReactDOM.renderToPipeableStream()** — поток в Node.js.

## React DevTools
251. **Components** — просмотр дерева компонентов.
252. **Profiler** — профилирование производительности.
253. **Hooks** — просмотр хуков.
254. **Props** — просмотр пропсов.
255. **State** — просмотр состояния.
256. **Context** — просмотр контекста.
257. **Profiler** — измерение времени рендеринга.
258. **Highlight updates** — выделение обновлённых компонентов.
259. **Suspense** — отображение Suspense.

## Оптимизация производительности
260. **React.memo** — мемоизация компонента.
261. **useCallback** — мемоизация функций.
262. **useMemo** — мемоизация значений.
263. **PureComponent** — для классовых компонентов.
264. **shouldComponentUpdate** — для классовых компонентов.
265. **lazy loading** — ленивая загрузка компонентов.
266. **Suspense** — ожидание загрузки.
267. **Code splitting** — разделение кода.
268. **Virtual list** — рендеринг только видимых элементов (react-window, react-virtualized).
269. **React.Profiler** — измерение производительности.
270. **Avoid inline functions** — не создавать функции в рендере.
271. **Avoid inline objects** — не создавать объекты в рендере.
272. **Use production build** — минимизированный код.
273. **React.Fragment** — без лишних DOM-элементов.

## React и TypeScript
274. **React.FC<Props>** — тип функционального компонента.
275. **React.ReactNode** — тип для children.
276. **React.ReactElement** — тип для элемента.
277. **React.CSSProperties** — тип для стилей.
278. **React.FormEvent<HTMLFormElement>** — событие формы.
279. **React.MouseEvent<HTMLButtonElement>** — событие мыши.
280. **React.ChangeEvent<HTMLInputElement>** — событие изменения.
281. **React.KeyboardEvent** — событие клавиатуры.
282. **React.FocusEvent** — событие фокуса.
283. **React.RefObject<HTMLInputElement>** — тип рефа.
284. **React.useRef<HTMLInputElement>(null)** — типизированный реф.
285. **React.useState<number>(0)** — типизированный state.
286. **React.useReducer<Reducer>(reducer, state)** — типизированный reducer.
287. **React.Context<Type>** — типизированный контекст.
288. **React.LazyExoticComponent** — тип для lazy компонента.
289. **React.SuspenseProps** — пропсы Suspense.
290. **React.ReactPortal** — тип для портала.

## React Router
291. **<BrowserRouter>** — роутер для браузера.
292. **<HashRouter>** — роутер с hash.
293. **<MemoryRouter>** — роутер для тестов.
294. **<Route>** — маршрут.
295. **<Routes>** — контейнер маршрутов (в v6).
296. **<Link to="/page">** — ссылка.
297. **<NavLink to="/page">** — ссылка с активным состоянием.
298. **useNavigate()** — навигация (в v6).
299. **useLocation()** — информация о местоположении.
300. **useParams()** — параметры URL.
301. **useSearchParams()** — параметры запроса.
302. **useRouteMatch()** — информация о совпадении.
303. **useOutlet()** — выходной компонент.
304. **useRoutes()** — конфигурация маршрутов.
305. **Navigate** — компонент для редиректа.
306. **Outlet** — компонент для вложенных маршрутов.
307. **BrowserRouter v6** — `import { BrowserRouter } from 'react-router-dom'`.
308. **Route v6** — `<Route path="/" element={<Home />}>`.
309. **Link v6** — `<Link to="/about">About</Link>`.
310. **useNavigate v6** — `const navigate = useNavigate(); navigate('/about')`.

## React Redux (State Management)
311. **createStore(reducer)** — создание хранилища.
312. **Provider** — провайдер для Redux.
313. **connect()** — связывание компонента с Redux.
314. **useSelector()** — получение состояния (через React-Redux).
315. **useDispatch()** — получение диспатча.
316. **dispatch(action)** — отправка действия.
317. **reducer** — функция для обработки действий.
318. **action** — объект с типом и данными.
319. **middleware** — промежуточное ПО (thunk, saga).
320. **createSlice** — создание слайса (Redux Toolkit).
321. **configureStore** — настройка хранилища (Redux Toolkit).
322. **createAsyncThunk** — асинхронные действия.

## React Query
323. **useQuery(key, fn)** — запрос данных.
324. **useMutation(fn)** — мутация данных.
325. **QueryClient** — клиент для управления кэшем.
326. **QueryClientProvider** — провайдер.
327. **useQueryClient** — доступ к клиенту.
328. **invalidateQueries(key)** — инвалидация кэша.
329. **useIsFetching** — состояние загрузки.
330. **useIsMutating** — состояние мутации.
331. **useInfiniteQuery** — бесконечная подгрузка.

## React Hook Form
332. **useForm()** — создание формы.
333. **register(name)** — регистрация поля.
334. **handleSubmit()** — обработка отправки.
335. **formState.errors** — ошибки валидации.
336. **setValue(name, value)** — установка значения.
337. **getValues()** — получение значений.
338. **reset()** — сброс формы.
339. **watch(name)** — наблюдение за полем.
340. **Controller** — для кастомных компонентов.

## ESLint плагины для React
341. **eslint-plugin-react** — правила для React.
342. **eslint-plugin-react-hooks** — правила для хуков.
343. **eslint-plugin-jsx-a11y** — доступность.
344. **eslint-plugin-react-refresh** — для React Refresh.

## Стилизация в React
345. **CSS Modules** — `import styles from './Component.module.css'`.
346. **Styled Components** — `const Button = styled.button` — CSS-in-JS.
347. **Emotion** — `css` prop.
348. **Tailwind CSS** — утилитарные классы.
349. **Inline styles** — `style={{ color: 'red' }}`.
350. **CSS-in-JS** — стили внутри JS.
351. **CSS Modules** — локальные стили.

## Тестирование React
352. **@testing-library/react** — рендеринг и взаимодействие.
353. **render(<Component />)** — рендеринг компонента.
354. **screen.getByText()** — поиск по тексту.
355. **screen.getByRole()** — поиск по роли.
356. **fireEvent** — симуляция событий.
357. **userEvent** — реалистичная симуляция.
358. **waitFor()** — ожидание асинхронных обновлений.
359. **act()** — обёртка для изменений состояния.
360. **jest** — фреймворк для тестов.
361. **React Testing Library** — подход к тестированию.

## React и Next.js
362. **next** — фреймворк для SSR/SSG.
363. **pages** — файловая маршрутизация.
364. **app** — маршрутизация на основе папок.
365. **getServerSideProps** — SSR (Server-side rendering).
366. **getStaticProps** — SSG (Static site generation).
367. **getStaticPaths** — динамические маршруты.
368. **Next.js API routes** — бэкенд-функции.
369. **next/link** — клиентская навигация.
370. **next/image** — оптимизация изображений.
371. **next/script** — загрузка скриптов.
372. **next/head** — управление head.
373. **next/font** — оптимизация шрифтов.
374. **next/dynamic** — динамический импорт.

## React и Vite
375. **vite** — быстрый сборщик.
376. **@vitejs/plugin-react** — плагин для React.
377. **@vitejs/plugin-react-swc** — плагин с SWC.
378. **vite** — HMR (Hot Module Replacement).
379. **vite** — быстрая сборка.

## React и Webpack
380. **webpack** — сборщик.
381. **babel-loader** — трансформация JSX.
382. **@babel/preset-react** — пресет для React.
383. **React Refresh** — HMR.

## Полезные библиотеки
384. **react-router-dom** — маршрутизация.
385. **react-query** — управление данными.
386. **react-hook-form** — формы.
387. **redux** — управление состоянием.
388. **redux-toolkit** — упрощённый Redux.
389. **mobx** — управление состоянием.
390. **react-spring** — анимации.
391. **framer-motion** — анимации.
392. **react-modal** — модальные окна.
393. **react-toastify** — уведомления.
394. **react-select** — кастомный select.
395. **react-datepicker** — выбор даты.
396. **react-dnd** — Drag and Drop.
397. **react-table** — таблицы.
398. **react-window** — виртуализация.
399. **react-virtualized** — виртуализация.
400. **storybook** — документация компонентов.

## Ошибки и их решение
401. **Cannot read property of undefined** — проверка props.
402. **Too many re-renders** — бесконечный цикл (setState в рендере).
403. **Hooks can only be called inside function components** — вызов хуков вне компонента.
404. **Missing key** — ключи в списках.
405. **Invalid hook call** — хуки вне React.
406. **Uncaught Error: Objects are not valid as a React child** — рендеринг объекта.
407. **React.Children.only expected to receive a single React element child** — один ребенок.
408. **Cannot update a component while rendering a different component** — обновление состояния во время рендера.
409. **Maximum update depth exceeded** — бесконечный цикл.

## Ресурсы
410. **Официальная документация** — react.dev.
411. **React Beta Docs** — новая документация.
412. **React GitHub** — исходники.
413. **Awesome React** — список ресурсов.
414. **React Ecosystem** — экосистема.
415. **React Status** — новости React.
416. **React Conferences** — конференции.

## Заключение
417. **React = компоненты + JSX + состояние + пропсы** — основа.
418. **Функциональные компоненты + хуки** — современный подход.
419. **Классовые компоненты** — устаревают.
420. **Hooks** — useState, useEffect, useContext, useReducer, useCallback, useMemo, useRef.
421. **Context** — передача данных без props drilling.
422. **SSR/SSG** — Next.js, Remix, Gatsby.
423. **Тестирование** — React Testing Library + Jest.
424. **Типизация** — TypeScript.
425. **Стилизация** — CSS Modules, Styled Components, Tailwind.
426. **Маршрутизация** — React Router.
427. **Управление состоянием** — Redux, Zustand, Jotai, MobX.
428. **Запросы** — React Query, SWR, Axios.
429. **Формы** — React Hook Form, Formik.
430. **Анимации** — Framer Motion, React Spring.
431. **Оптимизация** — memo, useCallback, useMemo, ленивая загрузка.
432. **React 18** — Concurrent Mode, Server Components.
433. **React 19** — React Compiler, Actions.
434. **Безопасность** — XSS защита.
435. **Доступность** — ARIA, правильные роли.
436. **Производительность** — избегать лишних рендеров.
437. **Сборщики** — Vite, Webpack.
438. **DevTools** — React Developer Tools.
439. **Сообщество** — огромное и активное.
440. **Будущее** — React продолжает развиваться.
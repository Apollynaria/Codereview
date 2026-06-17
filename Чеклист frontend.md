# Frontend Points  

При разработке используем eslint в текущей конфигурации.

## Основное  
  
1. Используем одинарные кавычки.
2. Не пропускаем `;`.
3. Перед ревью проверяем, что в коде не осталось случайных `console.log` и `debugger`.  
4. Для `if`, `else`, `for` и `while` всегда ставим фигурные скобки, даже если выполняется только одна строка.
5. Переменные, функции и методы называем в `camelCase.`
6. Компоненты и классы называем в `PascalCase.`
7. В многострочных объектах, массивах и импортах ставим запятую в конце. 
8. Асинхронные операции обрабатываем через `try/catch`.
9. В компонентах убираем неиспользуемые imports, props, переменные и методы.
10. Используем `optional chaining` вместо `&&` и заменяем в проекте, если видим.
11. Логические выражения пишем понятными (не используем двойное отрицание без необходимости, упрощаем выражения).
12. В сложных местах добавляем комментарии и jsdoc.
13. По возможности (с ИИ): генерировать и обновлять md-файлы модулей.

## Импорты  
  
1. Для импортов используем настроенные алиасы из `tsconfig`, чтобы не писать длинные относительные пути:
```ts
// Так
import GlobalMixin from 'src/mixins/GlobalMixin';
// Не так
import GlobalMixin from '../../../../mixins/GlobalMixin';
```
1. Общие компоненты и утилиты из библиотеки импортируем через `@tarif/component-lib`.

## TypeScript  
  
1. Типизация выполнена.
2. `any` не добавляем без причины. 
3. `as` используем только когда TypeScript не может сам вывести тип, а мы точно знаем, что лежит в значении.
4. Для новых `type`, `interface` и `enum` используем принятые префиксы: `T` для типов, `I` для интерфейсов, `E` для enum:
```ts  
type TUserFilter = {
	search: string,
	isActive: boolean,
};  
  
interface IUserInfo {
	id: string;
	name: string;
}  
  
enum EUserStatus { 
	active = 'active',
	blocked = 'blocked',
}  
```  

## Vue  
  
1. В Vue используем class components через `vue-property-decorator`.
2. Не изменяем `props` напрямую: для изменения значения используем локальное состояние, `v-model`, `.sync` / `@PropSync` или отправляем событие наверх.
3. Указываем `:key` для `v-for`.
4. Для новых actions используем `createAction`: 
```ts  
getAllDiffHeatSupplySystems = createAction<  
  EDiffHeatSupplySystemsEndpoints.getAllDiffHeatSupplySystems,  TDictionariesActionMethods>({  
  modulePath: 'dictionaries',  actionName: EDiffHeatSupplySystemsEndpoints.getAllDiffHeatSupplySystems,});  
```  
  
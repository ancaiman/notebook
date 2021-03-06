Объект ``Proxy`` «оборачивается» вокруг другого объекта и может перехватывать (и, при желании, самостоятельно обрабатывать) разные действия с ним, например чтение/запись свойств и другие.
```js 
let proxy = new Proxy(target, handler);
```

``target`` – это объект, для которого нужно сделать прокси, может быть чем угодно, включая функции.
``handler`` – конфигурация прокси: объект с «ловушками» («traps»): методами, которые перехватывают разные операции, например, ловушка ``get`` – для чтения свойства из ``target``, ловушка ``set`` – для записи свойства в ``target`` и так далее.

``Reflect`` – встроенный объект, упрощающий создание прокси.
```js
let user = {};
Reflect.set(user, 'name', 'Вася');
console.log(user.name); // Вася
```

Отключаемый (revocable) прокси – это прокси, который может быть отключён вызовом специальной функции.
```js
let {proxy, revoke} = Proxy.revocable(target, handler)
```

Запомнить:
Прокси ``!=`` оригинальный объект
Прокси не перехватывают проверку на строгое равенство ``===``
# _theory_
	- Дочерние элементы клиентского компонента АВТОматически становятся клиентскими
	- Для использования переменной из .env файла в клиентских компонентах - ее нужно сделать публичной, добавив вначале `NEXT_PUBLIC_`
	- console.log() - консоль серверных компонентов находится на сервере!
	- Стейты при изменении перерендеривают верстку компонента, а часть до return не трогают, для этого нужен useEffect
	- useState - если в качестве зависимости использовать объект или массив - то произойдет ошибка = стейт будет бесконечно перерендериваться!
		- JSON.stringify(orderList)
	- При переходе между страницами сайта с использованием <Link> стейты в не обновляются!
	- Server и Client технологии
		- Server: 
			- Midlaware, 
			- MetaData (статическая и динамическая)
		- Client: 
			- State storages: Zustand
			- AntD (некоторые компоненты)
# Язык TSX
	- MAP: использование циклов (пример: map())
		- ⚠️ Нельзя использовать пустые кавычки (<></>) - будет ошибка ключей
			- НО можно не использовать вообще ничего между вложенными map() - тогда и ключей не надо!
		- Свойство key принимает как числа так и строки
			- При множественной вложенности можно уникализировать key={'w_' + i}
	- Hook: хуки действуют только на часть после return, иначе нужно применять useEffect
	- ⚠️ Контекст исполнения: функции вызываемые событиями типа (onClick) имеют контекст исполнения при создании.
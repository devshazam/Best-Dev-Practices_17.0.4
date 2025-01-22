#
	1_ Starter - git шаблон
		1_ Для минимизации работ всегда нужно начинать с установка шаблона разработки, он должен включать:
			- AUTH - Систему авторизации с шаблонами страниц
			- State-Manager - Интегрированный Стейт-Менеджер
			- Sentry - Систему мониторинга (прмиер: Sentry) и логирования
			- ORM + DB - базу данных
			- layout - всегда серверный компонент
			- Все файлы являются модулями! - нужно ограничить входные и выходные параметры
	2_ Разработка схемы и зависимостей БД

	3_ Server-Component:
		- Meta-Tags - динамические мета теги!
		- в NextJs есть много важных ф-ций, которые доступны только в Server-Component (например: динамические мета-теги) - поэтому нужно всегда все файлы  и page оставлять серверными!
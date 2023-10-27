# # Домашняя работа №12.5 "Индексы»" - Одинцов Игорь

### Задание 1
Напишите запрос к учебной базе данных, который вернёт процентное отношение общего размера всех индексов к общему размеру всех таблиц.

### Ответ

![Z1 1](https://github.com/Bestenar/12.5-Index-hw/assets/111271419/6d7974de-b839-4474-97a4-866eeccad6f5)

![Z1 2](https://github.com/Bestenar/12.5-Index-hw/assets/111271419/8f393242-705e-4874-b791-befbe1879eef)

---

### Задание 2
Выполните explain analyze следующего запроса:
```ruby
select distinct concat(c.last_name, ' ', c.first_name), sum(p.amount) over (partition by c.customer_id, f.title)
from payment p, rental r, customer c, inventory i, film f
where date(p.payment_date) = '2005-07-30' and p.payment_date = r.rental_date and r.customer_id = c.customer_id and i.inventory_id = r.inventory_id
```
- перечислите узкие места;
- оптимизируйте запрос: внесите корректировки по использованию операторов, при необходимости добавьте индексы.

### Ответ
Узкие места наблюдаются в момент использования оконных функций OVER и PARTITION BY, а так же в момент фильтрации вывода, в сравнении колонок из разных таблиц.

![Z2 1](https://github.com/Bestenar/12.5-Index-hw/assets/111271419/124c0582-1881-41a1-ae8e-263ab41aa174)

![Z2 2](https://github.com/Bestenar/12.5-Index-hw/assets/111271419/d0432c25-4231-4b4b-b359-d7f2efb4bacb)

Оптимизация

![Z2 3](https://github.com/Bestenar/12.5-Index-hw/assets/111271419/df00e40e-efff-4e0d-9214-73557d54bc25)

![Z2 4](https://github.com/Bestenar/12.5-Index-hw/assets/111271419/c7c87ccd-7f4d-4cb0-9a31-f1c43c637c95)

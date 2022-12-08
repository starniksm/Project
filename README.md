### Постановка задачи

Реализуйте дополнительный статус экземпляра книги, позволяющий не отображать информацию об экземпляре книги при просмотре страницы книги.

### Краткий комментарий к решению задачи

Для решения данного задания в файл `book_detail.html` был добавлен фрагмент кода, который проверял на наличие доступа к просмотру данной книги с соотвествующим статусом его экземпляра, а именно было необходимо наличие статуса суперпользователя. Если аккаунт имел суперпользователя, то ему показывались книги со статусом "потеряно" ( данный статус был добавлен в админ-панеле ), если не имел, то соответственно - не показывались.
```
- {% if user.is_superuser %} – проверка на суперпользователя
- {% if copy.status.id == 4 %} – проверка на принадлежность к статусу экземпляра книги "Потеряно".
```

Таким образом весь код выглядел как проверка на 2 условия:
```
    {% for copy in book.bookinstance_set.all %}
    {% if user.is_superuser %}
      {% if copy.status.id == 4 %}

      ...

      {%endif%}

    {% else %}
      {% if copy.status.id != 4 %}

      ...

      {%endif%}
    {%endif%}
```
# ✅ Functional Requirements

Цей документ визначає функціональні вимоги до веб-платформи, яка призначена для підтримки навчального процесу, оцінювання знань студентів, надання рекомендацій на основі результатів тестування, а також забезпечення адміністративного управління та аналітики.

---

## 1. 👥 Користувачі та аутентифікація

### 1.1 Реєстрація та вхід
- Система повинна дозволяти створення облікових записів користувачів (студентів, викладачів, адміністраторів).
- Під час реєстрації мають збиратися основні персональні дані (ПІБ, email, пароль тощо).
- Аутентифікація повинна здійснюватися за допомогою JWT або сесій.
- Реалізувати функціонал відновлення паролю через email.

### 1.2 Авторизація та ролі
- Права доступу повинні бути розмежовані за ролями:
  - Студент (участь у курсах, тестування, перегляд рекомендацій)
  - Викладач (створення курсів, тестів, перегляд статистики)
  - Адміністратор (повне управління даними та користувачами)

---

## 2. 📚 Управління навчальним контентом

### 2.1 Курси та модулі
- Викладач повинен мати змогу створювати, редагувати та видаляти курси.
- Кожен курс повинен містити:
  - Назву, опис, категорію
  - Модулі з навчальними матеріалами (відео, текст, pdf тощо)
  - Тестові завдання

### 2.2 Пошук і підписка
- Студенти повинні мати можливість:
  - Переглядати список доступних курсів
  - Фільтрувати та шукати за ключовими словами
  - Підписуватись або відписуватись від курсів

---

## 3. 🧪 Система тестування

### 3.1 Проведення тестів
- Система повинна підтримувати створення тестів з варіантами відповідей.
- Тести можуть мати обмеження за часом та кількістю спроб.

### 3.2 Оцінювання
- Після проходження тесту система має автоматично оцінити відповіді.
- Повинна надаватися детальна розбивка результатів:
  - Загальна оцінка
  - Питання з правильними/неправильними відповідями
  - Теми, які потребують покращення

### 3.3 Збереження історії
- Усі спроби проходження тестів мають зберігатися для подальшого аналізу.
- Користувач повинен мати доступ до своєї історії тестування.

---

## 4. 🤖 Рекомендаційна система

### 4.1 Побудова профілю студента
- На основі результатів тестів та активності формується навчальний профіль користувача.

### 4.2 Генерація рекомендацій
- Система повинна надавати індивідуальні рекомендації:
  - Які курси пройти далі
  - Які теми слід повторити
  - Прогнозована складність матеріалів

### 4.3 Модель машинного навчання
- В основі рекомендацій — модель класифікації рівня знань студента.
- Модель має бути інтегрована через фонові завдання (наприклад, Celery task).

---

## 5. 📈 Аналітика та звіти

### 5.1 Для студентів
- Візуалізація прогресу по модулях та курсах.
- Індивідуальні графіки результатів з часом.

### 5.2 Для викладачів
- Статистика по успішності групи студентів.
- Виявлення слабких тем на основі агрегованих даних.
- Можливість експорту звітів у CSV / Excel.

---

## 6. 🔔 Повідомлення та зворотний зв’язок

### 6.1 Комунікація
- Система повинна дозволяти викладачу надсилати повідомлення студентам.
- Опціонально: email-нотифікації або внутрішній чат.

### 6.2 Збір фідбеку
- Після завершення курсу студент може залишити оцінку та коментар.
- Дані фідбеку повинні бути доступні викладачу в аналітичному вигляді.

---

## 7. ⚙️ Панель адміністратора

- Адміністратор повинен мати змогу:
  - Переглядати та редагувати список користувачів
  - Видаляти або блокувати облікові записи
  - Переглядати загальну статистику використання системи
  - Керувати курсами, категоріями, правами доступу

---

## 8. 🔐 Безпека та аудит

- Усі паролі зберігаються у хешованому вигляді (bcrypt або Argon2).
- Впроваджено захист від XSS, CSRF, SQL-ін’єкцій.
- Доступ до API захищено токенами.
- Ведення логів активності (MongoDB) — спроби входу, помилки, підозріла активність.

---

## 9. 🌐 Інтерфейс користувача

- Платформа має бути адаптована під мобільні пристрої (responsive UI).
- Темна / світла тема (опціонально).
- Підтримка мультимовності (у майбутніх версіях).

---

## 10. 🛠 Додаткові вимоги

- Під час реєстрації перевіряти унікальність email та мінімальну складність паролю.
- Питання тестів можуть містити зображення та фрагменти коду.
- Кожен курс може мати перелік рекомендованих або обовʼязкових попередніх курсів (пререквізити).
- Система повинна надсилати сповіщення про майбутні дедлайни та важливі події.
- Всі дії користувачів мають бути зафіксовані для аудиту.
- API має бути задокументовано для інтеграції з іншими системами (наприклад, через Swagger/OpenAPI).

---

📌 **Примітка:** Усі функціональні вимоги будуть перевірені за допомогою модульного, інтеграційного та E2E-тестування згідно з планом тестування (`testing_plan.md`).

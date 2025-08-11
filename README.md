# 🏥 АИС РУПОИ - Автоматизированная информационная система РУПОИ

Современная веб-система для управления личными делами, заказами, накладными и складскими операциями в Республиканском управлении протезно-ортопедических изделий (РУПОИ).

## ✨ Основные возможности

### 🔐 Система ролей и доступа
- **Регистратура** - управление личными делами пациентов
- **Медицинский отдел** - работа с ИПРА и медицинскими показаниями
- **Мастерские** - создание и отслеживание заказов
- **Склад** - управление запасами и выдача изделий
- **Администрация** - полный доступ к системе

### 📋 Модули системы
- **Личные дела** - картотека пациентов с полной медицинской историей
- **Заказы** - создание и отслеживание заказов на ТСР
- **Накладные** - управление выдачей готовых изделий
- **Склад** - учет запасов и контроль движения материалов
- **Отчеты** - аналитика и статистика по всем процессам

## 🚀 Технологический стек

### Backend
- **Django 5.0.2** - основной веб-фреймворк
- **Django REST Framework** - API для фронтенда
- **Django CORS Headers** - поддержка кросс-доменных запросов
- **Django Simple JWT** - JWT аутентификация
- **SQLite/PostgreSQL** - база данных
- **Django Import Export** - импорт/экспорт данных

### Frontend
- **HTML5 + CSS3** - современная разметка и стили
- **JavaScript (ES6+)** - интерактивность и логика
- **CSS Grid & Flexbox** - адаптивная верстка
- **CSS Variables** - единая система дизайна
- **Responsive Design** - поддержка всех устройств

### Дополнительные технологии
- **REST API** - архитектура взаимодействия
- **JWT токены** - безопасная аутентификация
- **CORS** - кросс-доменные запросы
- **Git** - система контроля версий

## 📦 Установка и запуск

### Предварительные требования
- Python 3.8+
- Node.js 16+ (для разработки)
- Git

### 1. Клонирование репозитория
```bash
git clone https://github.com/your-username/rupoi-ais.git
cd rupoi-ais
```

### 2. Настройка Backend (Django)
```bash
cd backend

# Создание виртуального окружения
python -m venv venv

# Активация виртуального окружения
# Windows:
venv\Scripts\activate
# Linux/Mac:
source venv/bin/activate

# Установка зависимостей
pip install -r requirements.txt

# Применение миграций
python manage.py migrate

# Создание суперпользователя
python manage.py createsuperuser

# Запуск сервера
python manage.py runserver
```

### 3. Настройка Frontend
```bash
cd frontend/rupoi-frontend

# Установка зависимостей
npm install

# Запуск в режиме разработки
npm run dev

# Сборка для продакшена
npm run build
```

### 4. Быстрый запуск
Просто откройте файл `frontend/index.html` в браузере для просмотра интерфейса.

## 🔧 Конфигурация

### Переменные окружения
Создайте файл `.env` в папке `backend`:

```env
DEBUG=True
SECRET_KEY=your-secret-key-here
DB_NAME=rupoi
DB_USER=postgres
DB_PASSWORD=your-password
DB_HOST=localhost
DB_PORT=5432
```

### Настройки базы данных
По умолчанию используется SQLite. Для PostgreSQL измените настройки в `backend/config/settings.py`.

## 📱 Использование

### Вход в систему
Используйте тестовые аккаунты:
- **Регистратура**: `registry` / `test123`
- **Медицинский отдел**: `medical` / `test123`
- **Мастерские**: `workshop` / `test123`
- **Склад**: `warehouse` / `test123`
- **Администратор**: `admin` / `admin123`

### Основные операции
1. **Создание личного дела** - регистрация нового пациента
2. **Создание заказа** - оформление заказа на ТСР
3. **Управление складом** - учет запасов и выдача
4. **Формирование отчетов** - аналитика по всем процессам

## 🏗️ Архитектура проекта

```
rupoi-ais/
├── backend/                 # Django backend
│   ├── accounts/           # Управление пользователями
│   ├── personal_cases/     # Личные дела пациентов
│   ├── orders/            # Заказы на ТСР
│   ├── invoices/          # Накладные
│   ├── warehouse/         # Складские операции
│   ├── dictionaries/      # Справочники
│   └── config/            # Настройки Django
├── frontend/               # Frontend интерфейс
│   ├── index.html         # Главная страница
│   ├── orders.html        # Модуль заказов
│   ├── invoices.html      # Модуль накладных
│   ├── warehouse.html     # Модуль склада
│   ├── dashboard.html     # Дашборд
│   ├── login.html         # Страница входа
│   └── api-integration.js # API интеграция
└── docs/                  # Документация
```

## 🔒 Безопасность

- JWT токены для аутентификации
- Ролевая система доступа
- CORS настройки для API
- Валидация данных на всех уровнях
- Защита от SQL-инъекций

## 📊 API Endpoints

### Аутентификация
- `POST /api/auth/login/` - вход в систему
- `POST /api/auth/logout/` - выход из системы
- `POST /api/auth/refresh/` - обновление токена

### Личные дела
- `GET /api/personal-cases/` - список личных дел
- `POST /api/personal-cases/` - создание личного дела
- `GET /api/personal-cases/{id}/` - просмотр личного дела
- `PUT /api/personal-cases/{id}/` - редактирование

### Заказы
- `GET /api/orders/` - список заказов
- `POST /api/orders/` - создание заказа
- `GET /api/orders/{id}/` - просмотр заказа
- `PUT /api/orders/{id}/` - редактирование

### Склад
- `GET /api/warehouse/stock/` - складские запасы
- `GET /api/warehouse/issues/` - выдача со склада
- `POST /api/warehouse/stock/` - добавление позиции

## 🧪 Тестирование

```bash
# Backend тесты
cd backend
python manage.py test

# Frontend тесты (если настроены)
cd frontend/rupoi-frontend
npm test
```

## 📈 Развертывание

### Production настройки
1. Измените `DEBUG = False` в settings.py
2. Настройте PostgreSQL базу данных
3. Настройте статические файлы
4. Используйте Gunicorn или uWSGI
5. Настройте Nginx как reverse proxy

### Docker (опционально)
```bash
docker-compose up -d
```

## 🤝 Вклад в проект

1. Fork репозитория
2. Создайте feature branch (`git checkout -b feature/amazing-feature`)
3. Commit изменения (`git commit -m 'Add amazing feature'`)
4. Push в branch (`git push origin feature/amazing-feature`)
5. Откройте Pull Request

## 📝 Лицензия

Этот проект распространяется под лицензией MIT. См. файл `LICENSE` для подробностей.

## 📞 Поддержка

- **Email**: support@rupoi.kg
- **Документация**: [Wiki проекта](https://github.com/your-username/rupoi-ais/wiki)
- **Issues**: [GitHub Issues](https://github.com/your-username/rupoi-ais/issues)

## 🙏 Благодарности

- Команде разработчиков РУПОИ
- Сообществу Django и Vue.js
- Всем участникам проекта

---

**АИС РУПОИ** - современное решение для управления протезно-ортопедическими изделиями в Кыргызстане 🇰🇬

FROM python:3.14-alpine

# Директория приложения
WORKDIR /app

# Копирование списка зависимостей
COPY requirements.txt .

RUN pip install -r requirements.txt --no-cache-dir

# Копирование файлов сервиса
COPY . .

# Пользователь сервиса
RUN useradd -m -r appuser && chown -R appuser /app
USER appuser

# Папки для медиа и статистики
RUN mkdir -p /app/collected_static /app/media
# Запуск сервиса
CMD ["sh","-c","python manage.py collectstatic --noinput && python manage.py migrate && python manage.py runserver 0.0.0.0:8000"]
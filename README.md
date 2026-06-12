Проект представляет собой аналитический pipeline для загрузки Excel-бланков OEE, расчёта производственных показателей, выявления недельных отклонений и формирования отчётных графиков по оборудованию.

Назначение проекта

Система предназначена для автоматизации анализа производственных событий по станкам. На вход подаются Excel-файлы с событиями простоев, потерями времени и данными по выпуску продукции. После обработки данные загружаются в PostgreSQL, где формируется единая база событий и рассчитываются аналитические показатели.

Основные задачи проекта:

Загрузка Excel-файлов из заданной структуры папок;
Извлечение событий, интервалов времени и длительности простоев;
Загрузка нормализованных данных в PostgreSQL;
Расчёт дневного OEE по каждому станку;
Анализ отклонений последней отчётной недели от исторического уровня;
Построение графиков по простоям и OEE;
Сохранение Excel-отчётов и PNG-графиков;
Отправка отчётов по email при наличии SMTP-настроек.
Используемый стек: Python 3.12+ pandas numpy matplotlib openpyxl SQLAlchemy psycopg2 PostgreSQL Запуск

Установите зависимости:

pip install pandas numpy matplotlib openpyxl sqlalchemy psycopg2-binary

Настройте переменные окружения:

OEE_DB_URL= field(default_factory=lambda: os.getenv("OEE_DB_URL", "")) OEE_SMTP_USER=your_email@gmail.com OEE_SMTP_PASSWORD=your_app_password OEE_EMAIL_RECIPIENT=recipient@example.com

Запуск pipeline:

run_pipeline(CFG) Результаты работы

После выполнения в папке reports формируются:

weekly_deviation_report.xlsx weekly_oee_deviation_report.xlsx weekly_deviation_top_events.png weekly_oee_deviation_by_machine.png

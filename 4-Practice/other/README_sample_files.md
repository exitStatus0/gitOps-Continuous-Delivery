# Примеры файлов для практической работы ArgoCD

Этот каталог содержит примеры файлов, которые вы можете использовать для выполнения практической работы.

## Структура каталога

```
sample-files/
├── apps/                           # Манифесты ArgoCD Application
    ├── cogitator-dev.yaml       # Application для среды Dev
    ├── cogitator-qa.yaml        # Application для среды QA
    └── cogitator-prod.yaml      # Application для среды Production
├── charts/                         # Helm-чарты
    └── cogitator/               # Чарт сервиса уведомлений
        ├── Chart.yaml              # Метаданные чарта
        ├── templates/              # Шаблоны манифестов Kubernetes
        │   ├── deployment.yaml
        │   ├── service.yaml
        │   ├── _helpers.tpl
        │   └── NOTES.txt
        ├── values.yaml             # Значения по умолчанию
        ├── values-dev.yaml         # Переопределения для среды Dev
        ├── values-qa.yaml          # Переопределения для среды QA
        └── values-prod.yaml        # Переопределения для среды Production
├── app-of-apps.yaml                # Манифест App of Apps
└── README.md                       # Этот файл
```

## Использование

1. **Скопируйте в свой GitOps репозиторий:**
   ```bash
   cp -r sample-files/* /path/to/your/gitops-repo/
   ```

2. **Обновите `repoURL` в манифестах Application:**
   Замените `https://github.com/your-org/gitops-config-repo` на актуальный URL вашего репозитория.

3. **Зафиксируйте изменения и отправьте их (commit & push):**
   ```bash
   cd /path/to/your/gitops-repo/
   git add .
   git commit -m "Add cogitator service configuration"
   git push origin main
   ```

4. **Следуйте инструкциям лабораторной работы** в `other/PracticeLab.md`, `EN/PracticeLab.md` или `UA/ПрактичнаРобота.md`.

## Настройка (Customization)

Вы можете свободно настраивать:
- **Image**: По умолчанию используется `nginx`. Вы можете изменить его на любой другой образ контейнера.
- **Resources**: Настройте лимиты CPU и памяти в зависимости от мощности вашего кластера.
- **Replicas**: Измените количество реплик для разных сред.
- **Repository URL**: Обновите ссылку на ваш актуальный Git-репозиторий.

## Примечания

- Helm-чарт использует nginx в качестве образа по умолчанию для демонстрационных целей.
- Все Applications настроены с параметром `CreateNamespace=true` для автоматического создания пространств имен.
- Для Application в среде Production включен параметр `selfHeal: true` для автоматического исправления отклонений (drift correction).

Удачного погружения в GitOps! 🚀

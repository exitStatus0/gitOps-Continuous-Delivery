# GitOps: Continuous Delivery & ArgoCD

> **Languages:** [English](#english-version) | [Українська](#українська-версія) | [Русский](#русская-версия)

---

## English Version

This repository is a practical course on Continuous Delivery, GitOps, and ArgoCD. It is designed to take you from first principles to hands-on implementation without losing the larger picture.

### The Parable of the Sacred Repository

High in the mountains of DevOps, there lived a wise monk named Git. He tended a sacred repository, a garden of digital order, where the desired state and the actual state were meant to live in harmony.

One day, a young apprentice named Ops arrived at the monastery. Ops was diligent and sincere, yet chaos followed every manual action. He planted here, watered there, pruned elsewhere, and still the storms would come: servers failed, configurations drifted, and the garden slipped back into disorder.

"Master," Ops asked, "how can I keep the garden whole when everything changes?"

Git answered, "Do not chase every leaf by hand. Describe the garden as it ought to be. Write down not the steps, but the state. Place that declaration in the sacred repository, and let the garden return to it again and again."

So Ops learned to write manifests: "Let there be three cherry trees in the east, watered at dawn. Let a stone path lead to the meditation hall." He committed these declarations to the repository, and through automation, or what the monk called continuous reconciliation, the garden kept finding its way back to balance.

When storms came, the garden healed. When wandering feet disturbed the paths, the paths reappeared. When the seasons changed, the garden adapted according to what had been declared.

The lesson was simple: **GitOps is not about issuing commands; it is about declaring the state you want and letting the system continuously reconcile reality to match it**. With version control, change becomes visible. With automation, human error is reduced. With auditability, trust is preserved.

And so Ops grew wiser, and the garden flourished in quiet, repeatable harmony.

If we leave the metaphor for a moment, that is exactly what this course is about:

### What You'll Learn

<p align="center">
  <img src="GitOps.png" alt="GitOps Overview" width="700"/>
</p>

GitOps was coined in 2017 by Alexis Richardson, CEO of Weaveworks, as a way to apply software development best practices such as version control, automation, and collaboration to infrastructure operations. Today, it is one of the standard approaches for managing Kubernetes deployments at scale.

This course is built to take you from first contact with the ideas to confident, practical use. By the end, you will be able to:

- **Understand Continuous Delivery** — see how pipelines work, why safe and frequent delivery matters, and where CD fits in modern engineering
- **Think in GitOps** — use Git as the single source of truth for infrastructure and deployments
- **Deploy with ArgoCD** — install it, configure it, and manage applications through ArgoCD resources
- **Build real-world setups** — use the App-of-Apps pattern, multi-environment Helm charts, automated sync, and self-healing
- **Avoid common pitfalls** — apply practical guidance around security, observability, and day-to-day operations

### Course Roadmap

| # | Module | Topic | Go to |
|---|--------|-------|-------|
| 0 | Introduction to CD | Continuous Delivery fundamentals | [EN](0-Introduction-CD/EN/IntroductionToCD.md) \| [UA](0-Introduction-CD/UA/ВступДоCD.md) \| [RU](0-Introduction-CD/other/IntroductionToCD.md) |
| 1 | Introduction to GitOps | GitOps principles & history | [EN](1-Intrduction-GitOps/EN/IntroductionToGitOps.md) \| [UA](1-Intrduction-GitOps/UA/ВступДоGitOps.md) \| [RU](1-Intrduction-GitOps/other/IntroductionToGitOps.md) |
| 2 | Introduction to ArgoCD | Architecture & core concepts | [EN](2-Introduction-to-ArgoCD/EN/IntroductionToArgoCD.md) \| [UA](2-Introduction-to-ArgoCD/UA/ВступДоArgoCD.md) \| [RU](2-Introduction-to-ArgoCD/other/IntroductionToArgoCD.md) |
| 3 | ArgoCD Applications | Custom Resource Definitions | [EN](3-CRD-ArgoCD/EN/IntroductionToArgoApplications.md) \| [UA](3-CRD-ArgoCD/UA/АплікаціяArgoCD.md) \| [RU](3-CRD-ArgoCD/other/IntroductionToArgoApplications.md) |
| 4 | Practice Lab | Hands-on deployment with ArgoCD | [EN](4-Practice/EN/PracticeLab.md) \| [UA](4-Practice/UA/ПрактичнаРобота.md) \| [RU](4-Practice/other/PracticeLab.md) |
| 5 | Conclusion | Summary & next steps | [EN](5-Conclusion/EN/Conclusion.md) \| [UA](5-Conclusion/UA/Висновок.md) \| [RU](5-Conclusion/other/Conclusion.md) |

Each module includes a short quiz to reinforce understanding.

### Who Is This For

- **DevOps Engineers** looking to adopt GitOps workflows
- **SREs & Platform Engineers** building self-healing infrastructure
- **Developers** moving into infrastructure and deployment automation
- **Team Leads** evaluating GitOps for their organizations

You do not need prior ArgoCD experience. Familiarity with Git and basic Kubernetes concepts will help.

### Prerequisites & Getting Started

If you want to follow along with the practice lab, you will need kubectl, a local Kubernetes cluster, and ArgoCD installed. The full setup guide is here:

**[Prerequisites Installation Guide](4-Practice/PrerequisitesInstallation.md)**

---

## Українська версія

Цей репозиторій — практичний курс про Continuous Delivery, GitOps і ArgoCD. Він побудований так, щоб провести вас від базових принципів до реального застосування, не втрачаючи цілісної картини.

### Притча про священне сховище

Високо в горах DevOps жив мудрий монах на ім'я Git. Він доглядав священне сховище — сад цифрового порядку, де бажаний стан і реальність мали перебувати в злагоді.

Одного дня до монастиря прийшов молодий учень на ім'я Ops. Він був старанним і щирим, але щоразу, коли намагався втримати все вручну, його наздоганяв хаос. Тут посіяв, там полив, десь підправив, а потім приходили бурі змін: сервери виходили з ладу, конфігурації дрейфували, і сад знову втрачав лад.

"Учителю," запитав Ops, "як мені зберегти цей сад, якщо все постійно змінюється?"

Мудрий Git відповів: "Не намагайся наздогнати кожен листок вручну. Опиши сад таким, яким він має бути. Записуй не кроки, а стан. Збережи це в моєму священному сховищі, і нехай сад знову й знову повертається до цієї істини."

Так Ops навчився писати маніфести: "Нехай на сході ростуть три вишні, які поливають на світанку. Нехай кам'яна стежка веде до зали медитації." Він фіксував ці декларації у сховищі, і завдяки автоматизації, яку монах називав безперервним узгодженням, сад сам повертався до ладу.

Коли приходили бурі, сад зцілювався. Коли відвідувачі витоптували стежки, вони відновлювалися. Коли змінювалися пори року, сад пристосовувався до того, що було задекларовано.

Висновок був простий: **GitOps — це не про ручні дії, а про чітке визначення бажаного стану і безперервне приведення реальності у відповідність до нього**. Завдяки контролю версій зміни стають прозорими. Завдяки автоматизації зменшується кількість людських помилок. Завдяки історії змін зберігається довіра до системи.

І так Ops подорослішав як інженер, а сад розквітав у спокійній і передбачуваній гармонії.

Якщо відкласти метафору, саме цьому і присвячений курс:

### Що ви вивчите

<p align="center">
  <img src="GitOps.png" alt="GitOps Огляд" width="700"/>
</p>

Термін GitOps з'явився у 2017 році завдяки Алексісу Річардсону, CEO Weaveworks, як спроба перенести найкращі практики розробки — контроль версій, автоматизацію та командну співпрацю — в управління інфраструктурою. Сьогодні цей підхід став одним із галузевих стандартів для Kubernetes-розгортань у масштабі.

Цей курс проведе вас від першого знайомства з темою до впевненої практики. Після завершення ви зможете:

- **Розуміти Continuous Delivery** — бачити принципи, роль пайплайнів і цінність швидкого та безпечного постачання змін
- **Мислити в GitOps** — використовувати Git як єдине джерело істини для інфраструктури та розгортань
- **Працювати з ArgoCD** — встановлювати його, налаштовувати й керувати додатками через ресурси ArgoCD
- **Будувати наближені до реальності сценарії** — App-of-Apps, Helm-чарти для кількох середовищ, автосинхронізація та самовідновлення
- **Уникати типових помилок** — враховувати безпеку, спостережуваність і щоденну експлуатацію

### Дорожня карта курсу

| # | Модуль | Тема | Перейти |
|---|--------|------|---------|
| 0 | Вступ до CD | Основи Continuous Delivery | [EN](0-Introduction-CD/EN/IntroductionToCD.md) \| [UA](0-Introduction-CD/UA/ВступДоCD.md) \| [RU](0-Introduction-CD/other/IntroductionToCD.md) |
| 1 | Вступ до GitOps | Принципи та історія GitOps | [EN](1-Intrduction-GitOps/EN/IntroductionToGitOps.md) \| [UA](1-Intrduction-GitOps/UA/ВступДоGitOps.md) \| [RU](1-Intrduction-GitOps/other/IntroductionToGitOps.md) |
| 2 | Вступ до ArgoCD | Архітектура та основні концепції | [EN](2-Introduction-to-ArgoCD/EN/IntroductionToArgoCD.md) \| [UA](2-Introduction-to-ArgoCD/UA/ВступДоArgoCD.md) \| [RU](2-Introduction-to-ArgoCD/other/IntroductionToArgoCD.md) |
| 3 | Додатки ArgoCD | Custom Resource Definitions | [EN](3-CRD-ArgoCD/EN/IntroductionToArgoApplications.md) \| [UA](3-CRD-ArgoCD/UA/АплікаціяArgoCD.md) \| [RU](3-CRD-ArgoCD/other/IntroductionToArgoApplications.md) |
| 4 | Практична робота | Практичне розгортання з ArgoCD | [EN](4-Practice/EN/PracticeLab.md) \| [UA](4-Practice/UA/ПрактичнаРобота.md) \| [RU](4-Practice/other/PracticeLab.md) |
| 5 | Висновок | Підсумки та наступні кроки | [EN](5-Conclusion/EN/Conclusion.md) \| [UA](5-Conclusion/UA/Висновок.md) \| [RU](5-Conclusion/other/Conclusion.md) |

Кожен модуль містить короткий тест, щоб закріпити матеріал.

### Для кого цей курс

- **DevOps-інженери**, які хочуть впровадити GitOps-підхід
- **SRE та Platform-інженери**, що будують інфраструктуру із самовідновленням
- **Розробники**, які переходять до автоматизації інфраструктури та розгортання
- **Тімліди**, що оцінюють GitOps для своїх організацій

Попередній досвід роботи з ArgoCD не потрібен. Базове розуміння Kubernetes і Git буде перевагою.

### Передумови та початок роботи

Якщо ви хочете пройти практичну лабораторну разом із матеріалом, вам знадобляться kubectl, локальний Kubernetes-кластер і встановлений ArgoCD. Повний гайд з налаштування:

**[Гайд з встановлення передумов](4-Practice/PrerequisitesInstallation.md)**

---

## Русская версия

Этот репозиторий — практический курс по Continuous Delivery, GitOps и ArgoCD. Он выстроен так, чтобы провести вас от базовых принципов к реальной практике и при этом не потерять общую картину.

### Притча о священном хранилище

Высоко в горах DevOps жил мудрый монах по имени Git. Он хранил священное хранилище — сад цифрового порядка, где желаемое состояние и реальность должны были находиться в согласии.

Однажды в монастырь пришёл молодой ученик по имени Ops. Он был старательным и искренним, но всякий раз, когда пытался удержать всё вручную, его настигал хаос. Тут он что-то сажал, там поливал, где-то подрезал, но затем приходили бури перемен: серверы выходили из строя, конфигурации дрейфовали, и сад снова терял стройность.

"Учитель," спросил Ops, "как мне сохранить этот сад, если всё вокруг постоянно меняется?"

Мудрый Git ответил: "Не пытайся догонять каждый лист вручную. Опиши сад таким, каким он должен быть. Записывай не шаги, а состояние. Сохрани эту декларацию в священном хранилище, и пусть сад снова и снова возвращается к ней."

Так Ops научился писать манифесты: "Пусть на востоке растут три вишнёвых дерева, которые поливают на рассвете. Пусть каменная тропа ведёт к залу медитации." Он фиксировал эти декларации в хранилище, и благодаря автоматизации, которую монах называл непрерывным согласованием, сад сам возвращался к порядку.

Когда приходили бури, сад исцелялся. Когда посетители вытаптывали тропы, они восстанавливались. Когда сменялись времена года, сад приспосабливался к тому, что было задекларировано.

Урок был прост: **GitOps — это не про ручные действия, а про ясное описание желаемого состояния и постоянное приведение реальности в соответствие с ним**. Контроль версий делает изменения прозрачными. Автоматизация сокращает число человеческих ошибок. История изменений сохраняет доверие к системе.

Так Ops вырос как инженер, а сад расцветал в спокойной, предсказуемой гармонии.

Если отойти от метафоры, именно этому и посвящён курс:

### Что вы изучите

<p align="center">
  <img src="GitOps.png" alt="GitOps Обзор" width="700"/>
</p>

Термин GitOps появился в 2017 году благодаря Алексису Ричардсону, CEO Weaveworks, как способ перенести лучшие практики разработки — контроль версий, автоматизацию и совместную работу — в управление инфраструктурой. Сегодня этот подход стал одним из отраслевых стандартов для Kubernetes-развёртываний в масштабе.

Этот курс проведёт вас от первого знакомства с темой к уверенной практике. После завершения вы сможете:

- **Понимать Continuous Delivery** — видеть принципы, роль пайплайнов и ценность быстрого и безопасного выпуска изменений
- **Мыслить в GitOps** — использовать Git как единый источник истины для инфраструктуры и развёртываний
- **Работать с ArgoCD** — устанавливать его, настраивать и управлять приложениями через ресурсы ArgoCD
- **Строить сценарии, близкие к реальности** — App-of-Apps, Helm-чарты для нескольких сред, автосинхронизация и самовосстановление
- **Избегать типичных ошибок** — учитывать безопасность, наблюдаемость и повседневную эксплуатацию

### Дорожная карта курса

| # | Модуль | Тема | Перейти |
|---|--------|------|---------|
| 0 | Введение в CD | Основы Continuous Delivery | [EN](0-Introduction-CD/EN/IntroductionToCD.md) \| [UA](0-Introduction-CD/UA/ВступДоCD.md) \| [RU](0-Introduction-CD/other/IntroductionToCD.md) |
| 1 | Введение в GitOps | Принципы и история GitOps | [EN](1-Intrduction-GitOps/EN/IntroductionToGitOps.md) \| [UA](1-Intrduction-GitOps/UA/ВступДоGitOps.md) \| [RU](1-Intrduction-GitOps/other/IntroductionToGitOps.md) |
| 2 | Введение в ArgoCD | Архитектура и основные концепции | [EN](2-Introduction-to-ArgoCD/EN/IntroductionToArgoCD.md) \| [UA](2-Introduction-to-ArgoCD/UA/ВступДоArgoCD.md) \| [RU](2-Introduction-to-ArgoCD/other/IntroductionToArgoCD.md) |
| 3 | Приложения ArgoCD | Custom Resource Definitions | [EN](3-CRD-ArgoCD/EN/IntroductionToArgoApplications.md) \| [UA](3-CRD-ArgoCD/UA/АплікаціяArgoCD.md) \| [RU](3-CRD-ArgoCD/other/IntroductionToArgoApplications.md) |
| 4 | Практическая работа | Практическое развёртывание с ArgoCD | [EN](4-Practice/EN/PracticeLab.md) \| [UA](4-Practice/UA/ПрактичнаРобота.md) \| [RU](4-Practice/other/PracticeLab.md) |
| 5 | Заключение | Итоги и следующие шаги | [EN](5-Conclusion/EN/Conclusion.md) \| [UA](5-Conclusion/UA/Висновок.md) \| [RU](5-Conclusion/other/Conclusion.md) |

Каждый модуль включает короткий тест, чтобы закрепить материал.

### Для кого этот курс

- **DevOps-инженеры**, желающие внедрить GitOps-подход
- **SRE и Platform-инженеры**, строящие инфраструктуру с самовосстановлением
- **Разработчики**, переходящие к автоматизации инфраструктуры и развёртывания
- **Тимлиды**, оценивающие GitOps для своих организаций

Предыдущий опыт работы с ArgoCD не требуется. Базовое понимание Kubernetes и Git будет полезным.

### Предварительные требования

Если вы хотите проходить практическую лабораторную вместе с материалом, вам понадобятся kubectl, локальный Kubernetes-кластер и установленный ArgoCD. Полное руководство по настройке:

**[Руководство по установке](4-Practice/PrerequisitesInstallation.md)**

---

*This course is designed to guide you from GitOps fundamentals to practical, production-minded implementation. May your infrastructure remain close to the state you declare.*

*Цей курс створено, щоб провести вас від основ GitOps до практичної, наближеної до реальності реалізації. Нехай ваша інфраструктура завжди лишається вірною задекларованому стану.*

*Этот курс создан, чтобы провести вас от основ GitOps к практической, приближенной к реальности реализации. Пусть ваша инфраструктура всегда остаётся верной задекларированному состоянию.*

# WallStack SRE Lab

**Учебная B2B-платформа. Строится руками в ходе 100-дневного курса DevOps / SRE.**

**Автор:** Andrey S. Yarovenko (WallStack)
**Создано:** 2026-10-10
**Старт разработки:** 2026-11-01
**Связанный курс:** [wallstack-sre-core](https://github.com/wss-ccg/wallstack-sre-core) (приватный)
**Статус:** 🟡 В разработке (день 0 из 100)

---

## 🎯 ЦЕЛЬ ПРОЕКТА

**Построить с нуля рабочую B2B-платформу, чтобы:**

1. **Закрепить знания** — каждый день курса = один кирпич в проект
2. **Создать портфолио** — публичный проект для собеседований на SRE / DevOps
3. **Пройти путь** — от «пустой папки» до «production-grade» инфраструктуры
4. **Понять полный цикл** — Linux → Docker → CI/CD → K8s → SRE

**К концу 100 дней:** работает B2B-платформа с полной инфраструктурой.

---

## 📚 О КУРСЕ

**100 дней × 6 раз в месяц × 8 часов = ~800 часов**

**5 фаз:**

| Фаза | Дни | Фокус | Что строим в lab |
|---|---|---|---|
| **1 · Foundation** | 1-20 | Linux, bash, сети | Базовая структура, первые скрипты |
| **2 · Core DevOps** | 21-40 | Git, Python, Docker, CI/CD | Python API, Docker, GitHub Actions |
| **3 · Infrastructure** | 41-60 | Ansible, Terraform, PostgreSQL, Nginx | IaC, БД, reverse proxy |
| **4 · Orchestration & SRE** | 61-80 | K8s, Prometheus, SLO | K8s-деплой, мониторинг, SLO |
| **5 · Advanced & Interview** | 81-100 | Микросервисы, distributed | Разбиение на сервисы, финал |

**Длительность:** ~17 месяцев (ноябрь 2026 → март 2028).

**Подробнее:** [ROADMAP.md](./ROADMAP.md)

---

## 🏗️ СТЕК

**Backend:**
- **Python 3.12+** — язык
- **FastAPI** — веб-фреймворк
- **PostgreSQL 16** — база данных

**Инфраструктура:**
- **Docker** — контейнеризация
- **Nginx** — reverse proxy
- **Ansible** — конфигурация серверов
- **Terraform** — IaC (провижининг)

**Оркестрация:**
- **Kubernetes (k3s)** — контейнерная оркестрация
- **Helm** — пакеты для K8s

**Observability:**
- **Prometheus** — метрики
- **Grafana** — дашборды
- **Loki** — логи

**CI/CD:**
- **GitHub Actions** — CI
- **ArgoCD** — CD (GitOps)

**Среда:**
- **Mac (Фаза 1)** — Docker Desktop
- **VPS `wss-ccg-msk1`** (Timeweb, Москва) — Фаза 2+

---

## 📁 СТРУКТУРА

```
wallstack-sre-lab/
├── README.md                 ← этот файл
├── ROADMAP.md                ← 100 кирпичей проекта
├── AI-ONBOARD.md             ← инструкции для AI
├── .gitignore                ← исключения git
├── .env.example              ← пример переменных окружения
├── docs/
│   ├── ARCHITECTURE.md       ← архитектура проекта
│   └── CHANGELOG.md          ← дневник проекта
├── src/                      ← исходный код (появится по ходу)
├── infra/                    ← конфигурация инфраструктуры
└── scripts/                  ← bash-скрипты и утилиты
```

**Наполнение растёт по мере прохождения курса.**

---

## 🚀 КАК РАЗВЕРНУТЬ

**⚠️ Пока не готово — проект в активной разработке.**

**Будет добавлено после Фазы 3** (когда появится первый работающий сервис).

**Планируемое:**

```bash
# Клонировать
git clone git@github.com:wss-ccg/wallstack-sre-lab.git
cd wallstack-sre-lab

# Установить зависимости (Python)
pip install -r requirements.txt

# Настроить переменные окружения
cp .env.example .env
# отредактировать .env

# Запустить через Docker Compose
docker compose up -d

# Открыть
# http://localhost:8000
```

---

## 📊 ПРОГРЕСС

| Параметр | Значение |
|---|---|
| **День курса** | 0 / 100 |
| **Кирпичей построено** | 0 |
| **Статус** | 🟡 Не начато |
| **Последнее изменение** | 2026-10-10 |

**Обновляется после каждого занятия.**

---

## 🎓 ЦЕЛЬ ОБУЧЕНИЯ

**После 100 дней:**

- ✅ Уверенный Junior SRE / DevOps инженер
- ✅ Портфолио-проект с полной инфраструктурой
- ✅ Навыки: Linux, Docker, K8s, CI/CD, IaC, observability
- ✅ Готов к техническим собеседованиям

**План курса:** https://github.com/wss-ccg/wallstack-sre-core (приватный)

---

## 🧭 ПРИНЦИПЫ

| # | Принцип |
|---|---|
| **1** | **Строим реальное** — не «hello world», а полноценный проект |
| **2** | **Каждый коммит — шаг вперёд** — не пустые изменения |
| **3** | **Документируем по ходу** — README, ARCHITECTURE, CHANGELOG растут вместе с кодом |
| **4** | **Открытая разработка** — публичный репо, чтобы видеть рост |
| **5** | **Свой темп** — не гонимся за скоростью, идём за пониманием |

---

## 📌 ЛИЦЕНЗИЯ

**MIT** — для учебного проекта.

*(Лицензия будет добавлена, когда проект станет стабильным — ближе к концу курса)*

---

## 📞 КОНТАКТЫ

**Автор:** Andrey S. Yarovenko
**Email:** origin@wallstackaudio.com
**Основной проект:** WallStack · B2B CaaS Audio
**Сайт:** https://wallstackaudio.com
**Курс:** [wallstack-sre-core](https://github.com/wss-ccg/wallstack-sre-core)

---

## 📌 ССЫЛКИ

- **Курс:** https://github.com/wss-ccg/wallstack-sre-core (приватный)
- **WallStack (основной проект):** https://wallstackaudio.com
- **Roadmap:** [ROADMAP.md](./ROADMAP.md)
- **Архитектура:** [docs/ARCHITECTURE.md](./docs/ARCHITECTURE.md)
- **Дневник:** [docs/CHANGELOG.md](./docs/CHANGELOG.md)

---

**Создано:** 2026-10-10
**Обновлено:** 2026-10-10

---

**END OF README.md**
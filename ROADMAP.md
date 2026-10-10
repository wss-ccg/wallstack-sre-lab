# WallStack SRE Lab · ROADMAP

**100 кирпичей проекта. Что строим в каждый день курса.**

**Владелец:** Andrey S. Yarovenko (WallStack)
**Создано:** 2026-10-10
**Версия файла:** 1.0.0
**Связанный курс:** [wallstack-sre-core](https://github.com/wss-ccg/wallstack-sre-core)

---

## 📌 ПРИНЦИП

**Каждый день курса = 1-3 «кирпича» в этом проекте.**

**Кирпич** — это:
- Новый файл (код, конфиг, скрипт)
- Или новый компонент инфраструктуры
- Или новая интеграция (БД, CI, мониторинг)

**Результат:** к концу 100 дней — работающая B2B-платформа.

---

## 📌 ИТОГОВАЯ АРХИТЕКТУРА (что будет к дню 100)

```
┌─────────────────────────────────────────────────────────────┐
│                    ПОЛЬЗОВАТЕЛЬ                              │
└──────────────────────┬──────────────────────────────────────┘
                       │ HTTPS
                       ▼
┌─────────────────────────────────────────────────────────────┐
│                    NGINX (reverse proxy)                     │
│                    + SSL (Let's Encrypt)                     │
└──────────────────────┬──────────────────────────────────────┘
                       │ HTTP
                       ▼
┌─────────────────────────────────────────────────────────────┐
│              FASTAPI (Python, 2+ сервиса)                    │
│              ├── /api/v1/users                               │
│              ├── /api/v1/projects                            │
│              └── /api/v1/files                                │
└──────────────────────┬──────────────────────────────────────┘
                       │ TCP
                       ▼
┌─────────────────────────────────────────────────────────────┐
│                 POSTGRESQL 16 (с репликацией)                │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│                    ИНФРАСТРУКТУРА                            │
│  ├── Docker (контейнеры)                                     │
│  ├── Kubernetes (k3s, оркестрация)                           │
│  ├── Terraform (IaC)                                         │
│  ├── Ansible (конфигурация)                                  │
│  └── GitHub Actions (CI/CD)                                  │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│                    OBSERVABILITY                             │
│  ├── Prometheus (метрики)                                    │
│  ├── Grafana (дашборды)                                      │
│  ├── Loki (логи)                                             │
│  └── SLO / Error budget                                      │
└─────────────────────────────────────────────────────────────┘
```

**Стек:** Python + FastAPI + PostgreSQL + Docker + Nginx + K8s + Prometheus.

---

## 📚 ФАЗА 1 · FOUNDATION (Дни 1-20)

**Цель:** базовая структура + первый bash-скрипт.

| День | Кирпич | Что появляется в проекте |
|---|---|---|
| **1** | Структура папок | `docs/`, `src/`, `infra/`, `scripts/`, `README.md`, `ROADMAP.md` |
| **2** | Первый bash-скрипт | `scripts/check-system.sh` — проверка системы |
| **3** | Скрипт мониторинга диска | `scripts/disk-usage.sh` — проверка места |
| **4** | Скрипт проверки пользователей | `scripts/check-users.sh` — аудит пользователей |
| **5** | Скрипт прав файлов | `scripts/check-permissions.sh` — аудит прав |
| **6** | Скрипт процессов | `scripts/top-processes.sh` — топ-10 по CPU |
| **7** | Скрипт статуса сервисов | `scripts/check-services.sh` — статус systemd |
| **8** | Парсинг логов | `scripts/parse-logs.sh` — grep по логам |
| **9** | Скрипт сети | `scripts/check-network.sh` — проверка соединений |
| **10** | Скрипт DNS | `scripts/check-dns.sh` — резолвинг |
| **11** | Скрипт портов | `scripts/check-ports.sh` — открытые порты |
| **12** | Скрипт curl-тестов | `scripts/check-http.sh` — проверка endpoints |
| **13** | Скрипт TLS-проверки | `scripts/check-tls.sh` — проверка сертификатов |
| **14** | Скрипт SSH-настройки | `scripts/setup-ssh.sh` — базовая конфигурация |
| **15** | Скрипт firewall | `scripts/setup-firewall.sh` — настройка ufw |
| **16** | Bash-библиотека | `scripts/lib/common.sh` — общие функции |
| **17** | Bash-логирование | `scripts/lib/logging.sh` — единый формат логов |
| **18** | Bash-ошибки | `scripts/lib/error.sh` — обработка ошибок |
| **19** | Regex-парсер | `scripts/parse-regex.sh` — парсинг через regex |
| **20** | **Финальный скрипт фазы** | `scripts/health-check.sh` — полная проверка системы |

**Итог Фазы 1:** папка `scripts/` с ~18 bash-утилитами.

---

## 📚 ФАЗА 2 · CORE DEVOPS (Дни 21-40)

**Цель:** git-настройка, Python API, Docker, CI/CD.

| День | Кирпич | Что появляется |
|---|---|---|
| **21** | Git-структура | `.gitignore`, `.gitattributes`, `CONTRIBUTING.md` |
| **22** | Первые ветки | Ветка `develop`, настройка GitHub |
| **23** | Remote-настройка | `git remote`, git hooks |
| **24** | Rebase workflow | Гайд в `docs/GIT-WORKFLOW.md` |
| **25** | Стратегия ветвления | Финализация в `docs/GIT-WORKFLOW.md` |
| **26** | Pull Request template | `.github/PULL_REQUEST_TEMPLATE.md` |
| **27** | Pre-commit hooks | `.pre-commit-config.yaml` |
| **28** | Очистка истории | Рефакторинг ранних коммитов |
| **29** | Python-проект | `pyproject.toml`, `requirements.txt`, `src/__init__.py` |
| **30** | Python-модули | `src/utils/`, `src/config.py` |
| **31** | Работа с файлами | `src/file_io.py` |
| **32** | Subprocess | `src/shell_wrapper.py` |
| **33** | Requests | `src/api_client.py` — HTTP-клиент |
| **34** | CLI-утилита | `src/cli.py` — argparse |
| **35** | Первый Dockerfile | `Dockerfile` — образ Python-приложения |
| **36** | Оптимизация образа | Multi-stage build, `.dockerignore` |
| **37** | Volumes и networks | `docker-compose.yml` — базовая версия |
| **38** | Compose для dev | `docker-compose.dev.yml` |
| **39** | Registry | Push в GitHub Container Registry |
| **40** | **CI/CD (первый)** | `.github/workflows/ci.yml` — сборка + тесты |

**Итог Фазы 2:** Python-приложение + Docker + GitHub Actions.

---

## 📚 ФАЗА 3 · INFRASTRUCTURE (Дни 41-60)

**Цель:** IaC, PostgreSQL, Nginx, cloud.

| День | Кирпич | Что появляется |
|---|---|---|
| **41** | Ansible-структура | `ansible/`, `inventory.ini` |
| **42** | Первый playbook | `ansible/setup-basic.yml` — базовая настройка VPS |
| **43** | Роли | `ansible/roles/nginx/`, `ansible/roles/python/` |
| **44** | **Ansible big** | `ansible/site.yml` — полный playbook |
| **45** | Terraform-структура | `terraform/`, `main.tf` |
| **46** | Terraform state | Backend, workspace |
| **47** | Terraform модули | `terraform/modules/vps/` |
| **48** | **Terraform big** | `terraform/environments/prod/` — провайдинг VPS |
| **49** | PostgreSQL init | `scripts/init-db.sh`, схема |
| **50** | Миграции | `src/migrations/` — Alembic |
| **51** | Бэкапы БД | `scripts/backup-db.sh` |
| **52** | Репликация | Гайд `docs/POSTGRES-REPLICA.md` |
| **53** | Nginx базовый | `infra/nginx/nginx.conf` |
| **54** | Nginx reverse proxy | `infra/nginx/sites/api.conf` |
| **55** | SSL через certbot | `infra/nginx/ssl/`, скрипт |
| **56** | **Nginx big** | Финальный Nginx перед FastAPI |
| **57** | Cloud-ресурсы | VPC, firewall в Timeweb/Terraform |
| **58** | Object storage | S3-совместимое хранилище, `src/storage.py` |
| **59** | Мониторинг cost | Гайд `docs/COST-MANAGEMENT.md` |
| **60** | **Infra big** | Собираем всю инфраструктуру вместе |

**Итог Фазы 3:** полная инфраструктура на VPS (`wss-ccg-msk1`).

---

## 📚 ФАЗА 4 · ORCHESTRATION & SRE (Дни 61-80)

**Цель:** K8s, observability, SLO.

| День | Кирпич | Что появляется |
|---|---|---|
| **61** | K8s-кластер | k3s на VPS, `kubectl` настроен |
| **62** | Namespace | `infra/k8s/namespace.yml` |
| **63** | Deployment | `infra/k8s/api-deployment.yml` |
| **64** | Service | `infra/k8s/api-service.yml` |
| **65** | ConfigMap, Secret | `infra/k8s/config.yml`, `secret.yml` |
| **66** | StatefulSet для БД | `infra/k8s/postgres-statefulset.yml` |
| **67** | Helm chart | `infra/helm/wallstack-sre-lab/` |
| **68** | **K8s big** | Полный деплой Python API в K8s |
| **69** | Prometheus setup | `infra/monitoring/prometheus.yml` |
| **70** | PromQL-запросы | Дашборд `infra/monitoring/queries/` |
| **71** | Grafana дашборды | `infra/monitoring/dashboards/` — JSON |
| **72** | Alertmanager | `infra/monitoring/alerts.yml` |
| **73** | Loki + логи | `infra/monitoring/loki.yml` |
| **74** | OpenTelemetry | `src/tracing.py` — трейсинг |
| **75** | Метрики RED/USE | `src/metrics.py` — приложение отдаёт метрики |
| **76** | SLI/SLO | `docs/SLO.md` — определение |
| **77** | Error budget | `docs/SLO.md` — продолжение |
| **78** | On-call practices | `docs/ONCALL.md` |
| **79** | Postmortem | `docs/POSTMORTEMS/` — папка + шаблон |
| **80** | **SRE big** | Grafana dashboard для SLO |

**Итог Фазы 4:** K8s + полный observability stack + SLO.

---

## 📚 ФАЗА 5 · ADVANCED & INTERVIEW (Дни 81-100)

**Цель:** микросервисы, distributed, финал.

| День | Кирпич | Что появляется |
|---|---|---|
| **81** | Анализ монолита | `docs/MICROSERVICES-PLAN.md` |
| **82** | API Gateway | FastAPI-gateway перед сервисами |
| **83** | Сервис users | `services/users/` — отдельный микросервис |
| **84** | Ownership | `docs/SERVICES.md` — матрица сервисов |
| **85** | Consistency | `docs/CONSISTENCY.md` — гайд |
| **86** | Консенсус в БД | Настройка PostgreSQL replication |
| **87** | Паттерны | `docs/PATTERNS.md` — Circuit Breaker и др. |
| **88** | **Microservices big** | Разбиение на 2+ сервиса |
| **89** | ETL pipeline | `pipelines/` — простой ETL-скрипт |
| **90** | Kafka setup | `infra/kafka/docker-compose.yml` |
| **91** | Обработка окон | `pipelines/windows.py` |
| **92** | **Pipeline big** | Kafka pipeline в проекте |
| **93** | CI/CD advanced | Reusable workflows в `.github/workflows/` |
| **94** | ArgoCD | `infra/argocd/` — GitOps-конфиг |
| **95** | Deployment-стратегии | Blue-green, canary — гайд |
| **96** | DevOps-философия | `docs/DEVOPS-CULTURE.md` |
| **97** | SRE vs DevOps | `docs/SRE-VS-DEVOPS.md` |
| **98** | Mock interview #1 | `docs/INTERVIEW-PREP.md` — вопросы Linux |
| **99** | Mock interview #2 | `docs/INTERVIEW-PREP.md` — Docker/K8s |
| **100** | **Финал** | Полная документация проекта + резюме |

**Итог Фазы 5:** микросервисная архитектура + GitOps + готовность к собеседованию.

---

## 📊 ИТОГОВАЯ СТРУКТУРА (к дню 100)

```
wallstack-sre-lab/
├── README.md
├── ROADMAP.md (этот файл)
├── AI-ONBOARD.md
├── .gitignore
├── .env.example
├── requirements.txt
├── pyproject.toml
├── Dockerfile
├── docker-compose.yml
├── .github/
│   ├── workflows/
│   │   ├── ci.yml
│   │   ├── cd.yml
│   │   └── deploy.yml
│   └── PULL_REQUEST_TEMPLATE.md
├── docs/
│   ├── ARCHITECTURE.md
│   ├── CHANGELOG.md
│   ├── GIT-WORKFLOW.md
│   ├── SLO.md
│   ├── ONCALL.md
│   ├── INTERVIEW-PREP.md
│   └── POSTMORTEMS/
├── src/
│   ├── __init__.py
│   ├── main.py
│   ├── config.py
│   ├── api_client.py
│   ├── file_io.py
│   ├── shell_wrapper.py
│   ├── cli.py
│   ├── metrics.py
│   ├── tracing.py
│   ├── storage.py
│   ├── migrations/
│   └── utils/
├── services/
│   ├── users/
│   └── files/
├── pipelines/
│   ├── etl.py
│   └── windows.py
├── scripts/
│   ├── check-system.sh
│   ├── disk-usage.sh
│   ├── backup-db.sh
│   ├── health-check.sh
│   └── lib/
├── infra/
│   ├── nginx/
│   ├── k8s/
│   ├── helm/
│   ├── monitoring/
│   ├── kafka/
│   └── argocd/
├── ansible/
│   ├── inventory.ini
│   ├── site.yml
│   └── roles/
└── terraform/
    ├── main.tf
    ├── modules/
    └── environments/
```

---

## 📌 ПРАВИЛА РАБОТЫ С ROADMAP

| # | Правило |
|---|---|
| **1** | **Каждый день** — минимум 1 кирпич |
| **2** | **Кирпич должен быть закоммичен** — не висеть в рабочей папке |
| **3** | **После кирпича** — обновить `docs/CHANGELOG.md` |
| **4** | **Если тема сложная** — можно 2 дня на 1 кирпич |
| **5** | **Не перескакивать** — порядок важен для зависимостей |
| **6** | **ROADMAP — живой документ** — можно корректировать по ходу |

---

## 📌 СВЯЗЬ С КУРСОМ

**Каждый день курса в `wallstack-sre-core` ссылается на этот ROADMAP:**

**Пример в `day-035.md`:**
```
## 🏗️ КИРПИЧ В LAB

Кирпич дня: Первый Dockerfile

Создать: Dockerfile в корне wallstack-sre-lab
Содержимое: см. ROADMAP.md · Фаза 2 · День 35

Действие:
1. Создай Dockerfile
2. Собери образ
3. Запусти контейнер
4. Проверь работу
5. git add + commit + push
```

**= Прямая связь: урок → кирпич в lab.**

---

## 📌 ОБНОВЛЕНИЕ ROADMAP

**Раз в месяц:**
- Проверить, что все кирпичи за месяц сделаны
- Если что-то не сделано — перенести или упростить
- Добавить комментарии в `docs/CHANGELOG.md`

**Раз в фазу:**
- Ретроспектива — что получилось, что нет
- Скорректировать план следующей фазы, если нужно

---

**Создано:** 2026-10-10
**Обновлено:** 2026-10-10

---

**END OF ROADMAP.md**
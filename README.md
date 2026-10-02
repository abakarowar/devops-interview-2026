# 🚀 DevOps Interview 2026 — шпаргалка-курс для подготовки к собеседованию

> Всё, что спрашивают на собеседованиях DevOps / SRE / Platform Engineer в 2026 году — в одном репозитории.
> Короткая теория, команды, типовые вопросы с ответами, задачи live-coding и «ловушки» интервьюеров.

![level](https://img.shields.io/badge/level-Junior%20→%20Senior-blue)
![lang](https://img.shields.io/badge/язык-русский-red)
![year](https://img.shields.io/badge/актуально-2026-green)
![license](https://img.shields.io/badge/license-MIT-lightgrey)

---

## 📚 Оглавление

- [00. Как устроено собеседование DevOps в 2026](#m00)
- [01. Linux](#m01)
- [02. Сети](#m02)
- [03. Git](#m03)
- [04. Docker и контейнеры](#m04)
- [05. Kubernetes](#m05)
- [06. CI/CD и GitOps](#m06)
- [07. Infrastructure as Code: Terraform / OpenTofu и Ansible](#m07)
- [08. Облака: AWS / Yandex Cloud / общие принципы](#m08)
- [09. Observability: метрики, логи, трейсы](#m09)
- [10. Bash и Python для DevOps](#m10)
- [11. DevSecOps](#m11)
- [12. SRE и управление инцидентами](#m12)
- [13. System Design для DevOps](#m13)
- [14. Практика: troubleshooting-кейсы и live-coding](#m14)
- [15. Soft skills, HR и переговоры](#m15)
- [⚡ DevOps-шпаргалка на одной странице](#cheatsheet)
- [❓ 150 вопросов с собеседований DevOps 2026](#questions)
- [🗺️ Дорожная карта DevOps 2026](#roadmap)

## 🔥 Что изменилось в DevOps-собеседованиях к 2026


- **Platform Engineering** и Internal Developer Platform (Backstage, Port) — частая тема для Middle+.
- **GitOps по умолчанию**: Argo CD / Flux спрашивают почти везде, где есть Kubernetes.
- **OpenTofu** рядом с Terraform (после смены лицензии HashiCorp → BSL).
- **OpenTelemetry** — стандарт де-факто для трейсов/метрик/логов.
- **Supply chain security**: SBOM, подписи образов (cosign/Sigstore), SLSA.
- **eBPF** (Cilium, Tetragon, Pixie) — в вопросах про сеть и observability в K8s.
- **Gateway API** постепенно вытесняет Ingress; ingress-nginx объявлен к выводу из поддержки.
- **AI в работе DevOps**: как используешь LLM-ассистентов, где им нельзя доверять, MLOps/GPU-ноды в K8s.
- **FinOps**: «как сократить счёт за облако на 30%» — популярный кейс.
- Для РФ-рынка: **Yandex Cloud, VK Cloud, Deckhouse, GitLab self-hosted**, импортозамещение.


---

<a id="m00"></a>

# 00. Как устроено собеседование DevOps в 2026

## Типичные этапы

| Этап | Длительность | Что проверяют |
|------|-------------|---------------|
| HR-скрининг | 20–30 мин | Мотивация, зарплатные ожидания, формат работы, английский |
| Техническое интервью | 60–90 мин | Linux, сети, контейнеры, K8s, CI/CD, IaC, облако |
| Практика / live-coding | 45–90 мин | Скрипт на Bash/Python, Dockerfile, починить пайплайн/под, troubleshooting |
| System design | 45–60 мин | Спроектировать инфраструктуру (Middle+/Senior) |
| Тестовое задание | 2–8 ч | Terraform + K8s + CI для простого сервиса |
| Финал с тимлидом/CTO | 30–60 мин | Культура, ownership, как вёл инциденты |

## Ожидания по грейдам

**Junior (0–1.5 года)**
- Уверенный Linux, основы сетей, Git.
- Docker: собрать образ, docker compose.
- Базовый CI (GitLab CI / GitHub Actions).
- Понимает, что такое K8s Pod/Deployment/Service.

**Middle (1.5–4 года)**
- K8s в продакшне: отладка, Helm, Ingress/Gateway, RBAC, HPA.
- Terraform: модули, remote state, workspaces.
- Мониторинг: Prometheus + Grafana + алерты, логирование.
- Стратегии деплоя, GitOps, секреты (Vault/ESO).
- Опыт инцидентов.

**Senior / Lead (4+ лет)**
- Проектирование платформы, multi-region, DR, RPO/RTO.
- SLO и error budget, культура postmortem.
- Безопасность цепочки поставки, compliance.
- FinOps, оценка trade-off, менторство, влияние на процессы.

## Как отвечать на технические вопросы

1. **Определение** — одно предложение.
2. **Как работает** — механизм.
3. **Пример из практики** — «у нас было так…».
4. **Trade-off / подводные камни** — это отличает Middle от Senior.

> ❌ «Rebase — это когда коммиты переносятся».
> ✅ «Rebase переписывает коммиты ветки поверх нового base, давая линейную историю. Использую для локальных фич-веток перед MR. Никогда не ребейзю публичные ветки — это переписывает хеши и ломает историю коллегам».

Если не знаешь — говори: «Не сталкивался, но рассуждал бы так…» — и рассуждай. Это ценится выше, чем выдумка.

## План подготовки

### 🏃 2 недели (интенсив)
| Дни | Темы |
|-----|------|
| 1–2 | Linux + сети (модули 01–02) |
| 3 | Git + Docker (03–04) |
| 4–6 | Kubernetes (05) + лабы |
| 7 | CI/CD + GitOps (06) |
| 8 | Terraform/Ansible (07) |
| 9 | Облако (08) |
| 10 | Observability (09) |
| 11 | Скрипты + Security (10–11) |
| 12 | SRE + System Design (12–13) |
| 13 | Практика (14), мок-интервью |
| 14 | Soft skills (15), CHEATSHEET, отдых |

### 🚶 4 недели
Тот же порядок, но по ~2 дня на модуль + каждая неделя заканчивается мок-интервью по [150 вопросов](#questions).

## Чек-лист перед интервью

- [ ] Подготовил 3 истории по STAR: инцидент, автоматизация, конфликт/неудача.
- [ ] Могу нарисовать архитектуру текущего/прошлого проекта за 5 минут.
- [ ] Знаю цифры своего проекта: RPS, кол-во сервисов, нод, время деплоя, MTTR.
- [ ] Подготовил 3–5 вопросов работодателю.
- [ ] Проверил камеру, микрофон, демонстрацию экрана, терминал с крупным шрифтом.


---

<a id="m01"></a>

# 01. Linux

## Процессы

- **Процесс** — экземпляр программы со своим адресным пространством; **поток** — разделяет память процесса.
- Создание: `fork()` (копия, copy-on-write) → `exec()` (заменяет образ).
- **PID 1** — init (systemd). В контейнере PID 1 — твоё приложение: оно должно обрабатывать сигналы и «пожинать» зомби (или используй `tini` / `--init`).
- **Зомби** — завершился, но родитель не вызвал `wait()`. Не занимает ресурсов, кроме записи в таблице PID. Убить нельзя — нужно убить/починить родителя.
- **Сирота** — родитель умер, процесс переподхватывает init.

### Состояния процесса (`ps` STAT)
| Код | Значение |
|----|----------|
| R | Running/runnable |
| S | Interruptible sleep |
| D | Uninterruptible sleep (обычно I/O) — не убивается даже `kill -9` |
| Z | Zombie |
| T | Stopped |

### Сигналы
| Сигнал | № | Смысл |
|--------|---|-------|
| SIGHUP | 1 | Перечитать конфиг / терминал закрыт |
| SIGINT | 2 | Ctrl+C |
| SIGKILL | 9 | Убить немедленно, нельзя перехватить |
| SIGTERM | 15 | Вежливое завершение (по умолчанию в `kill`, в K8s при остановке пода) |
| SIGSTOP/SIGCONT | 19/18 | Пауза/продолжение |

> 💡 В K8s: SIGTERM → ждём `terminationGracePeriodSeconds` (30s) → SIGKILL.

## Память

- `free -h`: колонка **available** важнее **free** — page cache освобождается по требованию.
- **OOM Killer** выбирает жертву по `oom_score`. Смотреть: `dmesg -T | grep -i oom`, `journalctl -k`.
- **Swap** в K8s традиционно выключали; с v1.28+ есть поддержка swap (NodeSwap), к 2026 — GA для LimitedSwap.
- VSZ — виртуальная память, RSS — реально в RAM.

## Файловая система

- **inode** — метаданные файла (права, владелец, блоки), но не имя. Имя — запись в каталоге.
- **Hard link** — ещё одно имя на тот же inode (в пределах ФС). **Soft link** — файл с путём.
- «Диск полон, а `du` показывает мало» → удалённый файл держит открытый процесс: `lsof +L1` / `lsof | grep deleted`. Решение: перезапустить процесс или `> /proc/PID/fd/N`.
- «Места есть, но файл не создаётся» → кончились inode: `df -i`.
- Права: `rwx` = 4+2+1. `chmod 750`. SUID (4000), SGID (2000), sticky bit (1000, как в `/tmp`).

## Загрузка системы
BIOS/UEFI → загрузчик (GRUB) → ядро + initramfs → systemd (PID 1) → target'ы → юниты.

## systemd

```bash
systemctl status|start|stop|restart|enable --now nginx
systemctl daemon-reload            # после правки юнита
journalctl -u nginx -f --since "10 min ago"
systemctl list-units --failed
systemd-analyze blame              # что тормозит загрузку
```

Минимальный юнит:
```ini
[Unit]
Description=My App
After=network-online.target

[Service]
ExecStart=/usr/local/bin/app
Restart=on-failure
User=app
LimitNOFILE=65536

[Install]
WantedBy=multi-user.target
```

## Load Average
Среднее число процессов в состоянии R **и D** за 1/5/15 минут. Сравнивай с числом ядер (`nproc`). Высокий LA при низком CPU → ждём I/O (D-состояние).

## Troubleshooting: метод USE (Utilization, Saturation, Errors)

```bash
uptime                      # load average
top / htop                  # CPU, память, процессы
vmstat 1                    # r, b, si/so (swap), wa (iowait)
iostat -xz 1                # %util, await дисков
mpstat -P ALL 1             # загрузка по ядрам
free -h
df -h ; df -i
ss -tulpn                   # слушающие порты
ss -s                       # сводка по сокетам
lsof -p PID                 # открытые файлы процесса
strace -p PID -f -e trace=network
dmesg -T | tail
journalctl -xe
```

> 🎯 «Сервер тормозит, что делаешь?» — назови «60 секунд Брендана Грегга»: `uptime, dmesg, vmstat, mpstat, pidstat, iostat, free, sar -n DEV, sar -n TCP, top`.

## Полезные однострочники

```bash
# Топ-10 процессов по памяти
ps aux --sort=-%mem | head -11
# Топ IP в access.log
awk '{print $1}' access.log | sort | uniq -c | sort -rn | head
# Найти файлы > 1G
find / -xdev -type f -size +1G 2>/dev/null
# Кто держит порт 8080
ss -lptn 'sport = :8080'
# Заменить в файлах
grep -rl old . | xargs sed -i 's/old/new/g'
```

## ❓ Вопросы

1. **Чем отличается процесс от потока?** — Потоки делят память и дескрипторы одного процесса; процессы изолированы.
2. **Что такое зомби и как от них избавиться?** — См. выше: исправить/перезапустить родителя.
3. **`kill -9` не убивает процесс — почему?** — Процесс в D-состоянии (ждёт I/O, например зависший NFS) или зомби.
4. **Что такое inode? Что будет, если они кончатся?** — Нельзя создать файл при свободном месте.
5. **Как найти, что съело диск?** — `du -xh --max-depth=1 / | sort -h`, `ncdu`, + проверить удалённые открытые файлы.
6. **Разница между `/etc/profile`, `~/.bashrc`, `~/.bash_profile`?** — login vs interactive non-login shell.
7. **Что такое cgroups и namespaces?** — Основа контейнеров (модуль 04).
8. **Что делает `chmod 4755`?** — SUID + rwxr-xr-x.
9. **Как работает `sudo`?** — SUID-бинарь, правила в `/etc/sudoers` (редактировать `visudo`).
10. **Что такое `ulimit` / «Too many open files»?** — Лимит дескрипторов; поднять `LimitNOFILE` в юните или `/etc/security/limits.conf`.


---

<a id="m02"></a>

# 02. Сети

## Модели OSI и TCP/IP

| OSI | Пример | TCP/IP |
|-----|--------|--------|
| 7 Application | HTTP, DNS, gRPC | Application |
| 6 Presentation | TLS, кодировки | Application |
| 5 Session | — | Application |
| 4 Transport | TCP, UDP, QUIC | Transport |
| 3 Network | IP, ICMP | Internet |
| 2 Data Link | Ethernet, ARP, MAC | Link |
| 1 Physical | кабель, радио | Link |

> L4-балансировщик смотрит на IP:порт, L7 — на HTTP (путь, заголовки, cookie).

## TCP vs UDP

| TCP | UDP |
|-----|-----|
| С установлением соединения (3-way handshake) | Без соединения |
| Гарантия доставки и порядка | Без гарантий |
| Контроль перегрузки | Минимум накладных |
| HTTP/1.1, HTTP/2, SSH, БД | DNS, VoIP, игры, QUIC (HTTP/3) |

**Handshake:** SYN → SYN-ACK → ACK. **Закрытие:** FIN → ACK → FIN → ACK.

**TIME_WAIT** — сторона, закрывшая первой, ждёт 2×MSL, чтобы поздние пакеты не попали в новое соединение. Много TIME_WAIT — норма для клиентов; лечится keep-alive / пулом соединений.

## IP и подсети

- `/24` = 256 адресов (254 хоста), `/16` = 65 536, `/28` = 16.
- Приватные: `10.0.0.0/8`, `172.16.0.0/12`, `192.168.0.0/16`. CGNAT: `100.64.0.0/10`.
- **NAT**: SNAT (исходящий, маскарадинг), DNAT (проброс портов).
- **ARP** — IP → MAC в локальном сегменте.

## DNS

Резолв `example.com`: stub resolver → `/etc/hosts` → рекурсивный резолвер → root → `.com` TLD → authoritative NS → ответ кэшируется по TTL.

| Запись | Назначение |
|--------|-----------|
| A / AAAA | IPv4 / IPv6 |
| CNAME | Алиас (нельзя на apex-домене) |
| MX | Почта |
| TXT | SPF, DKIM, верификация |
| NS | Делегирование |
| SRV | Сервис + порт |
| PTR | Обратная зона |

```bash
dig +trace example.com
dig @8.8.8.8 example.com A +short
```

> 💡 В K8s: `ndots:5` в `/etc/resolv.conf` пода → много лишних запросов к внешним доменам. Решение — FQDN с точкой в конце или уменьшить `ndots`.

## HTTP

- **Методы:** GET, POST, PUT (идемпотентный), PATCH, DELETE, HEAD, OPTIONS.
- **Коды:** 2xx успех, 301/302/307/308 редирект, 304 not modified, 400/401/403/404/429, 500/502/503/504.
  - **502** — прокси получил плохой ответ от бэкенда (упал, сбросил соединение).
  - **503** — сервис недоступен (нет здоровых апстримов, перегрузка).
  - **504** — апстрим не ответил за таймаут.
- **HTTP/1.1** — keep-alive, head-of-line blocking на уровне соединения.
- **HTTP/2** — мультиплексирование, бинарный, сжатие заголовков HPACK. HOL остаётся на уровне TCP.
- **HTTP/3** — поверх **QUIC (UDP)**, нет TCP HOL, быстрый 0-RTT/1-RTT handshake.

## TLS 1.3

1. ClientHello (поддерживаемые шифры, key share, SNI).
2. ServerHello + сертификат + Finished — 1-RTT.
3. Ключи по ECDHE → forward secrecy.

- Цепочка: leaf → intermediate → root CA (в trust store клиента).
- **mTLS** — клиент тоже предъявляет сертификат (service mesh, zero trust).
- Проверка: `openssl s_client -connect host:443 -servername host` ; `openssl x509 -noout -dates -in cert.pem`.
- Let's Encrypt + cert-manager в K8s. С 2026 года отрасль идёт к сокращению срока жизни сертификатов (CA/B Forum: до 47 дней к 2029) → автоматизация обязательна.

## Балансировка

- Алгоритмы: round robin, least connections, weighted, IP hash, consistent hashing.
- Health checks: active/passive.
- L4: IPVS, AWS NLB, HAProxy (tcp). L7: Nginx, Envoy, HAProxy, AWS ALB, Traefik.
- Sticky sessions — по cookie; лучше stateless.

## 🎯 «Что происходит, когда вводишь google.com в браузере?»

1. Браузер парсит URL, проверяет HSTS, кэш.
2. DNS-резолв (кэш браузера → ОС → резолвер → рекурсия).
3. TCP handshake (или QUIC для HTTP/3).
4. TLS handshake, проверка сертификата.
5. HTTP-запрос → CDN/балансировщик → reverse proxy → приложение → БД/кэш.
6. Ответ, рендеринг, параллельные запросы ресурсов.

Расскажи на уровне, где ты силён (например, подробно про LB и K8s ingress).

## Команды

```bash
ip a ; ip r ; ip neigh
ss -tanp state established
curl -v -o /dev/null -w "dns:%{time_namelookup} conn:%{time_connect} tls:%{time_appconnect} total:%{time_total}\n" https://site
traceroute / mtr host
tcpdump -i any -nn port 443 -w dump.pcap
nc -zv host 5432
iptables -L -n -v ; nft list ruleset
```

## ❓ Вопросы

1. **Разница L4 и L7 балансировщика?**
2. **Почему CNAME нельзя на корневом домене?** — Конфликт с SOA/NS; используют ALIAS/ANAME.
3. **Что такое MTU и чем грозит неправильный?** — Фрагментация/дроп пакетов в туннелях (VXLAN, VPN): «ping идёт, а HTTPS виснет».
4. **Что такое 502 vs 504?**
5. **Как работает HTTPS?** — TLS handshake + симметричное шифрование.
6. **Зачем keep-alive?** — Меньше handshake'ов и TIME_WAIT.
7. **Что такое anycast?** — Один IP анонсируется из многих точек (CDN, DNS 1.1.1.1).
8. **Как проверить, открыт ли порт?** — `nc -zv`, `ss`, `telnet`, `curl`.


---

<a id="m03"></a>

# 03. Git

## Модель
- Объекты: **blob** (содержимое), **tree** (каталог), **commit** (tree + родители + автор), **tag**.
- Ветка — просто указатель на коммит. `HEAD` — указатель на текущую ветку.
- Три зоны: working tree → index (staging) → repository.

## merge vs rebase

| merge | rebase |
|-------|--------|
| Сохраняет историю, создаёт merge-коммит | Переписывает коммиты, линейная история |
| Безопасно для общих веток | Только для локальных/своих веток |
| Шумная история | Чистая история, проще `bisect` |

**Squash merge** — фича одним коммитом в main.

## reset vs revert vs restore

| Команда | Что делает |
|---------|-----------|
| `git reset --soft HEAD~1` | Отменить коммит, изменения в index |
| `git reset --mixed HEAD~1` | Изменения в working tree (по умолчанию) |
| `git reset --hard HEAD~1` | Удалить изменения совсем |
| `git revert <sha>` | Новый коммит, отменяющий старый — безопасно для pushed |
| `git restore file` | Откатить файл в рабочей копии |

## Спасательные команды

```bash
git reflog                         # история перемещений HEAD — вернёт «потерянное»
git reset --hard HEAD@{2}
git cherry-pick <sha>
git stash push -m "wip" ; git stash pop
git bisect start ; git bisect bad ; git bisect good v1.0
git commit --amend --no-edit
git rebase -i HEAD~5               # squash, reword, drop
git push --force-with-lease        # безопаснее --force
git log --oneline --graph --all
git blame -L 10,20 file
```

## Стратегии ветвления
- **Trunk-based** — короткие ветки, частые мержи в main, feature flags. Стандарт для CI/CD в 2026.
- **GitHub Flow** — main + feature-ветки + PR.
- **GitFlow** — develop/release/hotfix; для релизных циклов, сейчас считается тяжеловесным.

## Секреты в репозитории
Закоммитили пароль → **сначала ротировать секрет**, потом чистить историю (`git filter-repo`, BFG). Профилактика: pre-commit + gitleaks/trufflehog, push protection.

## Монорепо vs полирепо
Монорепо: атомарные изменения, общий тулинг; нужны умные CI (affected-сборки: Nx, Bazel, Turborepo). Полирепо: независимость, но сложнее согласованность версий.

## ❓ Вопросы
1. Merge vs rebase — когда что?
2. Как отменить запушенный коммит? — `git revert`.
3. Как восстановить удалённую ветку? — `git reflog` → `git branch name <sha>`.
4. Что такое fast-forward?
5. Чем `fetch` отличается от `pull`? — pull = fetch + merge/rebase.
6. Что такое `--force-with-lease`?
7. Как разрешаешь конфликты?
8. Что такое git hooks? — pre-commit, commit-msg, pre-push; серверные pre-receive.


---

<a id="m04"></a>

# 04. Docker и контейнеры

## Контейнер ≠ виртуальная машина
Контейнер — изолированный **процесс** на общем ядре хоста. ВМ — отдельное ядро на гипервизоре.

Изоляция строится на:
- **namespaces** — что процесс *видит*: `pid, net, mnt, uts, ipc, user, cgroup, time`.
- **cgroups (v2)** — сколько процесс *может потребить*: CPU, память, I/O, pids.
- **capabilities, seccomp, AppArmor/SELinux** — что процесс *может делать*.
- **union FS (overlayfs)** — слои образа.

## Экосистема
- **OCI** — стандарты образа и рантайма.
- **containerd** — высокоуровневый рантайм (используется K8s). **runc** — низкоуровневый.
- **dockershim** удалён из K8s в 1.24 — K8s работает с containerd/CRI-O напрямую; образы Docker при этом совместимы.
- Альтернативы: Podman (daemonless, rootless), Buildah, BuildKit, kaniko (сборка в K8s без Docker daemon).

## Образ и слои
- Каждая инструкция `RUN/COPY/ADD` → слой. Слои кэшируются **сверху вниз**: изменение слоя инвалидирует все ниже.
- Порядок: сначала зависимости (редко меняются), потом код.

## Хороший Dockerfile (multi-stage)

```dockerfile
# syntax=docker/dockerfile:1
FROM golang:1.23 AS build
WORKDIR /src
COPY go.mod go.sum ./
RUN --mount=type=cache,target=/go/pkg/mod go mod download
COPY . .
RUN CGO_ENABLED=0 go build -ldflags="-s -w" -o /app ./cmd/app

FROM gcr.io/distroless/static:nonroot
COPY --from=build /app /app
USER nonroot:nonroot
EXPOSE 8080
ENTRYPOINT ["/app"]
```

Чек-лист:
- ✅ Multi-stage, минимальная база (distroless, alpine, chainguard/wolfi).
- ✅ Фиксированные теги или digest (`image@sha256:...`), не `latest`.
- ✅ `USER` не root.
- ✅ `.dockerignore` (`.git`, `node_modules`, секреты).
- ✅ Объединять `RUN apt-get update && apt-get install -y ... && rm -rf /var/lib/apt/lists/*`.
- ✅ Секреты при сборке — `RUN --mount=type=secret`, не `ARG`/`ENV`.
- ✅ HEALTHCHECK (для Docker/compose; в K8s — probes).

## CMD vs ENTRYPOINT
- `ENTRYPOINT` — исполняемый файл, `CMD` — аргументы по умолчанию (переопределяются при `docker run`).
- **exec-форма** `["app"]` — процесс PID 1 получает сигналы. **shell-форма** `app` — PID 1 = `/bin/sh`, SIGTERM не дойдёт до приложения.

## COPY vs ADD
`ADD` умеет распаковывать tar и качать URL — неявно; используй `COPY`.

## Сети Docker
`bridge` (по умолчанию), `host`, `none`, `overlay` (Swarm), `macvlan`. В пользовательской bridge-сети работает DNS по именам контейнеров.

## Хранилище
- **volume** — управляется Docker (`/var/lib/docker/volumes`), лучший выбор для данных.
- **bind mount** — каталог хоста.
- **tmpfs** — в памяти.

## Команды
```bash
docker build -t app:1.0 .
docker run -d --name app -p 8080:8080 --memory 512m --cpus 1 app:1.0
docker logs -f app ; docker exec -it app sh
docker inspect app ; docker stats
docker image history app:1.0       # размер слоёв
docker system df ; docker system prune -a
docker compose up -d --build
docker buildx build --platform linux/amd64,linux/arm64 -t repo/app:1.0 --push .
```

## Безопасность
- Сканирование: **Trivy**, Grype, Docker Scout.
- Подпись: **cosign** (Sigstore), SBOM: `syft`, `docker buildx --sbom=true`.
- Rootless-режим, `--read-only`, `--cap-drop=ALL`, `--security-opt no-new-privileges`.
- Никогда не монтировать `/var/run/docker.sock` в контейнер без крайней нужды — это root на хосте.

## ❓ Вопросы
1. Чем контейнер отличается от ВМ?
2. Что такое namespaces и cgroups?
3. Как уменьшить размер образа?
4. CMD vs ENTRYPOINT, exec vs shell form?
5. Почему контейнер не завершается по `docker stop` 10 секунд? — PID 1 не обрабатывает SIGTERM (shell-форма или нет обработчика) → через 10с SIGKILL.
6. Как передать секрет при сборке?
7. Как работает кэш слоёв?
8. Что будет с данными при удалении контейнера? — Пропадут, если не в volume.
9. Почему контейнер с exit code 137? — SIGKILL, чаще всего **OOMKilled**.


---

<a id="m05"></a>

# 05. Kubernetes

## Архитектура

**Control plane:**
- **kube-apiserver** — единственная точка входа, всё общение через него (REST, watch).
- **etcd** — распределённое KV-хранилище (Raft), источник истины. Нечётное число узлов (3/5). Бэкап: `etcdctl snapshot save`.
- **kube-scheduler** — выбирает ноду для пода (filtering → scoring).
- **kube-controller-manager** — контроллеры (Deployment, ReplicaSet, Node, Job…): цикл reconcile «желаемое → фактическое».
- **cloud-controller-manager** — интеграция с облаком (LB, диски).

**Worker node:**
- **kubelet** — запускает поды через CRI (containerd), шлёт статус.
- **kube-proxy** — правила Service (iptables/IPVS/nftables); может заменяться Cilium (eBPF).
- **CNI-плагин** — Calico, Cilium, Flannel.

## 🎯 Что происходит при `kubectl apply -f deployment.yaml`
1. kubectl → API server: аутентификация → авторизация (RBAC) → admission (mutating → validating) → запись в etcd.
2. Deployment controller создаёт ReplicaSet → ReplicaSet controller создаёт Pod'ы (без `nodeName`).
3. Scheduler назначает ноду.
4. kubelet на ноде видит под → CRI тянет образ, CNI настраивает сеть, CSI монтирует тома → запуск контейнеров.
5. Endpoints/EndpointSlice обновляются после readiness → трафик через Service.

## Основные объекты

| Объект | Зачем |
|--------|-------|
| Pod | Минимальная единица, 1+ контейнеров с общей сетью и томами |
| Deployment | Stateless, rolling update, откат |
| StatefulSet | Стабильные имена (`db-0`), свой PVC на под, порядок запуска |
| DaemonSet | По поду на каждую ноду (агенты логов, мониторинга) |
| Job / CronJob | Разовые / по расписанию задачи |
| Service | Стабильный IP/DNS к набору подов |
| Ingress / Gateway API | L7 вход в кластер |
| ConfigMap / Secret | Конфигурация (Secret — только base64, не шифрование!) |
| PV / PVC / StorageClass | Хранилище, динамический provisioning |
| HPA / VPA | Автоскейлинг подов |
| PDB | Минимум доступных подов при добровольных прерываниях (drain) |
| NetworkPolicy | Файрвол между подами |

## Типы Service
- **ClusterIP** — внутренний (по умолчанию).
- **NodePort** — порт 30000–32767 на каждой ноде.
- **LoadBalancer** — облачный LB.
- **ExternalName** — CNAME.
- **Headless** (`clusterIP: None`) — DNS отдаёт IP подов напрямую (для StatefulSet).

DNS: `svc.namespace.svc.cluster.local`.

## Probes
- **startupProbe** — пока не прошла, остальные не работают (медленный старт).
- **readinessProbe** — готов принимать трафик? Нет → убирается из Endpoints.
- **livenessProbe** — живой? Нет → рестарт контейнера.

> ⚠️ Ловушка: liveness проверяет БД → БД легла → все поды перезапускаются по кругу. Liveness должна проверять только сам процесс.

## Ресурсы и QoS

```yaml
resources:
  requests: { cpu: "250m", memory: "256Mi" }   # для планировщика
  limits:   { memory: "256Mi" }                # потолок
```
- **Guaranteed** — requests = limits для всех; **Burstable** — requests < limits; **BestEffort** — ничего. При нехватке памяти выселяются первыми BestEffort.
- Превышение лимита памяти → **OOMKilled**. Превышение CPU → **throttling** (не убивает).
- Тренд: ставить memory limit = request, CPU limit часто не ставить (избегать throttling).
- С 1.33+ — **in-place resize** ресурсов пода без рестарта (beta→GA).

## Планирование
- `nodeSelector`, **node affinity**, **pod (anti-)affinity**, `topologySpreadConstraints` (раскидать по зонам).
- **taints/tolerations** — нода «отталкивает» поды без toleration (`NoSchedule`, `NoExecute`).
- PriorityClass и preemption.

## Стратегии деплоя
- `RollingUpdate` (`maxSurge`, `maxUnavailable`), `Recreate`.
- Canary / Blue-Green — через Argo Rollouts / Flagger / service mesh.

## Автоскейлинг
- **HPA** — число подов по CPU/памяти/custom metrics.
- **VPA** — requests/limits.
- **KEDA** — по событиям (очередь Kafka, RabbitMQ, cron), умеет scale-to-zero.
- **Cluster Autoscaler** / **Karpenter** — добавление/удаление нод.

## RBAC
`Role`/`ClusterRole` (что можно) + `RoleBinding`/`ClusterRoleBinding` (кому) → `User`, `Group`, `ServiceAccount`.
```bash
kubectl auth can-i delete pods --as=system:serviceaccount:dev:ci -n dev
```

## Безопасность
- **Pod Security Admission** (`privileged/baseline/restricted`) — заменил PodSecurityPolicy.
- `securityContext`: `runAsNonRoot`, `readOnlyRootFilesystem`, `allowPrivilegeEscalation: false`, `capabilities.drop: [ALL]`.
- Policy engines: **Kyverno**, OPA Gatekeeper, встроенный **ValidatingAdmissionPolicy (CEL)**.
- Секреты: шифрование etcd at rest, External Secrets Operator + Vault/облачный SM, Sealed Secrets, SOPS.

## Сеть
- Каждый под — свой IP, все поды видят друг друга без NAT (модель K8s).
- Ingress-контроллеры: ingress-nginx (в 2025 объявлен retirement — переход на Gateway API: Envoy Gateway, Cilium, Istio, NGINX Gateway Fabric, Traefik).
- **Gateway API**: `GatewayClass` → `Gateway` → `HTTPRoute/GRPCRoute`, разделение ролей инфраструктура/приложение.
- Service mesh: Istio (в т.ч. ambient mode без sidecar), Linkerd, Cilium.

## 🔧 Отладка пода

| Статус | Причина | Что смотреть |
|--------|---------|--------------|
| `Pending` | Нет ресурсов, taints, affinity, PVC не связан | `kubectl describe pod` → Events |
| `ImagePullBackOff` | Неверный образ/тег, нет imagePullSecret, rate limit | describe, `kubectl get secret` |
| `CrashLoopBackOff` | Приложение падает | `kubectl logs --previous` |
| `OOMKilled` | Превышен memory limit | describe → Last State, поднять лимит/фикс утечки |
| `CreateContainerConfigError` | Нет ConfigMap/Secret | describe |
| `Running`, но 0/1 Ready | readiness не проходит | probe, логи, порт |
| `Terminating` вечно | finalizers, зависший volume | `kubectl get -o yaml`, finalizers |

```bash
kubectl get pods -A -o wide
kubectl describe pod NAME
kubectl logs NAME -c container --previous -f
kubectl get events --sort-by=.lastTimestamp
kubectl exec -it NAME -- sh
kubectl debug -it NAME --image=nicolaka/netshoot --target=app
kubectl top pod / node
kubectl rollout status|history|undo deploy/app
kubectl port-forward svc/app 8080:80
kubectl get endpointslices -l kubernetes.io/service-name=app
kubectl drain node --ignore-daemonsets --delete-emptydir-data
```

**Service не отвечает:** селектор совпадает с лейблами? Есть endpoints? targetPort верный? Под Ready? NetworkPolicy? DNS (`nslookup svc` из пода)?

## Helm / Kustomize
- **Helm** — шаблонизатор + менеджер релизов (`install/upgrade/rollback`, values, charts в OCI-реестре).
- **Kustomize** — патчи над базовыми манифестами (overlays dev/stage/prod), встроен в kubectl.

## Операторы и CRD
CRD расширяет API, оператор — контроллер, автоматизирующий знания администратора (CloudNativePG, Strimzi, Prometheus Operator).

## Апгрейд кластера
Сначала control plane, потом ноды; по одной минорной версии; читать deprecated API (`pluto`, `kubent`); PDB + drain; бэкап etcd.

## ❓ Вопросы
1. Компоненты control plane и их роли?
2. Что происходит при `kubectl apply`?
3. Deployment vs StatefulSet vs DaemonSet?
4. Readiness vs liveness vs startup?
5. Requests vs limits, QoS-классы?
6. Под в CrashLoopBackOff — твои действия?
7. Как под на одной ноде достучится до пода на другой? — CNI: overlay (VXLAN/Geneve) или маршрутизация (BGP), eBPF.
8. Как работает Service под капотом? — kube-proxy пишет iptables/IPVS-правила DNAT на IP подов.
9. Почему Secret небезопасен по умолчанию и как защитить?
10. Как сделать zero-downtime деплой? — readiness, `maxUnavailable: 0`, preStop sleep, graceful shutdown, PDB.
11. Ingress vs Gateway API?
12. Что такое оператор?
13. Как бэкапить кластер? — etcd snapshot + Velero для ресурсов и PV.


---

<a id="m06"></a>

# 06. CI/CD и GitOps

## Термины
- **CI** — каждое изменение автоматически собирается и тестируется.
- **Continuous Delivery** — артефакт всегда готов к релизу, выкатка в прод по кнопке.
- **Continuous Deployment** — в прод автоматически.

## Типовой пайплайн

```
lint → unit tests → build → SAST/SCA → image build → scan → push (+sign, SBOM)
   → deploy dev → integration/e2e → deploy stage → approve → deploy prod → smoke → monitor
```

Принципы:
- **Build once, deploy many** — один артефакт (образ по digest) проходит все окружения.
- Быстрая обратная связь: быстрые проверки первыми, параллелизм, кэш.
- Пайплайн как код, в репо.
- Неизменяемые артефакты, версии из git SHA/semver.

## Инструменты (2026)
| Инструмент | Комментарий |
|------------|-------------|
| GitLab CI | Самый частый в РФ, `.gitlab-ci.yml`, runners |
| GitHub Actions | Самый частый в мире, marketplace, OIDC |
| Jenkins | Легаси, Groovy pipelines, много плагинов |
| Argo CD / Flux | GitOps CD для K8s |
| Tekton, Argo Workflows | K8s-native пайплайны |
| Dagger | Пайплайны как код на Go/Python/TS |

## Пример: GitLab CI

```yaml
stages: [test, build, deploy]

variables:
  IMAGE: $CI_REGISTRY_IMAGE:$CI_COMMIT_SHORT_SHA

test:
  stage: test
  image: golang:1.23
  cache: { key: go, paths: [.cache/go] }
  script: [go test ./...]

build:
  stage: build
  image: docker:27
  services: [docker:27-dind]
  script:
    - docker login -u $CI_REGISTRY_USER -p $CI_REGISTRY_PASSWORD $CI_REGISTRY
    - docker build -t $IMAGE .
    - docker push $IMAGE
  rules:
    - if: $CI_COMMIT_BRANCH == $CI_DEFAULT_BRANCH

deploy_prod:
  stage: deploy
  environment: production
  when: manual
  script:
    - helm upgrade --install app ./chart --set image.tag=$CI_COMMIT_SHORT_SHA --atomic --wait
```

## Пример: GitHub Actions с OIDC

```yaml
name: ci
on: { push: { branches: [main] }, pull_request: {} }
permissions: { contents: read, id-token: write, packages: write }
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: docker/setup-buildx-action@v3
      - uses: docker/login-action@v3
        with: { registry: ghcr.io, username: ${{ github.actor }}, password: ${{ secrets.GITHUB_TOKEN }} }
      - uses: docker/build-push-action@v6
        with:
          push: ${{ github.ref == 'refs/heads/main' }}
          tags: ghcr.io/${{ github.repository }}:${{ github.sha }}
          cache-from: type=gha
          cache-to: type=gha,mode=max
```

> 💡 **OIDC** вместо долгоживущих ключей: CI получает короткоживущий токен в облаке (AWS/GCP/Yandex) по доверию к issuer'у.
> 💡 Пиньте actions по SHA (`uses: actions/checkout@<sha>`) — защита от supply chain атак (кейс tj-actions/changed-files, 2025).

## Стратегии деплоя

| Стратегия | Как | Плюсы | Минусы |
|-----------|-----|-------|--------|
| Recreate | Остановить старое → запустить новое | Просто | Даунтайм |
| Rolling | Постепенная замена | Без даунтайма, дефолт K8s | Две версии одновременно |
| Blue-Green | Две среды, переключение трафика | Мгновенный откат | x2 ресурсы |
| Canary | Новая версия на % трафика + метрики | Минимальный риск | Нужен мониторинг/маршрутизация |
| Feature flags | Код задеплоен, фича включается флагом | Развязка deploy и release | Техдолг флагов |
| Shadow | Зеркалирование трафика | Тест на реальной нагрузке | Сложно, побочные эффекты |

**Миграции БД** — паттерн expand/contract: сначала обратно-совместимые изменения схемы, потом код, потом удаление старого.

## GitOps
Принципы (OpenGitOps): декларативно, версионируется в Git, **pull**-модель (агент в кластере тянет), непрерывная сверка (reconcile).

- **Argo CD**: `Application`, `ApplicationSet`, sync waves, self-heal, prune, UI.
- **Flux**: набор контроллеров, `Kustomization`, `HelmRelease`, image automation.
- Плюсы: аудит через Git, откат = `git revert`, нет кред от кластера в CI, обнаружение drift.
- Типичная схема: репо приложения (CI собирает образ) → бот обновляет тег в **репо конфигурации** → Argo CD синхронизирует.

## Секреты в CI
- Masked/protected переменные, OIDC, Vault, никаких секретов в логах и в образе.
- Отдельные runner'ы для прода, минимальные права.

## Метрики DORA
1. **Deployment frequency**
2. **Lead time for changes**
3. **Change failure rate**
4. **Time to restore service** (MTTR)
(+ Reliability как 5-я в новых отчётах.)

## ❓ Вопросы
1. CI vs Continuous Delivery vs Deployment?
2. Какие стадии у твоего пайплайна и почему в таком порядке?
3. Как ускорить пайплайн с 30 до 5 минут? — кэш зависимостей/слоёв, параллелизм, тесты только затронутого, свои runner'ы, меньшие образы.
4. Blue-green vs canary?
5. Что такое GitOps, push vs pull?
6. Как откатить релиз?
7. Как хранить секреты для CI?
8. Как деплоить миграции БД без даунтайма?
9. Что такое DORA-метрики?


---

<a id="m07"></a>

# 07. Infrastructure as Code: Terraform / OpenTofu и Ansible

## Подходы
- **Декларативный** (Terraform, K8s) — описываешь *что*, инструмент вычисляет *как*.
- **Императивный** (скрипты) — описываешь шаги.
- **Mutable** (Ansible настраивает живые сервера) vs **Immutable** (новый образ Packer → пересоздаём ВМ).

## Terraform / OpenTofu

> С 2023 Terraform под BSL; **OpenTofu** — open-source форк под Linux Foundation, совместим, добавил шифрование state. В 2025 HashiCorp вошла в IBM. На собеседовании — знать оба.

### Workflow
```bash
terraform init      # провайдеры, бэкенд, модули
terraform fmt && terraform validate
terraform plan -out=tfplan
terraform apply tfplan
terraform destroy
```

### State
- Хранит соответствие ресурсов в коде ↔ реальных объектов, метаданные, зависимости.
- **Remote backend** (S3 + блокировка, GCS, Terraform Cloud, Yandex Object Storage). С TF 1.10+ S3 умеет нативную блокировку (`use_lockfile`), DynamoDB больше не обязателен.
- **Locking** — защита от одновременных apply.
- State содержит секреты → шифровать, ограничивать доступ.
- Команды: `terraform state list|show|mv|rm`, `terraform import` / блок `import {}`, `moved {}` для рефакторинга без пересоздания.

### Ключевые понятия
```hcl
terraform {
  required_version = ">= 1.9"
  required_providers { aws = { source = "hashicorp/aws", version = "~> 5.0" } }
  backend "s3" { bucket = "tf-state" key = "prod/net.tfstate" region = "eu-central-1" use_lockfile = true }
}

variable "env" { type = string }

locals { tags = { env = var.env, owner = "platform" } }

data "aws_ami" "ubuntu" { most_recent = true owners = ["099720109477"] filter { name = "name" values = ["ubuntu/images/*24.04*amd64*"] } }

resource "aws_instance" "web" {
  for_each      = toset(["a", "b"])
  ami           = data.aws_ami.ubuntu.id
  instance_type = "t3.micro"
  tags          = merge(local.tags, { Name = "web-${each.key}" })
  lifecycle { create_before_destroy = true }
}

output "ips" { value = { for k, v in aws_instance.web : k => v.private_ip } }
```

- **`count` vs `for_each`**: `count` по индексу — удаление элемента из середины сдвигает индексы и пересоздаёт ресурсы; `for_each` по ключу — стабильно.
- **lifecycle**: `create_before_destroy`, `prevent_destroy`, `ignore_changes`, `replace_triggered_by`.
- **Модули**: переиспользование, версии из реестра/Git-тегов.
- **Workspaces** vs **отдельные каталоги/стейты на окружение** — второе обычно предпочтительнее для прода (изоляция, разные креды).
- **Terragrunt** — DRY для множества стейтов.

### Drift
Ручные изменения в облаке → `terraform plan` покажет расхождение. Решение: запрет ручных правок, регулярный plan в CI (drift detection), `-refresh-only`.

### Тестирование и качество
`tflint`, `checkov`/`trivy config`, `terraform test`, Terratest, pre-commit-terraform, Atlantis / Spacelift / env0 для plan в PR.

## Ansible

- **Agentless**, по SSH, push-модель. YAML-плейбуки, инвентарь, роли, модули.
- **Идемпотентность** — повторный запуск не меняет систему, если она уже в нужном состоянии. Модули (`apt`, `copy`, `template`) идемпотентны; `shell/command` — нет (используй `creates:`, `changed_when:`).

```yaml
- hosts: web
  become: true
  vars: { nginx_port: 80 }
  tasks:
    - name: Install nginx
      ansible.builtin.apt: { name: nginx, state: present, update_cache: true }
    - name: Config
      ansible.builtin.template: { src: nginx.conf.j2, dest: /etc/nginx/nginx.conf }
      notify: reload nginx
  handlers:
    - name: reload nginx
      ansible.builtin.service: { name: nginx, state: reloaded }
```

- Приоритет переменных: extra vars (`-e`) — самый высокий.
- Секреты: `ansible-vault`.
- Проверка: `--check --diff`, `ansible-lint`, Molecule.

## Terraform vs Ansible
Terraform — **провижининг** инфраструктуры (сети, ВМ, кластеры), хранит state. Ansible — **конфигурация** ОС и софта, без state. Часто вместе: Terraform создаёт ВМ → Ansible настраивает (или Packer + cloud-init).

## Другие инструменты
Pulumi (IaC на TS/Python/Go), Crossplane (IaC через K8s CRD), CloudFormation/CDK, Packer, cloud-init.

## ❓ Вопросы
1. Что такое state и зачем remote backend + locking?
2. Что делать, если state повреждён/потерян? — Бэкап/версионирование бакета, `import`.
3. `count` vs `for_each`?
4. Как импортировать существующий ресурс?
5. Как переименовать ресурс без пересоздания? — `moved {}` / `state mv`.
6. Как организовать окружения dev/stage/prod?
7. Что такое drift и как с ним бороться?
8. Terraform vs OpenTofu?
9. Идемпотентность в Ansible?
10. Как хранить секреты в Terraform? — не в коде; Vault provider, SM, `sensitive = true`, шифрование state.


---

<a id="m08"></a>

# 08. Облака: AWS / Yandex Cloud / общие принципы

## Модели
- **IaaS** (ВМ, сети) → **PaaS** (managed БД, K8s) → **SaaS**. **Serverless/FaaS** — Lambda, Cloud Functions.
- **Shared responsibility**: облако отвечает за безопасность *облака*, ты — за безопасность *в облаке* (IAM, данные, конфиги, патчи ВМ).

## Регионы и зоны
- **Region** — географическая локация; **AZ** — изолированный ДЦ внутри региона.
- Прод — минимум 2–3 AZ. Multi-region — для DR и глобальной задержки, дорого и сложно.

## Соответствие сервисов

| Категория | AWS | Yandex Cloud | GCP |
|-----------|-----|--------------|-----|
| ВМ | EC2 | Compute Cloud | Compute Engine |
| K8s | EKS | Managed Kubernetes | GKE |
| Объектное хранилище | S3 | Object Storage | GCS |
| Блочные диски | EBS | Disks | Persistent Disk |
| Managed SQL | RDS/Aurora | Managed PostgreSQL/MySQL | Cloud SQL |
| Сеть | VPC | VPC | VPC |
| IAM | IAM | IAM + сервисные аккаунты | IAM |
| Секреты | Secrets Manager / KMS | Lockbox / KMS | Secret Manager |
| Реестр | ECR | Container Registry | Artifact Registry |
| Функции | Lambda | Cloud Functions | Cloud Run Functions |
| Мониторинг | CloudWatch | Monitoring | Cloud Monitoring |
| DNS | Route 53 | Cloud DNS | Cloud DNS |
| LB | ALB/NLB | Application/Network LB | Cloud LB |

## Сеть (VPC)
- Публичная подсеть: маршрут в **Internet Gateway**. Приватная: исходящий через **NAT Gateway**.
- **Security Group** — stateful, на уровне ENI/инстанса, только allow. **NACL** — stateless, на подсеть, allow+deny.
- Связность: VPC peering, Transit Gateway, PrivateLink/VPC endpoints (доступ к S3 без интернета и без платы за NAT), VPN, Direct Connect.

## IAM
- Принцип **least privilege**.
- Роли вместо долгоживущих ключей; для EC2 — instance profile, для EKS — **IRSA / EKS Pod Identity**, для CI — **OIDC**.
- Политика: Effect / Action / Resource / Condition. Явный Deny побеждает Allow.
- Organizations + SCP, отдельные аккаунты на окружения.

## Хранилище
- **Object** (S3): классы хранения, lifecycle-политики, версионирование, Object Lock (защита бэкапов от ransomware). С 2020 S3 strongly consistent.
- **Block** (EBS): IOPS/throughput, снапшоты, привязаны к AZ.
- **File** (EFS/NFS): общий доступ многим инстансам.

## Отказоустойчивость и DR
- **RPO** — сколько данных можно потерять. **RTO** — за сколько восстановиться.
- Стратегии по росту стоимости: Backup & Restore → Pilot Light → Warm Standby → Multi-site Active/Active.
- Правило бэкапов **3-2-1**: 3 копии, 2 типа носителей, 1 вне площадки (+ immutable). Бэкап без проверенного восстановления — не бэкап.

## FinOps — «как сократить счёт»
1. Видимость: теги, cost allocation, дашборды (Kubecost/OpenCost для K8s).
2. Rightsizing: по фактической утилизации, VPA-рекомендации.
3. Модели оплаты: Reserved/Savings Plans для базы, **Spot** для stateless/батчей (Karpenter).
4. Выключать dev по ночам, scale-to-zero.
5. Хранилище: lifecycle в холодные классы, удалить orphaned диски/снапшоты/IP.
6. Трафик: NAT Gateway и межзональный/межрегиональный трафик — частые «скрытые» расходы; VPC endpoints.
7. ARM-инстансы (Graviton) — дешевле на 20–40%.

## Well-Architected Framework (6 столпов)
Operational Excellence, Security, Reliability, Performance Efficiency, Cost Optimization, Sustainability.

## ❓ Вопросы
1. Security Group vs NACL?
2. Как приватная подсеть ходит в интернет?
3. Как дать поду в EKS доступ к S3 без ключей?
4. RPO vs RTO, стратегии DR?
5. Как сократить расходы на облако?
6. Как построить отказоустойчивое веб-приложение в облаке? — LB в нескольких AZ, ASG/K8s, managed БД Multi-AZ, кэш, CDN, бэкапы.
7. Что такое shared responsibility?
8. Что делать, если ключ доступа утёк на GitHub? — немедленно деактивировать, ротировать, проверить CloudTrail, найти созданные ресурсы.


---

<a id="m09"></a>

# 09. Observability: метрики, логи, трейсы

## Мониторинг vs Observability
Мониторинг отвечает на *известные* вопросы («упал ли сервис?»). Observability позволяет ответить на *неизвестные* («почему у 2% пользователей из региона X медленно?») по телеметрии.

**Три столпа:** метрики, логи, трейсы (+ профилирование как четвёртый — Pyroscope, eBPF-профайлеры).

## Методологии
- **RED** (для сервисов): Rate, Errors, Duration.
- **USE** (для ресурсов): Utilization, Saturation, Errors.
- **Four Golden Signals** (Google SRE): Latency, Traffic, Errors, Saturation.

## Prometheus
- **Pull-модель**: скрейпит `/metrics` по HTTP. Для короткоживущих задач — Pushgateway.
- Service discovery (K8s, Consul, файлы), в K8s — Prometheus Operator: `ServiceMonitor`, `PodMonitor`, `PrometheusRule`.
- Хранение: локальная TSDB. Долгосрочное и HA: **Thanos, VictoriaMetrics, Mimir**.
- Prometheus 3.0 (2024): новый UI, native OTLP-приём, UTF-8 имена метрик.

### Типы метрик
| Тип | Пример | Как использовать |
|-----|--------|------------------|
| Counter | `http_requests_total` | Только растёт → `rate()` |
| Gauge | `memory_usage_bytes` | Текущее значение |
| Histogram | `http_request_duration_seconds_bucket` | Перцентили через `histogram_quantile` (агрегируется!) |
| Summary | квантили на клиенте | Нельзя агрегировать между инстансами |

### Кардинальность
Каждая уникальная комбинация лейблов = новый time series. **Никогда** не клади в лейблы user_id, request_id, email, полный URL — Prometheus умрёт.

### PromQL шпаргалка
```promql
# RPS сервиса
sum(rate(http_requests_total{job="api"}[5m]))

# Доля 5xx
sum(rate(http_requests_total{status=~"5.."}[5m]))
  / sum(rate(http_requests_total[5m]))

# p99 latency
histogram_quantile(0.99, sum by (le) (rate(http_request_duration_seconds_bucket[5m])))

# CPU пода в ядрах
sum by (pod) (rate(container_cpu_usage_seconds_total{namespace="prod"}[5m]))

# Диск заполнится через 4 часа
predict_linear(node_filesystem_avail_bytes[6h], 4*3600) < 0

# Под рестартился за час
increase(kube_pod_container_status_restarts_total[1h]) > 0

# Таргет недоступен
up == 0
```

`rate` — среднее за окно (для алертов/графиков), `irate` — по последним двум точкам (для резких графиков), `increase` — прирост за окно.

### Алертинг
```yaml
groups:
- name: api
  rules:
  - alert: HighErrorRate
    expr: |
      sum(rate(http_requests_total{status=~"5.."}[5m]))
      / sum(rate(http_requests_total[5m])) > 0.05
    for: 10m
    labels: { severity: critical }
    annotations:
      summary: "5xx > 5% на api"
      runbook_url: https://wiki/runbooks/api-5xx
```
**Alertmanager**: группировка, дедупликация, подавление (inhibition), silences, маршрутизация (Telegram, Slack, PagerDuty, email).

Хороший алерт: **actionable**, на симптомы (пользовательская боль), а не на причины; с runbook. Борьба с alert fatigue. Лучшая практика — **алерты на burn rate SLO** (модуль 12).

## Логи
- Структурированные (JSON), с `trace_id`, уровнем, сервисом.
- Стеки: **ELK/EFK** (Elasticsearch/OpenSearch), **Loki** (индексирует только лейблы — дёшево), ClickHouse-based (SigNoz, Uptrace), VictoriaLogs.
- Сборщики: Fluent Bit, Vector, Promtail → **Grafana Alloy** (Promtail в 2025 объявлен deprecated), OTel Collector.
- В K8s: приложение пишет в stdout → DaemonSet-агент читает `/var/log/containers`.

## Трейсы
- Распределённый трейс = дерево **span**'ов через сервисы; контекст передаётся в заголовках (W3C `traceparent`).
- Бэкенды: **Jaeger**, **Tempo**, Zipkin.
- **Sampling**: head-based (решение в начале) vs tail-based (в коллекторе, сохраняем ошибки и медленные).

## OpenTelemetry
Вендор-нейтральный стандарт: API/SDK для языков + **OTel Collector** (receivers → processors → exporters) + протокол OTLP. Автоинструментация, в т.ч. через eBPF (Grafana Beyla / OBI). Стандарт де-факто в 2026.

## Grafana
Дашборды, алерты, источники данных (Prometheus, Loki, Tempo, ClickHouse). Дашборды как код (Grafonnet, provisioning, Terraform). Стек **LGTM**: Loki, Grafana, Tempo, Mimir.

## ❓ Вопросы
1. Pull vs push модель мониторинга?
2. Типы метрик Prometheus, histogram vs summary?
3. Что такое кардинальность и чем опасна?
4. Как посчитать p95 latency?
5. `rate` vs `irate` vs `increase`?
6. Как сделать Prometheus HA и долгое хранение?
7. Что такое хороший алерт?
8. Loki vs Elasticsearch?
9. Что такое OpenTelemetry и Collector?
10. RED vs USE?


---

<a id="m10"></a>

# 10. Bash и Python для DevOps

## Bash: безопасный шаблон

```bash
#!/usr/bin/env bash
set -Eeuo pipefail          # падать на ошибке, неизвестной переменной, ошибке в пайпе
IFS=$'\n\t'
trap 'echo "Ошибка на строке $LINENO" >&2' ERR
trap 'rm -rf "$TMP"' EXIT

TMP=$(mktemp -d)
LOG_LEVEL=${LOG_LEVEL:-info}

log() { printf '%s [%s] %s\n' "$(date -Is)" "$1" "${*:2}" >&2; }

usage() { echo "Usage: $0 -e <env> [-n]"; exit 1; }

DRY_RUN=false
while getopts "e:nh" opt; do
  case $opt in
    e) ENV=$OPTARG ;;
    n) DRY_RUN=true ;;
    *) usage ;;
  esac
done
[[ -z ${ENV:-} ]] && usage

log info "Деплой в $ENV (dry-run=$DRY_RUN)"
```

### Ловушки Bash
- Всегда кавычки: `"$var"`, `"$@"`.
- `[[ ]]` вместо `[ ]` в bash.
- `$(...)` вместо обратных кавычек.
- `set -e` не срабатывает внутри `if`, `&&`, `||`.
- Проверяй скрипты **shellcheck**.
- `2>&1` — stderr в stdout; `&>/dev/null` — всё в никуда.
- Exit codes: `0` — успех, `$?` — код последней команды, `${PIPESTATUS[@]}`.

### Однострочники
```bash
# Подсчёт кодов ответа в nginx-логе
awk '{print $9}' access.log | sort | uniq -c | sort -rn
# Запросы в минуту
awk '{print substr($4,2,17)}' access.log | uniq -c
# Удалить файлы старше 7 дней
find /var/log/app -name "*.log" -mtime +7 -delete
# Параллельно пинговать хосты
xargs -P10 -I{} sh -c 'ping -c1 -W1 {} >/dev/null && echo "{} up" || echo "{} down"' < hosts.txt
# Повтор с задержкой
for i in {1..5}; do curl -fsS http://svc/health && break || sleep $((i*2)); done
# JSON
kubectl get pods -o json | jq -r '.items[] | select(.status.phase!="Running") | .metadata.name'
# YAML
yq '.spec.replicas = 3' -i deploy.yaml
```

## Задачи с собеседований (Bash)

**1. Найти топ-5 IP с наибольшим числом 5xx в логе nginx**
```bash
awk '$9 ~ /^5/ {print $1}' access.log | sort | uniq -c | sort -rn | head -5
```

**2. Проверить список URL и вывести недоступные**
```bash
while read -r url; do
  code=$(curl -s -o /dev/null -w '%{http_code}' --max-time 5 "$url")
  [[ $code =~ ^2|^3 ]] || echo "$url -> $code"
done < urls.txt
```

**3. Алерт, если диск > 80%**
```bash
df -P | awk 'NR>1 && int($5) > 80 {print $6, $5}'
```

**4. Ротация бэкапов: оставить последние 7**
```bash
ls -1t /backup/db-*.sql.gz | tail -n +8 | xargs -r rm --
```

## Python для DevOps

```python
#!/usr/bin/env python3
"""Найти поды не в Running и вывести причину."""
import json, subprocess, sys

out = subprocess.run(["kubectl", "get", "pods", "-A", "-o", "json"],
                     capture_output=True, text=True, check=True).stdout
for p in json.loads(out)["items"]:
    phase = p["status"]["phase"]
    if phase != "Running":
        reasons = [cs.get("state", {}).get("waiting", {}).get("reason")
                   for cs in p["status"].get("containerStatuses", [])]
        print(f'{p["metadata"]["namespace"]}/{p["metadata"]["name"]}: {phase} {reasons}')
```

**Парсинг логов с collections.Counter**
```python
from collections import Counter
import re
pat = re.compile(r'^(\S+) .* "(\w+) (\S+) [^"]+" (\d{3})')
c = Counter()
with open("access.log") as f:
    for line in f:
        if m := pat.match(line):
            ip, method, path, status = m.groups()
            if status.startswith("5"):
                c[ip] += 1
for ip, n in c.most_common(5):
    print(ip, n)
```

**HTTP health-check с ретраями**
```python
import time, requests
def check(url, retries=3, backoff=2):
    for i in range(retries):
        try:
            r = requests.get(url, timeout=5)
            if r.ok: return True
        except requests.RequestException as e:
            print(f"try {i+1}: {e}")
        time.sleep(backoff ** i)
    return False
```

Полезные библиотеки: `requests/httpx`, `boto3`, `kubernetes`, `pyyaml`, `click/typer`, `paramiko/fabric`, `jinja2`, `pytest`. Для CLI-утилит команды всё чаще пишут на **Go**.

## ❓ Вопросы
1. Что делает `set -euo pipefail`?
2. Разница `$@` и `$*`?
3. Как обработать сигналы в скрипте? — `trap`.
4. Как сделать скрипт идемпотентным?
5. Когда Bash, а когда Python/Go? — Bash для склейки команд до ~100 строк; дальше — Python/Go (структуры данных, тесты, ошибки).


---

<a id="m11"></a>

# 11. DevSecOps

## Shift Left
Безопасность встраивается в пайплайн как можно раньше, а не проверяется перед релизом.

| Проверка | Что ищет | Инструменты |
|----------|----------|-------------|
| Secrets scanning | Ключи/пароли в коде | gitleaks, trufflehog, GitHub push protection |
| SAST | Уязвимости в коде | Semgrep, SonarQube, CodeQL |
| SCA | Уязвимые зависимости | Trivy, Grype, Dependabot, Renovate, Snyk |
| IaC scanning | Ошибки конфигурации | Checkov, Trivy config, tfsec (в Trivy), KICS |
| Container scanning | CVE в образах | Trivy, Grype, Docker Scout |
| DAST | Уязвимости работающего приложения | OWASP ZAP, Burp |
| Runtime | Аномалии в рантайме | Falco, Tetragon (eBPF) |

## Supply chain security
- **SBOM** (Software Bill of Materials) — список компонентов: SPDX, CycloneDX (`syft`, `trivy sbom`).
- **Подпись образов**: cosign / Sigstore (keyless через OIDC), проверка admission-политикой (Kyverno, sigstore policy-controller).
- **SLSA** — уровни зрелости сборки (provenance, изолированный builder).
- Пиннинг зависимостей и actions по digest/SHA, приватные зеркала, проверка контрольных сумм.
- Примеры атак: SolarWinds, Codecov, xz-utils backdoor (2024), tj-actions/changed-files (2025), атаки на npm-пакеты (Shai-Hulud, 2025).

## Секреты
- **Vault** (HashiCorp) / OpenBao (open-source форк): динамические секреты (временные креды БД), lease, ротация, аудит.
- Облачные: AWS Secrets Manager, Yandex Lockbox.
- В K8s: External Secrets Operator, Vault Agent/CSI, Sealed Secrets, SOPS (+ age/KMS).
- Принципы: короткоживущие креды > долгоживущие; OIDC/workload identity; никаких секретов в git, образах, env в логах.

## Принципы
- **Least privilege**, **defense in depth**, **zero trust** («никогда не доверяй, всегда проверяй»: mTLS, идентичность сервиса, проверка каждого запроса).
- Иммутабельная инфраструктура, минимальные образы, регулярные патчи.
- Сегментация сети (NetworkPolicy, SG).

## Hardening Linux
SSH: только ключи, `PermitRootLogin no`, `PasswordAuthentication no`; fail2ban; автообновления безопасности; файрвол; аудит (auditd); CIS Benchmarks.

## Kubernetes security
- RBAC с минимальными правами, отключить `automountServiceAccountToken` где не нужно.
- Pod Security Standards `restricted`.
- NetworkPolicy default deny.
- Шифрование Secrets в etcd, аудит-логи API.
- Проверка: `kube-bench` (CIS), `kubescape`, Trivy Operator.

## OWASP Top 10 (2025) — кратко
Broken Access Control, Security Misconfiguration, Software Supply Chain Failures, Cryptographic Failures, Injection, Insecure Design, Authentication Failures, Software/Data Integrity Failures, Logging & Alerting Failures, Mishandling of Exceptional Conditions.

## ❓ Вопросы
1. Что такое DevSecOps и shift left?
2. SAST vs DAST vs SCA?
3. Как хранить секреты в K8s?
4. Что такое SBOM и зачем подписывать образы?
5. Нашли критическую CVE в базовом образе — действия? — оценить применимость/эксплуатируемость, обновить базу, пересобрать всё зависимое, задеплоить, добавить gate в CI.
6. Что такое zero trust?
7. Как защитить CI/CD от компрометации?


---

<a id="m12"></a>

# 12. SRE и управление инцидентами

## DevOps vs SRE vs Platform Engineering
- **DevOps** — культура и практики сотрудничества Dev и Ops, автоматизация, CI/CD.
- **SRE** — «что получится, если поручить эксплуатацию инженерам-программистам» (Google). Конкретная реализация DevOps через SLO, error budget, борьбу с toil.
- **Platform Engineering** — команда строит внутреннюю платформу (IDP) с «golden paths», чтобы разработчики сами деплоили без тикетов.

## SLI / SLO / SLA
- **SLI** — измеряемый показатель: доля успешных запросов, доля запросов быстрее 300 мс.
- **SLO** — цель по SLI: 99.9% успешных запросов за 28 дней.
- **SLA** — договор с клиентом с последствиями (штрафы); SLA мягче SLO.

### Таблица «девяток»
| Доступность | Даунтайм в год | В месяц (30д) |
|-------------|---------------|---------------|
| 99% | 3.65 дня | 7.2 ч |
| 99.9% | 8.76 ч | 43.2 мин |
| 99.95% | 4.38 ч | 21.6 мин |
| 99.99% | 52.6 мин | 4.32 мин |
| 99.999% | 5.26 мин | 26 сек |

> Доступность последовательных компонентов перемножается: 99.9% × 99.9% = 99.8%.

## Error budget
`Бюджет = 1 − SLO`. При 99.9% — 0.1% запросов могут быть ошибочными.
- Бюджет есть → релизим, экспериментируем.
- Бюджет исчерпан → фриз фич, фокус на надёжности.
- **Burn rate alerts** (multi-window, multi-burn-rate): например, сжигание 2% бюджета за 1 час (burn rate 14.4) → пейджинг; 5% за 6 ч → пейджинг; 10% за 3 дня → тикет.

## Toil
Ручная, повторяющаяся, автоматизируемая работа без долгосрочной ценности. Цель SRE — < 50% времени на toil.

## Управление инцидентами
**Роли:** Incident Commander (координирует), Ops/Tech lead (чинит), Communications (статус стейкхолдерам), Scribe.

**Порядок:**
1. Обнаружить (алерт/пользователи) → объявить инцидент, severity (SEV1–SEV4).
2. **Mitigate first** — сначала восстановить сервис (откат, переключение, скейл, feature flag), причину искать потом.
3. Коммуникация: статус-страница, регулярные апдейты.
4. Разрешение и наблюдение.
5. **Blameless postmortem**.

**Метрики:** MTTD (обнаружение), MTTA (подтверждение), MTTR (восстановление), MTBF.

## Postmortem — шаблон
- Резюме, влияние (сколько пользователей, сколько времени, деньги).
- Таймлайн.
- Root cause и способствующие факторы (5 Whys).
- Что сработало хорошо / плохо / где повезло.
- Action items с владельцами и сроками.
- **Без поиска виноватых** — ищем системные причины.

## Надёжность: паттерны
- Timeouts, retries с **exponential backoff + jitter**, **circuit breaker**, bulkhead, rate limiting, graceful degradation, load shedding.
- Идемпотентность операций (для безопасных ретраев).
- Избегать retry storm: бюджет ретраев, ретраить только на одном уровне.
- **Chaos engineering**: Chaos Mesh, LitmusChaos, Gremlin; game days.
- Capacity planning, нагрузочное тестирование (k6, Gatling, Locust).

## On-call
Разумная ротация, runbooks на каждый алерт, компенсация, разбор шумных алертов, эскалация (PagerDuty, Opsgenie → в 2025 Atlassian объявил его закрытие, Grafana OnCall/IRM, incident.io).

## ❓ Вопросы
1. SLI vs SLO vs SLA?
2. Сколько даунтайма в месяц допускает 99.95%?
3. Что такое error budget и как он влияет на релизы?
4. Как ты проводишь инцидент? Расскажи о реальном.
5. Что такое blameless postmortem?
6. Что такое toil?
7. Retry + backoff + jitter — зачем jitter? — Чтобы клиенты не ретраили синхронно (thundering herd).
8. DevOps vs SRE?


---

<a id="m13"></a>

# 13. System Design для DevOps

## Шаблон ответа (45 минут)

1. **Уточнить требования (5–7 мин)**
   - Функциональные: что делает система.
   - Нефункциональные: RPS, пользователи, гео, latency, доступность (SLO), RPO/RTO, бюджет, compliance (152-ФЗ, GDPR), команда.
2. **Оценки (3 мин)** — нагрузка, объём данных, трафик.
3. **Высокоуровневая схема (10 мин)** — нарисовать блоки.
4. **Углубление (15 мин)** — сеть, деплой, данные, масштабирование, отказоустойчивость, безопасность, observability.
5. **Узкие места и trade-off (5 мин)**.
6. **Эволюция** — что делать при x10.

> Говори вслух, задавай вопросы, называй trade-off. Нет «правильного» ответа — оценивают ход мысли.

## Чек-лист тем для любой задачи
- [ ] Вход: DNS, CDN, WAF, LB (L4/L7), TLS.
- [ ] Вычисления: K8s/ВМ/serverless, автоскейлинг, multi-AZ.
- [ ] Данные: БД (репликация, шардирование), кэш (Redis), очередь (Kafka/RabbitMQ), объектное хранилище.
- [ ] Деплой: CI/CD, GitOps, стратегии, откат.
- [ ] Конфигурация и секреты.
- [ ] Observability: метрики, логи, трейсы, SLO-алерты.
- [ ] Безопасность: IAM, сеть, шифрование at rest/in transit.
- [ ] DR: бэкапы, RPO/RTO, multi-region?
- [ ] Стоимость.

## Типовые задачи

### 1. Инфраструктура для веб-приложения на 1M пользователей
CDN → WAF → ALB (multi-AZ) → K8s (HPA + Karpenter, 3 AZ) → Redis (кэш/сессии) → PostgreSQL (primary + реплики, Multi-AZ, PITR) → S3 для статики/файлов. Kafka для асинхронных задач. GitOps (Argo CD), Prometheus/Grafana/Loki/Tempo, Vault. Бэкапы в другой регион.

### 2. CI/CD-платформа для 200 микросервисов
Шаблоны пайплайнов (include/reusable workflows), автоскейлинг runner'ов в K8s, кэш и общий реестр, build once deploy many, GitOps-монорепо конфигурации, ApplicationSet, preview-окружения на MR, политики (Kyverno), подписи образов, DORA-метрики, IDP (Backstage) с golden paths.

### 3. Централизованное логирование для 500 нод, 2 ТБ/день
Агент (Fluent Bit/Vector/Alloy) на ноде → буфер Kafka (развязка и защита от пиков) → обработка → хранилище: Loki (дёшево, S3) или ClickHouse/OpenSearch (полнотекстовый поиск). Ретенция: горячее 7 дней, холодное в S3 90 дней. Семплирование debug-логов, лимиты на tenant'а.

### 4. Мониторинг для 50 K8s-кластеров
Prometheus/vmagent в каждом кластере → remote_write в центральный Mimir/VictoriaMetrics/Thanos (multi-tenant) → Grafana. Alertmanager HA, единые правила через GitOps, контроль кардинальности.

### 5. Миграция монолита из ДЦ в облако / K8s
Оценка (6R: rehost, replatform, refactor…), сеть (VPN/interconnect), перенос данных (репликация, CDC), strangler fig pattern, поэтапное переключение трафика (DNS weighted), план отката.

### 6. Zero-downtime деплой с миграцией БД
Expand/contract, обратная совместимость версий, rolling/canary, feature flags, миграции отдельной Job до деплоя, проверка через метрики.

### 7. Multi-region active-active
Global LB / GeoDNS / anycast, данные: выбрать между консистентностью и доступностью (CAP) — глобальные БД (CockroachDB, YDB, Spanner) или регион-владелец данных + асинхронная репликация, конфликты, стоимость межрегионального трафика.

## Полезные числа
- Чтение из RAM ~100 нс, SSD ~100 мкс, сеть внутри ДЦ ~0.5 мс, межконтинентальный RTT ~150 мс.
- 1M запросов/день ≈ 12 RPS (пик ×3–10).
- 1 день = 86 400 с.

## Теоремы
- **CAP**: при сетевом разделении выбираешь консистентность или доступность.
- **PACELC**: и без разделения — компромисс latency vs consistency.


---

<a id="m14"></a>

# 14. Практика: troubleshooting-кейсы и live-coding

Формат: интервьюер описывает проблему, ты говоришь, **что проверяешь и в каком порядке**. Оценивают системность.

> Общий алгоритм: **что изменилось?** (деплой, конфиг, нагрузка) → масштаб (все/часть) → от симптома вниз по стеку → mitigate → root cause.

---

### Кейс 1. «Сайт открывается медленно»
1. Все ли пользователи/регионы? Когда началось? Был ли релиз?
2. Метрики: latency по сервисам (трейсы — где тратится время), RPS, ошибки, saturation.
3. `curl -w` — разложить по DNS/connect/TLS/TTFB.
4. Бэкенд: CPU/память/GC, пулы соединений, медленные запросы к БД (`pg_stat_statements`), блокировки, кэш hit rate.
5. Mitigation: откат, скейл, отключить тяжёлую фичу.

### Кейс 2. «Под в CrashLoopBackOff после деплоя»
`kubectl describe` (exit code, events) → `logs --previous` → нет конфига/секрета? неправильная команда? liveness слишком строгая? OOMKilled (137)? Нет доступа к БД? → `rollout undo`.

### Кейс 3. «Диск на сервере заполнился на 100%»
`df -h` → `du -xh --max-depth=1 / | sort -h` → логи? (`journalctl --vacuum-size=500M`, logrotate) → docker (`docker system df`) → удалённые открытые файлы (`lsof +L1`) → `df -i` (inode). Долгосрочно: алерт на `predict_linear`, ротация.

### Кейс 4. «Сервис не может подключиться к БД»
DNS резолвится? `nc -zv db 5432`? Security group/NetworkPolicy/firewall? Креды/секрет ротировали? `max_connections` исчерпан? TLS-сертификат истёк? БД жива?

### Кейс 5. «Внезапно вырос счёт за облако x2»
Cost Explorer по сервисам/тегам → чаще всего: NAT/межзональный трафик, забытые ресурсы, логи (CloudWatch ingestion), автоскейлинг вышел из-под контроля, утечка ключа → майнинг.

### Кейс 6. «После обновления ноды K8s поды не стартуют: Pending»
`describe pod` → Insufficient cpu/memory? taint на новой ноде? PVC в другой AZ (volume node affinity conflict)? Лимит IP в подсети (EKS VPC CNI)?

### Кейс 7. «Терраформ хочет пересоздать базу данных в проде»
СТОП. Смотреть plan: какой атрибут вызывает `forces replacement`? Изменили имя/ключ for_each (→ `moved {}`)? Обновили провайдер? Кто-то менял руками (drift)? Добавить `prevent_destroy`.

### Кейс 8. «Сертификат истёк, сайт лежит»
Mitigation: выпустить вручную, задеплоить. Root cause: почему не продлился (cert-manager логи, ACME challenge, DNS, rate limit). Действия: алерт за 21/7 дней (`probe_ssl_earliest_cert_expiry`), автоматизация.

### Кейс 9. «Периодические 502 на ingress»
Поды убиваются во время запросов при деплое → `preStop: sleep 10`, graceful shutdown, readiness. Keep-alive таймаут апстрима меньше, чем у прокси → выровнять. OOM подов.

---

## Live-coding задачи

1. **Напиши Dockerfile** для Node.js/Python/Go приложения (multi-stage, non-root, кэш).
2. **Напиши Deployment + Service + Ingress** с probes, ресурсами, 3 репликами, anti-affinity.
3. **Напиши пайплайн** CI: тест → сборка → пуш → деплой.
4. **Terraform**: VPC + 2 подсети + SG + ВМ, вынести в модуль.
5. **Bash**: распарсить лог, посчитать топ, проверить список хостов.
6. **Python**: вызвать API (GitHub/K8s), отфильтровать, вывести таблицу/JSON.
7. **PromQL**: доля ошибок, p99, алерт.
8. **«Найди баги в манифесте»** — типичные:
   - селектор Service не совпадает с лейблами подов;
   - `targetPort` ≠ `containerPort`;
   - liveness без `initialDelaySeconds`/startupProbe;
   - `image: app:latest` + `imagePullPolicy: IfNotPresent`;
   - отсутствуют requests/limits;
   - secret в `env.value` открытым текстом.

Попробуй сам: возьми манифест, Dockerfile или лог и найди в нём ошибки.


---

<a id="m15"></a>

# 15. Soft skills, HR и переговоры

## Метод STAR
- **S**ituation — контекст.
- **T**ask — твоя задача.
- **A**ction — что сделал *ты* (не «мы»).
- **R**esult — результат в цифрах.

> Пример: «Деплой занимал 40 минут и падал в 20% случаев (S). Мне поручили ускорить (T). Я перевёл сборку на BuildKit с кэшем, распараллелил тесты, ввёл Argo CD (A). Время деплоя — 7 минут, change failure rate — 4% (R).»

## Подготовь истории
1. Самый сложный инцидент.
2. Автоматизация, которой гордишься.
3. Ошибка, которую ты совершил, и чему научился.
4. Конфликт / несогласие с коллегой или руководителем.
5. Как внедрил изменение, которому сопротивлялись.
6. Как учил/менторил коллег.
7. Как расставлял приоритеты при завале задач.

## Частые вопросы
- Расскажи о себе (2 минуты: опыт → стек → достижения → почему здесь).
- Почему уходишь с текущего места? (позитивно, без критики)
- Опиши архитектуру текущего проекта.
- Как следишь за новыми технологиями?
- Как используешь AI-инструменты в работе? (конкретно: генерация манифестов/скриптов, разбор логов; всегда ревью, не отдаёшь секреты, не применяешь в прод без проверки)
- Где видишь себя через 2–3 года?

## Вопросы работодателю
1. Как устроен on-call? Сколько алертов в неделю?
2. Как часто деплоите и сколько занимает путь от коммита до прода?
3. Какой стек и что планируете менять?
4. Сколько людей в DevOps/платформенной команде и сколько разработчиков на них?
5. Какие главные проблемы инфраструктуры сейчас?
6. Как выглядит успех на этой позиции через 3 и 6 месяцев?
7. Есть ли бюджет на обучение/конференции/сертификации?
8. Как проходит постмортем — есть ли культура blameless?

## Переговоры о зарплате
- Изучи рынок (hh.ru, Хабр Карьера — отчёты о зарплатах, levels.fyi, сообщества).
- Первую цифру называй вилкой с нижней границей чуть выше желаемого минимума.
- Уточняй: gross/net, бонусы, ДМС, удалёнка, оборудование, обучение.
- Несколько офферов — сильная позиция; будь честным.
- Встречный оффер от текущей работы редко решает причину ухода.

## Сертификации (по желанию, плюс к резюме)
CKA, CKAD, CKS (Kubernetes); AWS SAA / DevOps Pro; HashiCorp Terraform Associate; Yandex Cloud сертификации.

## Красные флаги у компании
- «DevOps — это человек, который делает всё».
- Нет мониторинга, деплой руками по SSH в прод, и менять это не планируют.
- On-call без компенсации.
- Тестовое задание на неделю.


---

<a id="cheatsheet"></a>

# ⚡ DevOps-шпаргалка на одной странице

> Повторить за час до собеседования.

## Linux
| Задача | Команда |
|--------|---------|
| Нагрузка | `uptime`, `top`, `vmstat 1`, `iostat -xz 1` |
| Память | `free -h` (смотри **available**), `dmesg -T \| grep -i oom` |
| Диск | `df -h`, `df -i`, `du -xh --max-depth=1 / \| sort -h`, `lsof +L1` |
| Порты | `ss -tulpn`, `ss -lptn 'sport = :80'` |
| Процесс | `ps aux --sort=-%cpu`, `strace -p PID`, `lsof -p PID` |
| Сервис | `systemctl status X`, `journalctl -u X -f` |

- Сигналы: TERM(15) вежливо, KILL(9) насильно, HUP(1) перечитать конфиг.
- D-state не убивается; зомби — чинить родителя.
- LA = R + D процессы; сравнивать с `nproc`.

## Сети
- OSI: Physical → Data Link → Network → Transport → Session → Presentation → Application.
- TCP: SYN / SYN-ACK / ACK. UDP — без соединения. HTTP/3 = QUIC поверх UDP.
- 502 — плохой ответ апстрима, 503 — нет доступных, 504 — таймаут апстрима.
- DNS: A, AAAA, CNAME, MX, TXT, NS, SRV, PTR. `dig +trace`.
- `/24`=256, `/16`=65536. Приватные: 10/8, 172.16/12, 192.168/16.
- `curl -w "%{time_namelookup} %{time_connect} %{time_appconnect} %{time_total}"`.

## Git
- merge — сохраняет историю; rebase — линейная, только для своих веток.
- revert — безопасная отмена pushed; reset — переписывает.
- Потерял? → `git reflog`. Push после rebase → `--force-with-lease`.

## Docker
- Контейнер = процесс + namespaces (видимость) + cgroups (ресурсы).
- Multi-stage, distroless, non-root, digest, `.dockerignore`, `--mount=type=secret`.
- exec-форма `["app"]` → сигналы доходят. Exit 137 = SIGKILL/OOM.
- Слои кэшируются сверху вниз — зависимости раньше кода.

## Kubernetes
- CP: apiserver, etcd, scheduler, controller-manager. Node: kubelet, kube-proxy, CRI, CNI.
- apply → API (authn → authz → admission) → etcd → controller → scheduler → kubelet.
- Deployment / StatefulSet / DaemonSet / Job / CronJob.
- Service: ClusterIP / NodePort / LoadBalancer / Headless. DNS `svc.ns.svc.cluster.local`.
- Probes: startup → readiness (трафик) / liveness (рестарт). Liveness не зависит от БД!
- QoS: Guaranteed / Burstable / BestEffort. Memory > limit → OOMKilled; CPU > limit → throttling.
- Отладка: `describe` → `logs --previous` → `get events` → `exec`/`debug`.
- Pending → ресурсы/taints/affinity/PVC. ImagePullBackOff → образ/секрет. CrashLoop → логи.
- Zero downtime: readiness + `maxUnavailable: 0` + preStop sleep + graceful shutdown + PDB.
- Secret = base64, не шифрование → ESO/Vault/SOPS + шифрование etcd.
- Ingress → Gateway API. Автоскейл: HPA, VPA, KEDA, Cluster Autoscaler/Karpenter.

## CI/CD
- lint → test → build → scan → push(sign, SBOM) → deploy dev → e2e → stage → prod.
- Build once, deploy many. OIDC вместо статических ключей. Pin actions по SHA.
- Rolling / Recreate / Blue-Green / Canary / Feature flags.
- GitOps: Git = источник истины, pull, reconcile (Argo CD, Flux).
- DORA: deploy frequency, lead time, change failure rate, MTTR.
- Миграции БД: expand → migrate → contract.

## Terraform / Ansible
- init → plan → apply. State: remote + lock + encrypt.
- `for_each` > `count`. Рефакторинг: `moved {}`. Существующее: `import {}`.
- lifecycle: `prevent_destroy`, `create_before_destroy`, `ignore_changes`.
- Drift → plan в CI. OpenTofu — open-source форк.
- Ansible: agentless, SSH, идемпотентность, роли, handlers, vault.

## Облако
- Region → AZ. Прод ≥ 2–3 AZ.
- SG stateful (allow) vs NACL stateless (allow+deny).
- Private subnet → NAT GW. S3 без интернета → VPC endpoint.
- Роли/IRSA/Pod Identity/OIDC вместо ключей. Explicit Deny побеждает.
- RPO — потеря данных, RTO — время восстановления. Бэкапы 3-2-1 + тест восстановления.
- FinOps: теги, rightsizing, spot, RI/SP, lifecycle, NAT-трафик, ARM.

## Observability
- RED (Rate, Errors, Duration), USE (Utilization, Saturation, Errors), 4 Golden Signals.
- Counter → `rate()`. Histogram → `histogram_quantile(0.99, sum by (le)(rate(x_bucket[5m])))`.
- Кардинальность: никаких user_id в лейблах.
- Ошибки: `sum(rate(req{status=~"5.."}[5m])) / sum(rate(req[5m]))`.
- Алерт: на симптом, actionable, с runbook, `for:`.
- Логи: Loki/ELK; трейсы: Tempo/Jaeger; стандарт — OpenTelemetry.

## Security
- Shift left: secrets scan, SAST, SCA, IaC scan, image scan, DAST, runtime (Falco).
- Supply chain: SBOM, cosign, SLSA, pin по digest.
- Least privilege, defense in depth, zero trust, mTLS.
- Утёк ключ → отозвать и ротировать **сначала**, чистить историю потом.

## SRE
- SLI (метрика) → SLO (цель) → SLA (договор).
- 99.9% = 43 мин/мес, 99.99% = 4.3 мин/мес.
- Error budget = 1 − SLO. Алерты на burn rate.
- Инцидент: mitigate first → коммуникация → root cause → blameless postmortem.
- Retries + exponential backoff + **jitter**, circuit breaker, timeouts.

## System Design
Требования (RPS, SLO, RPO/RTO, бюджет) → оценки → схема → углубление → trade-off → x10.
Вход (DNS/CDN/WAF/LB) → compute (K8s, multi-AZ, autoscale) → данные (БД+реплики, кэш, очередь, S3) → CI/CD → observability → security → DR → cost.

## Soft
STAR. 3 истории: инцидент, автоматизация, ошибка. Знай цифры своего проекта. 3–5 вопросов работодателю.


---

<a id="questions"></a>

# ❓ 150 вопросов с собеседований DevOps 2026

> Закрой ответ, ответь вслух, потом раскрой ▶️ и проверь себя.
> 🟢 Junior · 🟡 Middle · 🔴 Senior

---

## 🐧 Linux (1–20)

<details><summary>1. 🟢 Процесс vs поток?</summary>Поток делит адресное пространство и дескрипторы процесса; процессы изолированы друг от друга.</details>
<details><summary>2. 🟢 Что такое зомби-процесс?</summary>Завершившийся процесс, чей код возврата не прочитал родитель (`wait()`). Убрать — перезапустить/исправить родителя.</details>
<details><summary>3. 🟢 SIGTERM vs SIGKILL?</summary>TERM можно перехватить и корректно завершиться; KILL — немедленно ядром, перехватить нельзя.</details>
<details><summary>4. 🟡 Почему `kill -9` не убивает процесс?</summary>Процесс в D-state (uninterruptible I/O, например NFS) или уже зомби.</details>
<details><summary>5. 🟢 Что показывает load average?</summary>Среднее число процессов в R и D за 1/5/15 мин. Сравнивать с числом ядер.</details>
<details><summary>6. 🟡 Высокий LA, но CPU простаивает — почему?</summary>Процессы ждут I/O (D-state): диск, NFS. Смотреть `iostat -x`, `vmstat` (колонки b, wa).</details>
<details><summary>7. 🟢 Что такое inode?</summary>Структура с метаданными файла (права, владелец, блоки), без имени. Могут закончиться раньше места — `df -i`.</details>
<details><summary>8. 🟢 Hard link vs symlink?</summary>Hard — ещё одно имя того же inode в пределах ФС; symlink — отдельный файл с путём, может «висеть».</details>
<details><summary>9. 🟡 `df` показывает 100%, `du` — 40%. Почему?</summary>Удалённый файл держит открытым процесс. `lsof +L1`, перезапустить процесс или обнулить через `/proc/PID/fd`.</details>
<details><summary>10. 🟢 free vs available в `free -h`?</summary>available учитывает освобождаемый page cache — это реальная доступная память.</details>
<details><summary>11. 🟡 Как работает OOM killer?</summary>При нехватке памяти ядро убивает процесс с наибольшим `oom_score` (с учётом `oom_score_adj`). Следы — `dmesg`.</details>
<details><summary>12. 🟢 Что делает `chmod 755` и `chmod 4755`?</summary>rwxr-xr-x; 4 — SUID: запуск с правами владельца файла.</details>
<details><summary>13. 🟢 Как посмотреть слушающие порты?</summary>`ss -tulpn` (или `netstat -tulpn`, `lsof -i`).</details>
<details><summary>14. 🟡 Порядок загрузки Linux?</summary>UEFI/BIOS → GRUB → ядро + initramfs → systemd (PID 1) → targets → сервисы.</details>
<details><summary>15. 🟢 Как сделать сервис автозапускаемым?</summary>Юнит в `/etc/systemd/system`, `systemctl daemon-reload && systemctl enable --now svc`.</details>
<details><summary>16. 🟡 «Too many open files» — что делать?</summary>Поднять лимит: `LimitNOFILE` в юните, `ulimit -n`, `/etc/security/limits.conf`; проверить утечку дескрипторов.</details>
<details><summary>17. 🟡 Что такое swap и нужен ли он серверу?</summary>Выгрузка страниц на диск. Небольшой swap спасает от OOM, но может вызывать деградацию; для БД/K8s традиционно минимизируют (`vm.swappiness`).</details>
<details><summary>18. 🟢 Как найти большие файлы?</summary>`find / -xdev -type f -size +1G`, `du -xh --max-depth=1 / | sort -h`, `ncdu`.</details>
<details><summary>19. 🟡 Что такое strace и когда использовать?</summary>Трассировка системных вызовов: процесс «висит», не может открыть файл, к чему подключается.</details>
<details><summary>20. 🔴 Как диагностировать медленный сервер за 60 секунд?</summary>uptime, dmesg, vmstat 1, mpstat -P ALL, pidstat, iostat -xz, free -m, sar -n DEV, sar -n TCP,ETCP, top (метод Брендана Грегга).</details>

## 🌐 Сети (21–40)

<details><summary>21. 🟢 Модель OSI?</summary>Physical, Data Link, Network, Transport, Session, Presentation, Application.</details>
<details><summary>22. 🟢 TCP vs UDP?</summary>TCP — соединение, гарантия доставки и порядка; UDP — без соединения и гарантий, быстрее.</details>
<details><summary>23. 🟢 Трёхстороннее рукопожатие TCP?</summary>SYN → SYN-ACK → ACK.</details>
<details><summary>24. 🟡 Что такое TIME_WAIT?</summary>Состояние закрывшей первой стороны на 2×MSL, чтобы поздние пакеты не попали в новое соединение.</details>
<details><summary>25. 🟢 Как работает DNS-резолв?</summary>Кэш → hosts → рекурсивный резолвер → root → TLD → authoritative → ответ кэшируется по TTL.</details>
<details><summary>26. 🟢 A vs CNAME?</summary>A — имя → IPv4; CNAME — имя → другое имя. CNAME нельзя на apex.</details>
<details><summary>27. 🟢 502 vs 503 vs 504?</summary>502 — некорректный ответ апстрима; 503 — сервис недоступен; 504 — апстрим не ответил за таймаут.</details>
<details><summary>28. 🟡 HTTP/1.1 vs HTTP/2 vs HTTP/3?</summary>H2 — мультиплексирование в одном TCP, бинарный, HPACK; H3 — QUIC поверх UDP, нет TCP head-of-line blocking.</details>
<details><summary>29. 🟡 Как работает TLS handshake?</summary>ClientHello (шифры, key share, SNI) → ServerHello + сертификат → ECDHE общий ключ → симметричное шифрование. TLS 1.3 — 1-RTT.</details>
<details><summary>30. 🟡 Что такое mTLS?</summary>Обе стороны предъявляют сертификаты. Используется в service mesh и zero trust.</details>
<details><summary>31. 🟢 L4 vs L7 балансировщик?</summary>L4 — по IP/порту (TCP/UDP); L7 — видит HTTP: путь, заголовки, cookie, TLS termination.</details>
<details><summary>32. 🟢 Что такое NAT?</summary>Трансляция адресов: SNAT — приватные хосты выходят в интернет; DNAT — проброс портов внутрь.</details>
<details><summary>33. 🟢 Сколько адресов в /26?</summary>64 (62 хоста).</details>
<details><summary>34. 🟡 Что такое MTU и проблемы с ним?</summary>Максимальный размер кадра. В туннелях (VXLAN, VPN) — фрагментация/дроп: ping проходит, большие пакеты (TLS) виснут.</details>
<details><summary>35. 🟡 Что такое anycast?</summary>Один IP анонсируется из многих точек по BGP — трафик идёт к ближайшей (CDN, публичные DNS).</details>
<details><summary>36. 🟢 Что происходит при вводе URL в браузер?</summary>URL → DNS → TCP/QUIC → TLS → HTTP → CDN/LB → приложение → ответ → рендер.</details>
<details><summary>37. 🟡 Что такое CDN и как инвалидировать кэш?</summary>Сеть edge-кэшей. Инвалидация через API/purge или версионирование имён файлов (хеш в имени).</details>
<details><summary>38. 🟢 Как проверить доступность порта?</summary>`nc -zv host port`, `curl -v telnet://host:port`, `ss` на сервере.</details>
<details><summary>39. 🟡 Как снять трафик для анализа?</summary>`tcpdump -i any -nn host X and port 443 -w f.pcap` → Wireshark.</details>
<details><summary>40. 🔴 Проблема ndots в K8s?</summary>`ndots:5` → внешний домен сначала пробуется со всеми search-доменами → лишние DNS-запросы и задержки. Решение — FQDN с точкой, dnsConfig, NodeLocal DNSCache.</details>

## 🌿 Git (41–48)

<details><summary>41. 🟢 merge vs rebase?</summary>merge — merge-коммит, сохраняет историю; rebase — переписывает коммиты поверх base, линейная история, не для общих веток.</details>
<details><summary>42. 🟢 Как отменить запушенный коммит?</summary>`git revert <sha>`.</details>
<details><summary>43. 🟢 fetch vs pull?</summary>pull = fetch + merge (или rebase).</details>
<details><summary>44. 🟡 Как восстановить удалённую ветку/коммит?</summary>`git reflog` → `git branch name <sha>`.</details>
<details><summary>45. 🟡 reset --soft/--mixed/--hard?</summary>soft — изменения в index; mixed — в рабочей копии; hard — удалить.</details>
<details><summary>46. 🟡 Что такое `--force-with-lease`?</summary>Force push, который откажет, если удалённая ветка изменилась с последнего fetch.</details>
<details><summary>47. 🟡 Trunk-based vs GitFlow?</summary>Trunk — короткие ветки, частые мержи, feature flags (под CI/CD); GitFlow — долгие ветки develop/release, тяжеловесно.</details>
<details><summary>48. 🟡 Закоммитили секрет — что делать?</summary>Сначала отозвать/ротировать секрет, затем чистить историю (git filter-repo/BFG), включить secret scanning.</details>

## 🐳 Docker (49–62)

<details><summary>49. 🟢 Контейнер vs ВМ?</summary>Контейнер — изолированный процесс на общем ядре; ВМ — полная ОС со своим ядром на гипервизоре.</details>
<details><summary>50. 🟡 Что такое namespaces и cgroups?</summary>namespaces — изоляция видимости (pid, net, mnt, uts, ipc, user); cgroups — ограничение ресурсов.</details>
<details><summary>51. 🟢 Образ vs контейнер?</summary>Образ — read-only шаблон из слоёв; контейнер — запущенный экземпляр с writable-слоем.</details>
<details><summary>52. 🟢 Как уменьшить образ?</summary>Multi-stage, slim/distroless база, меньше слоёв, чистка кэшей пакетного менеджера, `.dockerignore`.</details>
<details><summary>53. 🟢 CMD vs ENTRYPOINT?</summary>ENTRYPOINT — что запускается; CMD — аргументы по умолчанию, легко переопределить.</details>
<details><summary>54. 🟡 exec vs shell form?</summary>exec `["app"]` — app = PID 1 и получает сигналы; shell — PID 1 = sh, SIGTERM не доходит.</details>
<details><summary>55. 🟢 COPY vs ADD?</summary>ADD умеет URL и распаковку tar; предпочитать COPY.</details>
<details><summary>56. 🟡 Как работает кэш слоёв?</summary>Слой переиспользуется, если инструкция и входы не изменились; изменение инвалидирует все последующие.</details>
<details><summary>57. 🟢 volume vs bind mount?</summary>volume управляется Docker; bind — произвольный путь хоста.</details>
<details><summary>58. 🟡 Exit code 137?</summary>128+9 — SIGKILL, чаще всего OOMKilled.</details>
<details><summary>59. 🟡 Как безопасно передать секрет при сборке?</summary>`RUN --mount=type=secret,id=x` (BuildKit), не ARG/ENV.</details>
<details><summary>60. 🟡 Почему опасно монтировать docker.sock?</summary>Доступ к сокету = root на хосте.</details>
<details><summary>61. 🟡 Docker vs containerd vs runc?</summary>Docker — инструмент/демон; containerd — высокоуровневый рантайм (CRI для K8s); runc — запуск контейнера по OCI-спеке.</details>
<details><summary>62. 🟡 Как собрать образ под arm64 и amd64?</summary>`docker buildx build --platform linux/amd64,linux/arm64 --push`.</details>

## ☸️ Kubernetes (63–90)

<details><summary>63. 🟢 Компоненты control plane?</summary>kube-apiserver, etcd, kube-scheduler, kube-controller-manager (+ cloud-controller-manager).</details>
<details><summary>64. 🟢 Компоненты worker-ноды?</summary>kubelet, kube-proxy, container runtime (containerd), CNI.</details>
<details><summary>65. 🟡 Что происходит при `kubectl apply`?</summary>API: authn → authz → admission → etcd; контроллеры создают RS/Pods; scheduler выбирает ноду; kubelet запускает через CRI/CNI/CSI.</details>
<details><summary>66. 🟢 Pod vs Deployment?</summary>Pod — единица запуска; Deployment управляет ReplicaSet'ами: реплики, rolling update, откат.</details>
<details><summary>67. 🟢 Deployment vs StatefulSet?</summary>StatefulSet: стабильные имена, свой PVC на под, упорядоченный запуск — для БД/кластерного ПО.</details>
<details><summary>68. 🟢 Что такое DaemonSet?</summary>Под на каждой (подходящей) ноде — агенты логов/мониторинга/CNI.</details>
<details><summary>69. 🟢 Типы Service?</summary>ClusterIP, NodePort, LoadBalancer, ExternalName, Headless.</details>
<details><summary>70. 🟡 Как Service работает под капотом?</summary>kube-proxy (или Cilium eBPF) настраивает DNAT с виртуального IP на IP готовых подов из EndpointSlice.</details>
<details><summary>71. 🟢 readiness vs liveness?</summary>readiness — убирает под из балансировки; liveness — рестартует контейнер.</details>
<details><summary>72. 🟡 Зачем startupProbe?</summary>Для медленно стартующих приложений: пока не прошла, liveness не убивает контейнер.</details>
<details><summary>73. 🟢 requests vs limits?</summary>requests — для планирования (гарантия); limits — потолок.</details>
<details><summary>74. 🟡 QoS-классы?</summary>Guaranteed (req=lim), Burstable, BestEffort — порядок выселения при нехватке ресурсов обратный.</details>
<details><summary>75. 🟡 Что будет при превышении CPU и памяти?</summary>CPU — throttling; память — OOMKilled.</details>
<details><summary>76. 🟢 Под в Pending — причины?</summary>Нет ресурсов, taints, nodeSelector/affinity, не связан PVC, лимиты квоты.</details>
<details><summary>77. 🟢 CrashLoopBackOff — действия?</summary>`describe` (exit code, events), `logs --previous`, конфиги/секреты, probes, OOM, откат.</details>
<details><summary>78. 🟡 taints/tolerations vs affinity?</summary>Taint — нода отталкивает поды; affinity — под притягивается к нодам/подам.</details>
<details><summary>79. 🟡 Что такое PDB?</summary>PodDisruptionBudget — минимум доступных подов при добровольных прерываниях (drain, апгрейд).</details>
<details><summary>80. 🟡 HPA vs VPA vs KEDA?</summary>HPA — число реплик по метрикам; VPA — requests; KEDA — по внешним событиям, scale-to-zero.</details>
<details><summary>81. 🟡 Cluster Autoscaler vs Karpenter?</summary>CA масштабирует группы нод; Karpenter подбирает тип инстанса под pending-поды напрямую, быстрее, консолидирует.</details>
<details><summary>82. 🟡 Почему Secret небезопасен?</summary>base64, хранится в etcd открыто без encryption at rest; доступен всем с правом get secrets.</details>
<details><summary>83. 🟡 Ingress vs Gateway API?</summary>Gateway API — новый стандарт: разделение ролей, L4/L7, gRPC, богаче маршрутизация, переносимость; ingress-nginx уходит из поддержки.</details>
<details><summary>84. 🟡 Как сделать zero-downtime деплой?</summary>readiness, maxUnavailable 0, preStop sleep, обработка SIGTERM, PDB, достаточный terminationGracePeriod.</details>
<details><summary>85. 🟡 Helm vs Kustomize?</summary>Helm — шаблоны + релизы + пакеты; Kustomize — патчи и overlays без шаблонов.</details>
<details><summary>86. 🟡 Что такое оператор?</summary>CRD + контроллер, автоматизирующий эксплуатацию сложного ПО (бэкапы, failover).</details>
<details><summary>87. 🟡 RBAC в K8s?</summary>Role/ClusterRole (права) + RoleBinding/ClusterRoleBinding (к пользователю/группе/ServiceAccount).</details>
<details><summary>88. 🔴 Как поды на разных нодах общаются?</summary>CNI: overlay (VXLAN/Geneve) или прямая маршрутизация (BGP), либо eBPF (Cilium); у каждого пода свой IP без NAT.</details>
<details><summary>89. 🔴 Как обновить кластер K8s?</summary>Проверить deprecated API, бэкап etcd, control plane → ноды по одной минорной версии, drain с PDB, проверить аддоны.</details>
<details><summary>90. 🔴 Как бэкапить K8s?</summary>etcd snapshot (control plane) + Velero (ресурсы + PV снапшоты) + GitOps-репо как источник манифестов.</details>

## 🔁 CI/CD (91–102)

<details><summary>91. 🟢 CI vs CD?</summary>CI — автосборка и тесты каждого изменения; Delivery — готовность к релизу по кнопке; Deployment — автоматически в прод.</details>
<details><summary>92. 🟢 Стадии пайплайна?</summary>lint → test → build → scan → push → deploy → e2e/smoke.</details>
<details><summary>93. 🟡 Build once, deploy many?</summary>Один неизменяемый артефакт (по digest) продвигается по всем окружениям; конфиг — снаружи.</details>
<details><summary>94. 🟢 Blue-green vs canary?</summary>BG — переключение всего трафика между средами; canary — постепенный % трафика с анализом метрик.</details>
<details><summary>95. 🟡 Как ускорить пайплайн?</summary>Кэш, параллелизм, тесты только изменённого, собственные runner'ы, BuildKit кэш, меньшие образы.</details>
<details><summary>96. 🟡 Что такое GitOps?</summary>Желаемое состояние в Git, агент в кластере тянет и сверяет (Argo CD, Flux), drift исправляется автоматически.</details>
<details><summary>97. 🟡 Push vs pull деплой?</summary>Push — CI ходит в кластер (нужны креды в CI); pull — кластер тянет из Git (безопаснее, видит drift).</details>
<details><summary>98. 🟡 Как хранить секреты в CI?</summary>Masked/protected vars, OIDC к облаку, Vault, никогда в репо и логах.</details>
<details><summary>99. 🟡 Миграции БД без даунтайма?</summary>Expand/contract: обратно-совместимая схема → новый код → удаление старого.</details>
<details><summary>100. 🟡 DORA-метрики?</summary>Deployment frequency, Lead time, Change failure rate, Time to restore.</details>
<details><summary>101. 🟡 Feature flags — зачем?</summary>Разделить деплой и релиз, быстро выключить фичу, A/B, canary для пользователей.</details>
<details><summary>102. 🔴 Как защитить CI/CD от supply-chain атак?</summary>Pin по SHA, минимальные права токенов, OIDC, изолированные runner'ы, подпись артефактов, SBOM, review изменений пайплайна.</details>

## 🏗 IaC (103–114)

<details><summary>103. 🟢 Зачем IaC?</summary>Воспроизводимость, версионирование, ревью, автоматизация, меньше ручных ошибок.</details>
<details><summary>104. 🟢 Что такое Terraform state?</summary>Соответствие кода реальным ресурсам + метаданные. Хранить удалённо с блокировкой и шифрованием.</details>
<details><summary>105. 🟡 Зачем state locking?</summary>Чтобы два apply не изменили инфраструктуру одновременно и не повредили state.</details>
<details><summary>106. 🟡 count vs for_each?</summary>count — по индексу, сдвиг индексов пересоздаёт ресурсы; for_each — по ключу, стабильнее.</details>
<details><summary>107. 🟡 Как импортировать ресурс?</summary>Блок `import { to = ..., id = ... }` + plan (или `terraform import`).</details>
<details><summary>108. 🟡 Как переименовать ресурс без пересоздания?</summary>Блок `moved { from = ..., to = ... }` или `terraform state mv`.</details>
<details><summary>109. 🟡 Что такое drift?</summary>Расхождение реальности и кода из-за ручных изменений. Выявлять регулярным plan.</details>
<details><summary>110. 🟡 Terraform vs OpenTofu?</summary>OpenTofu — open-source (MPL) форк после перехода Terraform на BSL; совместим, есть шифрование state.</details>
<details><summary>111. 🟡 Как организовать окружения?</summary>Отдельные стейты/каталоги (или Terragrunt), общие модули, разные креды и аккаунты.</details>
<details><summary>112. 🟢 Terraform vs Ansible?</summary>Terraform — провижининг, декларативный, со state; Ansible — конфигурация, процедурно-декларативный, без state.</details>
<details><summary>113. 🟢 Что такое идемпотентность?</summary>Повторное применение даёт тот же результат без лишних изменений.</details>
<details><summary>114. 🔴 Plan хочет пересоздать прод-БД — действия?</summary>Не применять; найти атрибут с forces replacement; moved/ignore_changes/исправить код; prevent_destroy.</details>

## ☁️ Облака (115–124)

<details><summary>115. 🟢 Region vs AZ?</summary>Регион — география; AZ — изолированный ДЦ в регионе.</details>
<details><summary>116. 🟢 Security Group vs NACL?</summary>SG — stateful, на инстанс, только allow; NACL — stateless, на подсеть, allow/deny.</details>
<details><summary>117. 🟢 Публичная vs приватная подсеть?</summary>Публичная — маршрут через Internet Gateway; приватная — исходящий через NAT.</details>
<details><summary>118. 🟡 Как дать приложению доступ к S3 без ключей?</summary>IAM-роль: instance profile / IRSA / EKS Pod Identity / workload identity.</details>
<details><summary>119. 🟡 RPO vs RTO?</summary>RPO — допустимая потеря данных; RTO — допустимое время восстановления.</details>
<details><summary>120. 🟡 Стратегии DR?</summary>Backup&Restore → Pilot Light → Warm Standby → Active/Active.</details>
<details><summary>121. 🟡 Как сократить расходы?</summary>Теги/видимость, rightsizing, spot, RI/SP, автовыключение dev, lifecycle хранилища, VPC endpoints вместо NAT, ARM.</details>
<details><summary>122. 🟢 Shared responsibility?</summary>Облако — безопасность инфраструктуры; клиент — IAM, данные, конфигурации, ОС.</details>
<details><summary>123. 🟡 Утёк облачный ключ — действия?</summary>Деактивировать/удалить ключ, ротировать, аудит (CloudTrail), удалить созданные злоумышленником ресурсы, разбор.</details>
<details><summary>124. 🔴 Отказоустойчивое веб-приложение в облаке?</summary>CDN+WAF, LB в 3 AZ, автоскейлинг compute, Multi-AZ БД с репликами, кэш, бэкапы в другой регион, IaC, мониторинг.</details>

## 📊 Observability (125–136)

<details><summary>125. 🟢 Метрики vs логи vs трейсы?</summary>Метрики — агрегаты во времени; логи — события; трейсы — путь запроса через сервисы.</details>
<details><summary>126. 🟢 Pull vs push мониторинг?</summary>Prometheus тянет /metrics; push — агент отправляет (Pushgateway, OTLP).</details>
<details><summary>127. 🟢 Типы метрик Prometheus?</summary>Counter, Gauge, Histogram, Summary.</details>
<details><summary>128. 🟡 Histogram vs Summary?</summary>Histogram агрегируется между инстансами (квантили на сервере); Summary — квантили на клиенте, не агрегируются.</details>
<details><summary>129. 🟡 Как посчитать p99?</summary>`histogram_quantile(0.99, sum by (le) (rate(x_bucket[5m])))`.</details>
<details><summary>130. 🟡 Что такое кардинальность?</summary>Число уникальных комбинаций лейблов = числу рядов. Высокая (user_id) убивает TSDB.</details>
<details><summary>131. 🟡 rate vs irate vs increase?</summary>rate — средняя скорость за окно; irate — по последним 2 точкам; increase — прирост за окно.</details>
<details><summary>132. 🟡 HA и долгое хранение Prometheus?</summary>Две реплики + Thanos/Mimir/VictoriaMetrics с объектным хранилищем.</details>
<details><summary>133. 🟢 RED vs USE?</summary>RED — для сервисов (Rate, Errors, Duration); USE — для ресурсов (Utilization, Saturation, Errors).</details>
<details><summary>134. 🟡 Что такое хороший алерт?</summary>На симптом, actionable, с runbook, без шума, с `for:` и правильной severity.</details>
<details><summary>135. 🟡 Loki vs Elasticsearch?</summary>Loki индексирует только лейблы — дешевле, хранение в S3; ES — полнотекстовый индекс, мощный поиск, дороже.</details>
<details><summary>136. 🟡 Что такое OpenTelemetry?</summary>Вендор-нейтральный стандарт и SDK для метрик/логов/трейсов + Collector + протокол OTLP.</details>

## 🔐 Security (137–142)

<details><summary>137. 🟢 SAST vs DAST vs SCA?</summary>SAST — анализ кода; DAST — атака работающего приложения; SCA — уязвимости зависимостей.</details>
<details><summary>138. 🟡 Что такое SBOM?</summary>Перечень компонентов ПО (SPDX/CycloneDX) — для учёта и быстрого поиска уязвимостей.</details>
<details><summary>139. 🟡 Зачем подписывать образы?</summary>Гарантия происхождения и целостности; admission-контроль пускает только подписанные (cosign + Kyverno).</details>
<details><summary>140. 🟡 Как хранить секреты в K8s?</summary>ESO + Vault/облачный SM, Sealed Secrets, SOPS; шифрование etcd, RBAC.</details>
<details><summary>141. 🟡 Что такое zero trust?</summary>Нет доверия по сетевому периметру: каждая сущность аутентифицируется и авторизуется (mTLS, identity).</details>
<details><summary>142. 🟢 Least privilege?</summary>Минимально необходимые права и только на нужное время.</details>

## 🛡 SRE (143–150)

<details><summary>143. 🟢 SLI vs SLO vs SLA?</summary>SLI — метрика; SLO — внутренняя цель; SLA — договор с последствиями.</details>
<details><summary>144. 🟢 99.9% — сколько даунтайма в месяц?</summary>≈ 43 минуты.</details>
<details><summary>145. 🟡 Что такое error budget?</summary>1 − SLO; допустимая ненадёжность. Исчерпан — фриз фич, работа над надёжностью.</details>
<details><summary>146. 🟡 Что такое burn rate алерт?</summary>Алерт на скорость сжигания бюджета ошибок в нескольких окнах (1ч/5м, 6ч/30м) — меньше шума, ловит и быстрые, и медленные проблемы.</details>
<details><summary>147. 🟡 Первое действие при инциденте?</summary>Восстановить сервис (mitigate: откат, failover, скейл), коммуникация; root cause — потом.</details>
<details><summary>148. 🟡 Blameless postmortem?</summary>Разбор без поиска виноватых: таймлайн, причины, системные улучшения, action items с владельцами.</details>
<details><summary>149. 🟡 Зачем jitter в ретраях?</summary>Рассинхронизировать клиентов, избежать thundering herd/retry storm.</details>
<details><summary>150. 🔴 DevOps vs SRE vs Platform Engineering?</summary>DevOps — культура; SRE — инженерный подход к надёжности через SLO и error budget; Platform Eng — внутренний продукт-платформа с golden paths для разработчиков.</details>


---

<a id="roadmap"></a>

# 🗺️ Дорожная карта DevOps 2026

```
Linux + сети + Git
        │
        ▼
 Bash / Python ──► Docker ──► CI/CD (GitLab CI / GitHub Actions)
                                  │
                                  ▼
                       Kubernetes + Helm/Kustomize
                                  │
             ┌────────────────────┼────────────────────┐
             ▼                    ▼                    ▼
   Terraform/OpenTofu      Observability          GitOps (Argo CD)
   + Ansible + Облако      (Prometheus, Grafana,   + DevSecOps
                            Loki, OTel)
             └────────────────────┼────────────────────┘
                                  ▼
                 SRE (SLO, инциденты) + System Design
                                  ▼
                 Platform Engineering / FinOps / Лидерство
```

## Junior — «могу выполнить задачу»
- [ ] Linux: процессы, права, systemd, логи, сети на уровне `ss/curl/dig`
- [ ] Git: ветки, MR, конфликты
- [ ] Bash-скрипты с `set -euo pipefail`
- [ ] Docker: Dockerfile, compose
- [ ] CI: пайплайн сборки и тестов
- [ ] K8s: Pod, Deployment, Service, ConfigMap, `kubectl` отладка
- [ ] Одно облако: ВМ, сеть, IAM на базовом уровне
- [ ] Проект: задеплоить приложение с БД в K8s через CI

## Middle — «отвечаю за систему»
- [ ] K8s в проде: Ingress/Gateway, HPA, RBAC, NetworkPolicy, Helm, операторы
- [ ] Terraform: модули, remote state, окружения, импорт
- [ ] GitOps (Argo CD/Flux)
- [ ] Мониторинг и алертинг, логи, трейсы
- [ ] Секреты (Vault/ESO), сканирование образов
- [ ] Стратегии деплоя, миграции БД
- [ ] Инциденты и постмортемы
- [ ] Проект: инфраструктура с нуля под IaC + GitOps + observability

## Senior — «определяю, как строим»
- [ ] Архитектура: multi-AZ/region, DR, RPO/RTO
- [ ] SLO, error budget, on-call процессы
- [ ] Supply chain security, compliance
- [ ] FinOps, capacity planning
- [ ] Platform Engineering: IDP, golden paths, DX
- [ ] Менторство, RFC/ADR, влияние на команды

## Ресурсы
- Книги: *Site Reliability Engineering* (Google, бесплатно онлайн), *The Phoenix Project*, *Accelerate*, *Kubernetes in Action*, *Terraform: Up & Running*, *Systems Performance* (Brendan Gregg).
- Практика: [Killercoda](https://killercoda.com), [KodeKloud](https://kodekloud.com), [roadmap.sh/devops](https://roadmap.sh/devops), «Kubernetes the Hard Way».
- Документация: kubernetes.io, prometheus.io, developer.hashicorp.com/terraform, opentofu.org.


---

⭐ Поставь звезду, если помогло пройти собеседование! Лицензия: MIT

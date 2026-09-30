# komorebi

Персональный конфиг [komorebi](https://github.com/LGUG2Z/komorebi) — тайлинг-менеджера окон для Windows. Вместе с ним идут панель `komorebi-bar` и хоткеи [whkd](https://github.com/LGUG2Z/whkd).

## Состав

| Файл | Назначение |
| --- | --- |
| `komorebi.json` | Основной конфиг оконного менеджера |
| `komorebi.bar.json` | Панель: воркспейсы, раскладка, дата, время, батарея |
| `applications.json` | Правила для конкретных приложений (игнор, float, tray) |
| `.config/whkdrc` | Горячие клавиши |

## Что настроено

- Семь воркспейсов с разными раскладками: BSP, вертикальный и горизонтальный стек, ultrawide, rows, grid, right-main.
- Цветная рамка окна: фиолетовая для одиночного окна, зелёная для стека, розовая для monocle, жёлтая для floating.
- Курсор следует за фокусом.
- Панель на шрифте JetBrains Mono, тема Base16 Ashes.

## Установка

Нужны [komorebi](https://github.com/LGUG2Z/komorebi) и [whkd](https://github.com/LGUG2Z/whkd). Через Scoop:

```powershell
scoop bucket add extras
scoop install komorebi whkd
```

Клонируйте репозиторий и разложите файлы так, как их ищет komorebi:

```powershell
git clone https://github.com/DmNep/komorebi.git $HOME\komorebi-config

Copy-Item $HOME\komorebi-config\komorebi.json $HOME\komorebi.json
Copy-Item $HOME\komorebi-config\komorebi.bar.json $HOME\komorebi.bar.json
Copy-Item $HOME\komorebi-config\applications.json $HOME\applications.json
New-Item -ItemType Directory -Force $HOME\.config | Out-Null
Copy-Item $HOME\komorebi-config\.config\whkdrc $HOME\.config\whkdrc
```

Либо укажите каталог конфигов через переменную окружения и держите `komorebi.json` / `komorebi.bar.json` там:

```powershell
[System.Environment]::SetEnvironmentVariable("KOMOREBI_CONFIG_HOME", "$HOME\komorebi-config", "User")
```

`applications.json` в этом конфиге читается из `$Env:USERPROFILE\applications.json`. `whkd` по умолчанию берёт `$HOME\.config\whkdrc`.

Запуск:

```powershell
komorebic start --whkd --bar
```

Перезагрузка конфига: `Alt + Shift + O`. Перезапуск whkd: `Alt + O`.

## Воркспейсы

| Клавиша | Имя | Раскладка |
| --- | --- | --- |
| `Alt + 1` | I | BSP |
| `Alt + 2` | II | Vertical Stack |
| `Alt + 3` | III | Horizontal Stack |
| `Alt + 4` | IV | Ultrawide Vertical Stack |
| `Alt + 5` | V | Rows |
| `Alt + 6` | VI | Grid |
| `Alt + 7` | VII | Right Main Vertical Stack |

`Alt + Shift + N` переносит текущее окно на воркспейс `N`.

## Горячие клавиши

Модификатор — `Alt`. Vim-навигация: `H` `J` `K` `L`.

### Фокус и перемещение

| Клавиша | Действие |
| --- | --- |
| `Alt + H/J/K/L` | Фокус влево / вниз / вверх / вправо |
| `Alt + Shift + H/J/K/L` | Переместить окно |
| `Alt + Shift + [` / `]` | Цикл фокуса назад / вперёд |
| `Alt + Shift + Enter` | Promote — сделать окно главным |

### Стек

| Клавиша | Действие |
| --- | --- |
| `Alt + ←/↓/↑/→` | Сложить окно в сторону |
| `Alt + ;` | Достать из стека |
| `Alt + [` / `]` | Цикл окон в стеке |

### Размер и раскладка

| Клавиша | Действие |
| --- | --- |
| `Alt + +` / `-` | Ширина ± |
| `Alt + Shift + +` / `-` | Высота ± |
| `Alt + X` / `Y` | Зеркалировать раскладку по горизонтали / вертикали |
| `Alt + T` | Переключить floating |
| `Alt + Shift + F` | Monocle |
| `Alt + Shift + R` | Пересобрать тайлинг |
| `Alt + P` | Пауза менеджера |

### Окна и конфиг

| Клавиша | Действие |
| --- | --- |
| `Alt + Q` | Закрыть окно |
| `Alt + M` | Свернуть |
| `Alt + I` | Показать / скрыть подсказки по хоткеям |
| `Alt + O` | Перезапустить whkd |
| `Alt + Shift + O` | Перезагрузить конфиг komorebi |

## Лицензия

Собственные файлы этого репозитория — `README.md` и `komorebi.json` — распространяются по лицензии MIT, © 2026 Дмитрий Непобедимый / DmNep. `komorebi.json` основан на `docs/komorebi.example.json` из [LGUG2Z/komorebi](https://github.com/LGUG2Z/komorebi): под MIT отдаются только настройки из этого репозитория, сам пример остаётся под Komorebi License 2.0.0.

Чужой код не перелицензируется. `.config/whkdrc` и `komorebi.bar.json` совпадают с примерами komorebi v0.1.40 (`docs/whkdrc.sample`, `docs/komorebi.bar.example.json`) и остаются под [Komorebi License 2.0.0](https://github.com/LGUG2Z/komorebi/blob/master/LICENSE.md). `applications.json` — снимок [`applications.json`](https://github.com/LGUG2Z/komorebi-application-specific-configuration) и остаётся под MIT © 2024 Jade Iqbal.

Лицензия собственных файлов: [MIT](LICENSE) © 2026 Дмитрий Непобедимый / DmNep.

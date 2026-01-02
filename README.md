<p align="center">
  <img src="https://raw.githubusercontent.com/nickmilo/obsidian-blast/main/assets/blast-logo.svg" alt="BlastLibs Logo" width="120"/>
</p>

<h1 align="center">🚀 BlastLibs</h1>

<p align="center">
  <strong>Полная коллекция библиотек для MoonLoader SA-MP Lua разработки</strong>
  <br>
  <em>Специально оптимизировано для использования с Context7 AI</em>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/MoonLoader-v0.26+-blue?style=for-the-badge&logo=lua&logoColor=white" alt="MoonLoader"/>
  <img src="https://img.shields.io/badge/SA--MP-0.3.7-orange?style=for-the-badge" alt="SA-MP"/>
  <img src="https://img.shields.io/badge/Lua-5.1+-purple?style=for-the-badge&logo=lua&logoColor=white" alt="Lua"/>
  <img src="https://img.shields.io/badge/Context7-Ready-green?style=for-the-badge" alt="Context7"/>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Libraries-14-brightgreen?style=flat-square" alt="Libraries"/>
  <img src="https://img.shields.io/badge/Documentation-LLMS_Format-blueviolet?style=flat-square" alt="Docs"/>
  <img src="https://img.shields.io/badge/License-MIT-yellow?style=flat-square" alt="License"/>
</p>

---

## 📖 О проекте

**BlastLibs** — это тщательно подобранная коллекция всех основных библиотек для разработки Lua-скриптов под MoonLoader для GTA San Andreas Multiplayer. Каждая библиотека сопровождается документацией в формате LLMS.txt, что делает проект идеальным для использования с AI-ассистентами, такими как **Context7**.

### ✨ Особенности

- 🎯 **14 ключевых библиотек** — всё необходимое для SA-MP разработки
- 📚 **LLMS.txt документация** — оптимизировано для AI-ассистентов
- 🔄 **Context7 Ready** — мгновенная интеграция с Context7
- 🎨 **UI/UX библиотеки** — ImGui, mimgui, анимации, blur-эффекты
- 🌐 **Сетевые инструменты** — RakNet, пакеты, BitStream
- ⚙️ **Низкоуровневый доступ** — память, структуры, FFI

---

## 📦 Структура библиотек

### 🎮 Ядро SA-MP

| Библиотека | Описание | Документация |
|------------|----------|--------------|
| **[samp.lua](./samp.lua)** | Событийная обработка RPC и пакетов синхронизации | `sampluallms.txt` |
| **[RakLua](./RakLua)** | Работа с RakNet и BitStream без SAMPFUNCS | `rakluallms.txt` |
| **[SAMemory](./SAMemory)** | Доступ к памяти через C-структуры | `samemoryllms.txt` |

### 🖥️ Графический интерфейс

| Библиотека | Описание | Документация |
|------------|----------|--------------|
| **[imgui](./imgui)** | Dear ImGui для MoonLoader | `imguillms.txt` |
| **[mimgui](./mimgui)** | Современная версия ImGui (v1.72 + FFI) | `mimguillms.txt` |
| **[mimguiblur](./mimguiblur)** | Blur-эффекты для mimgui окон | `mimguiblurllms.txt` |
| **[moonimguiaddons](./moonimguiaddons)** | Анимированные виджеты и утилиты | `moonimguiaddonsllms.txt` |
| **[tabler-icons](./tabler-icons)** | 5000+ иконок Tabler для mimgui | `tablericonsllms.txt` |
| **[moonmonet](./moonmonet)** | Material You цветовые палитры | `moonmonetllms.txt` |

### 🌐 Сеть и боты

| Библиотека | Описание | Документация |
|------------|----------|--------------|
| **[SNET](./SNET)** | UDP сеть с TCP-подобной надёжностью | `snetllms.txt` |
| **[moonbot](./moonbot)** | Создание игровых ботов | `moonllms.txt` |

### 🎰 Arizona RP

| Библиотека | Описание | Документация |
|------------|----------|--------------|
| **[arizona-events](./arizona%20events)** | Обработка кастомных пакетов Arizona | `arizonaeventllms.txt` |
| **[arizona-api](./arizona-api)** | API для Arizona Trilogy (TrilogyLoader) | `arizonallms.txt` |

### 🔧 Дополнительно

| Библиотека | Описание | Документация |
|------------|----------|--------------|
| **[moonadditions](./moonadditions)** | Рендеринг, текстуры, кости, компоненты | `moonadditionsllms.txt` |

---

## 🚀 Быстрый старт

### Использование с Context7

1. **Добавьте BlastLibs в Context7:**
   ```
   Укажите путь к BlastLibs в настройках Context7
   ```

2. **Запросите нужную библиотеку:**
   ```
   Используй документацию mimgui для создания окна настроек
   ```

3. **AI автоматически использует актуальную документацию!**

### Ручная установка

1. Скопируйте нужные библиотеки в папку `moonloader/lib/`
2. Подключите в своём скрипте:

```lua
-- Пример: создание GUI с mimgui
local imgui = require 'mimgui'
local encoding = require 'encoding'
encoding.default = 'CP1251'
local u8 = encoding.UTF8

local window = imgui.new.bool(false)

imgui.OnFrame(function() return window[0] end, function()
    imgui.Begin(u8'Моё окно', window)
    imgui.Text(u8'Привет, мир!')
    imgui.End()
end)

function main()
    wait(-1)
end
```

---

## 📚 Примеры использования

### 🎨 UI с Material You темой

```lua
local imgui = require 'mimgui'
local MoonMonet = require 'MoonMonet'
local addons = require 'ADDONS'

-- Генерация палитры из основного цвета
local palette = MoonMonet.buildColors(0xFF6750A4, 1.0, true)

-- Применение к ImGui
imgui.OnInitialize(function()
    local style = imgui.GetStyle()
    -- Используйте ColorAccentsAdapter для конвертации
end)
```

### 🌐 Перехват сетевых пакетов

```lua
local sampev = require 'lib.samp.events'

-- Модификация исходящего чата
function sampev.onSendChat(msg)
    return {'[MyTag] ' .. msg}  -- Добавляем префикс
end

-- Блокировка входящих сообщений
function sampev.onServerMessage(color, text)
    if text:find('реклама') then
        return false  -- Блокируем спам
    end
end
```

### 🤖 Создание бота

```lua
local mb = require 'MoonBot'

function main()
    local bot = mb.add('TestBot')
    bot:connect()  -- Подключение к текущему серверу
    
    wait(3000)
    bot:sendChat('Привет от бота!')
end

function onBotRPC(bot, rpcId, bs)
    print(string.format('Bot %s: RPC %d', bot.name, rpcId))
end
```

### 🔮 Blur-эффект для окон

```lua
local imgui = require 'mimgui'
local blur = require 'mimgui_blur'

imgui.OnFrame(function() return true end, function()
    imgui.Begin('Glass Window')
    
    -- Размытие фона окна
    blur.apply(imgui.GetWindowDrawList(), 5.0)
    
    imgui.Text('Контент поверх blur-эффекта')
    imgui.End()
end)
```

---

## 📖 Формат документации LLMS.txt

Каждая библиотека содержит файл `*llms.txt` с документацией в специальном формате:

```markdown
# Library Name
Краткое описание библиотеки

## Dependencies
```lua
local lib = require 'library'
```

## Boilerplate
Минимальный рабочий пример

## Data Types
Описание типов данных

## Syntax & Patterns
Примеры синтаксиса и паттернов

## Best Practices
Рекомендации по использованию
```

Этот формат оптимизирован для:
- 🤖 **AI-ассистентов** — структурированная информация
- 📖 **Быстрого старта** — boilerplate готов к использованию
- 🎯 **Точных ответов** — примеры для каждого случая

---

## 🗂️ Структура проекта

```
BlastLibs/
├── 📁 RakLua/              # RakNet без SAMPFUNCS
│   ├── rakluallms.txt
│   └── src/
├── 📁 SAMemory/            # Память и структуры GTA
│   ├── samemoryllms.txt
│   └── src/
├── 📁 SNET/                # UDP сеть
│   └── snetllms.txt
├── 📁 arizona events/      # Arizona RP пакеты
│   ├── arizonaeventllms.txt
│   └── arizona-events/
├── 📁 arizona-api/         # Arizona Trilogy API
│   └── arizonallms.txt
├── 📁 imgui/               # Classic ImGui
│   ├── imguillms.txt
│   ├── docs/
│   └── examples/
├── 📁 mimgui/              # Modern ImGui
│   ├── mimguillms.txt
│   ├── examples/
│   └── lua/
├── 📁 mimguiblur/          # Blur эффекты
│   └── mimguiblurllms.txt
├── 📁 moonadditions/       # Графика и рендеринг
│   ├── moonadditionsllms.txt
│   └── examples/
├── 📁 moonbot/             # Игровые боты
│   └── moonllms.txt
├── 📁 moonimguiaddons/     # UI виджеты
│   ├── moonimguiaddonsllms.txt
│   └── src/
├── 📁 moonmonet/           # Material You палитры
│   ├── moonmonetllms.txt
│   └── src/
├── 📁 samp.lua/            # События SA-MP
│   ├── sampluallms.txt
│   └── samplua/
└── 📁 tabler-icons/        # Иконки
    ├── tablericonsllms.txt
    └── src/
```

---

## 🛠️ Совместимость

| Компонент | Версия |
|-----------|--------|
| **MoonLoader** | 0.26+ |
| **SA-MP** | 0.3.7 R1-R5 |
| **LuaJIT** | 2.0+ |
| **GTA:SA** | 1.0 US |

### Поддерживаемые серверы
- ✅ Стандартные SA-MP серверы
- ✅ Arizona RP
- ✅ Другие RP проекты

---

## 🤝 Вклад в проект

Мы приветствуем вклад в развитие BlastLibs!

1. 🍴 Fork репозитория
2. 🔧 Внесите изменения
3. 📝 Обновите документацию (LLMS.txt)
4. 🚀 Создайте Pull Request

### Добавление новой библиотеки

1. Создайте папку с именем библиотеки
2. Добавьте файл `{name}llms.txt` с документацией
3. Следуйте формату существующих LLMS файлов

---

## 📜 Лицензия

Каждая библиотека сохраняет свою оригинальную лицензию. BlastLibs как коллекция распространяется под лицензией **MIT**.

---

## 🙏 Благодарности

<table>
  <tr>
    <td align="center"><strong>MoonLoader Team</strong><br/>За невероятный загрузчик</td>
    <td align="center"><strong>FYP</strong><br/>За samp.lua и mimgui</td>
    <td align="center"><strong>JEDT</strong><br/>За Arizona Events</td>
  </tr>
  <tr>
    <td align="center"><strong>Сообщество</strong><br/>За все библиотеки</td>
    <td align="center"><strong>Context7</strong><br/>За AI-интеграцию</td>
    <td align="center"><strong>Dear ImGui</strong><br/>За UI framework</td>
  </tr>
</table>

---

<p align="center">
  <strong>⭐ Поставьте звезду, если проект полезен! ⭐</strong>
</p>

<p align="center">
  <sub>Made with ❤️ for SA-MP Lua Community</sub>
</p>


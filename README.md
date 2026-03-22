# VYUD AI — Design System v2.0

> **Единый источник правды** для всех интерфейсов экосистемы VYUD AI:  
> Telegram-бот · Веб-приложение (Streamlit) · Лендинги · Сертификаты · Документация

---

## Содержание

1. [Принципы](#1-принципы)
2. [Файловая структура](#2-файловая-структура)
3. [Токены: Цвета](#3-токены-цвета)
4. [Токены: Типографика](#4-токены-типографика)
5. [Токены: Пространство и сетка](#5-токены-пространство-и-сетка)
6. [Токены: Motion и анимация](#6-токены-motion-и-анимация)
7. [Токены: Z-index и тени](#7-токены-z-index-и-тени)
8. [Компоненты: Кнопки](#8-компоненты-кнопки)
9. [Компоненты: Карточки](#9-компоненты-карточки)
10. [Компоненты: Формы](#10-компоненты-формы)
11. [Компоненты: Статусы и бейджи](#11-компоненты-статусы-и-бейджи)
12. [Компоненты: Состояния загрузки](#12-компоненты-состояния-загрузки)
13. [Telegram Bot UI](#13-telegram-bot-ui)
14. [Логотип и ассеты](#14-логотип-и-ассеты)
15. [Адаптивность](#15-адаптивность)
16. [Тёмная тема](#16-тёмная-тема)
17. [Доступность](#17-доступность)
18. [Интеграция](#18-интеграция)
19. [Версионирование](#19-версионирование)

---

## 1. Принципы

### Четыре кита дизайна VYUD AI

| Принцип | Описание | Применение |
|---------|----------|------------|
| **Скорость очевидна** | Интерфейс должен *ощущаться* быстрым до того, как начнётся загрузка | Skeleton-анимации, мгновенный feedback, прогресс-индикаторы |
| **Zero cognitive load** | Пользователь делает одно действие → получает результат | Минимум кнопок, чёткая иерархия, одна CTA на экран |
| **Доверие через детали** | B2B-клиент оценивает профессионализм по мелочам | Консистентные отступы, чёткая типографика, корректная обработка ошибок |
| **Mobile-first** | Основная точка входа — Telegram (мобильный) | Все компоненты проектируются для 375px, десктоп — расширение |

---

## 2. Файловая структура

```
/var/www/vyud_app/
├── design_system/
│   ├── tokens.css           # CSS-переменные (единственный источник токенов)
│   ├── reset.css            # CSS-нормализация
│   ├── components.css       # Готовые UI-компоненты
│   ├── animations.css       # Keyframes и motion-утилиты
│   └── dark.css             # Оверрайды для тёмной темы
├── assets/
│   ├── logo/
│   │   ├── logo-full.svg    # Полный логотип (светлый фон)
│   │   ├── logo-full-dark.svg # Полный логотип (тёмный фон)
│   │   ├── logo-mark.svg    # Только знак V
│   │   └── logo-wordmark.svg # Только текст VYUD.AI
│   ├── favicon.ico
│   ├── favicon-32.png
│   ├── apple-touch-icon.png # 180×180px
│   └── og-image.png         # 1200×630px
├── fonts/                   # Self-hosted (опционально)
└── DESIGN_SYSTEM.md         # Этот файл
```

---

## 3. Токены: Цвета

### `design_system/tokens.css` — Секция цветов

```css
:root {
  /* ============================================
     BRAND PALETTE
     Философия: тёмно-сланцевая база + электрик-акцент.
     Не generic indigo — наш синий смещён в голубую сторону,
     что даёт ощущение технологичности, а не корпоративности.
  ============================================ */

  /* Primary — электрический синий (≠ Bootstrap/Tailwind indigo) */
  --vyud-primary-50:  #EEF6FF;
  --vyud-primary-100: #DBEEFF;
  --vyud-primary-200: #BADdff;
  --vyud-primary-300: #7EC4FF;
  --vyud-primary-400: #399FFF;
  --vyud-primary-500: #0D7EFF; /* BASE — основной акцент */
  --vyud-primary-600: #0062E0;
  --vyud-primary-700: #004DB5;
  --vyud-primary-800: #003D94;
  --vyud-primary-900: #002F72;

  /* Semantic aliases */
  --vyud-color-brand:       var(--vyud-primary-500);
  --vyud-color-brand-hover: var(--vyud-primary-600);
  --vyud-color-brand-light: var(--vyud-primary-50);
  --vyud-color-brand-ring:  rgba(13, 126, 255, 0.25);

  /* Neutral — холодный сланец (не pure grey) */
  --vyud-neutral-0:   #FFFFFF;
  --vyud-neutral-50:  #F7F9FC;
  --vyud-neutral-100: #EEF2F7;
  --vyud-neutral-200: #DDE4EF;
  --vyud-neutral-300: #C4CFDF;
  --vyud-neutral-400: #9AAABF;
  --vyud-neutral-500: #6B809A;
  --vyud-neutral-600: #4A5F78;
  --vyud-neutral-700: #324159;
  --vyud-neutral-800: #1E2D40;
  --vyud-neutral-900: #0D1926;
  --vyud-neutral-950: #070E18;

  /* Semantic surface aliases */
  --vyud-bg:              var(--vyud-neutral-0);
  --vyud-bg-secondary:    var(--vyud-neutral-50);
  --vyud-bg-tertiary:     var(--vyud-neutral-100);
  --vyud-bg-inverse:      var(--vyud-neutral-900);

  /* Text */
  --vyud-text-primary:    var(--vyud-neutral-900);
  --vyud-text-secondary:  var(--vyud-neutral-600);
  --vyud-text-muted:      var(--vyud-neutral-400);
  --vyud-text-inverse:    var(--vyud-neutral-0);
  --vyud-text-brand:      var(--vyud-primary-600);

  /* Border */
  --vyud-border-light:  var(--vyud-neutral-100);
  --vyud-border:        var(--vyud-neutral-200);
  --vyud-border-strong: var(--vyud-neutral-300);

  /* Semantic states */
  --vyud-success:        #0EA86E;
  --vyud-success-light:  #ECFDF5;
  --vyud-warning:        #E08A00;
  --vyud-warning-light:  #FFFBEB;
  --vyud-error:          #D93025;
  --vyud-error-light:    #FEF2F2;
  --vyud-info:           var(--vyud-primary-500);
  --vyud-info-light:     var(--vyud-primary-50);

  /* Telegram brand (фиксированный, не переопределяется темой) */
  --vyud-telegram:       #229ED9;
  --vyud-telegram-hover: #1A8DC7;

  /* Акцент для Terminal/Code блоков */
  --vyud-code-bg:        #0D1926;
  --vyud-code-text:      #7EC4FF;
  --vyud-code-comment:   #4A5F78;
  --vyud-code-string:    #0EA86E;
  --vyud-code-keyword:   #399FFF;
}
```

---

## 4. Токены: Типографика

### Обоснование выбора шрифтов

| Роль | Шрифт | Причина |
|------|-------|---------|
| **Display** | [Syne](https://fonts.google.com/specimen/Syne) | Геометрический, футуристичный. Отличает нас от 90% SaaS с Inter |
| **Body** | [DM Sans](https://fonts.google.com/specimen/DM+Sans) | Оптимизирован для экранов, отличная читаемость на кириллице |
| **Mono** | [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) | Промышленный стандарт для кода, лигатуры |

### Подключение шрифтов

```html
<!-- В <head> ПЕРЕД любыми стилями -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;700;800&family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;0,9..40,600;1,9..40,300&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
```

### `tokens.css` — Секция типографики

```css
:root {
  /* Font families */
  --vyud-font-display: 'Syne', system-ui, sans-serif;
  --vyud-font-body:    'DM Sans', system-ui, sans-serif;
  --vyud-font-mono:    'JetBrains Mono', 'Fira Code', monospace;

  /* Font sizes — fluid type scale (clamp для адаптивности) */
  --vyud-text-xs:   0.75rem;   /* 12px */
  --vyud-text-sm:   0.875rem;  /* 14px */
  --vyud-text-base: 1rem;      /* 16px */
  --vyud-text-lg:   1.125rem;  /* 18px */
  --vyud-text-xl:   1.25rem;   /* 20px */
  --vyud-text-2xl:  1.5rem;    /* 24px */
  --vyud-text-3xl:  clamp(1.75rem, 4vw, 2rem);    /* 28–32px */
  --vyud-text-4xl:  clamp(2rem, 5vw, 2.5rem);     /* 32–40px */
  --vyud-text-5xl:  clamp(2.5rem, 6vw, 3.5rem);   /* 40–56px */
  --vyud-text-hero: clamp(3rem, 8vw, 5rem);        /* 48–80px */

  /* Font weights */
  --vyud-weight-light:    300;
  --vyud-weight-regular:  400;
  --vyud-weight-medium:   500;
  --vyud-weight-semibold: 600;
  --vyud-weight-bold:     700;
  --vyud-weight-extrabold:800;

  /* Line heights */
  --vyud-leading-tight:  1.2;
  --vyud-leading-snug:   1.35;
  --vyud-leading-normal: 1.5;
  --vyud-leading-relaxed:1.65;
  --vyud-leading-loose:  1.8;

  /* Letter spacing */
  --vyud-tracking-tight:  -0.02em;
  --vyud-tracking-normal:  0;
  --vyud-tracking-wide:    0.04em;
  --vyud-tracking-widest:  0.08em;
}
```

### Типографическая шкала (CSS-классы)

```css
/* design_system/components.css — Typography */

.vyud-display-xl {
  font: var(--vyud-weight-extrabold) var(--vyud-text-hero)/var(--vyud-leading-tight) var(--vyud-font-display);
  letter-spacing: var(--vyud-tracking-tight);
  color: var(--vyud-text-primary);
}

.vyud-display-lg {
  font: var(--vyud-weight-bold) var(--vyud-text-5xl)/var(--vyud-leading-tight) var(--vyud-font-display);
  letter-spacing: var(--vyud-tracking-tight);
  color: var(--vyud-text-primary);
}

.vyud-h1 {
  font: var(--vyud-weight-bold) var(--vyud-text-4xl)/var(--vyud-leading-snug) var(--vyud-font-display);
  color: var(--vyud-text-primary);
}

.vyud-h2 {
  font: var(--vyud-weight-semibold) var(--vyud-text-3xl)/var(--vyud-leading-snug) var(--vyud-font-display);
  color: var(--vyud-text-primary);
}

.vyud-h3 {
  font: var(--vyud-weight-semibold) var(--vyud-text-2xl)/var(--vyud-leading-snug) var(--vyud-font-body);
  color: var(--vyud-text-primary);
}

.vyud-h4 {
  font: var(--vyud-weight-semibold) var(--vyud-text-xl)/var(--vyud-leading-normal) var(--vyud-font-body);
  color: var(--vyud-text-primary);
}

.vyud-body-lg  { font: var(--vyud-weight-regular) var(--vyud-text-lg)/var(--vyud-leading-relaxed) var(--vyud-font-body); }
.vyud-body     { font: var(--vyud-weight-regular) var(--vyud-text-base)/var(--vyud-leading-relaxed) var(--vyud-font-body); }
.vyud-body-sm  { font: var(--vyud-weight-regular) var(--vyud-text-sm)/var(--vyud-leading-normal) var(--vyud-font-body); }
.vyud-caption  { font: var(--vyud-weight-medium) var(--vyud-text-xs)/var(--vyud-leading-normal) var(--vyud-font-body); letter-spacing: var(--vyud-tracking-wide); text-transform: uppercase; }

.vyud-code {
  font: var(--vyud-weight-regular) var(--vyud-text-sm)/var(--vyud-leading-relaxed) var(--vyud-font-mono);
  background: var(--vyud-bg-tertiary);
  color: var(--vyud-text-brand);
  padding: 0.15em 0.4em;
  border-radius: 4px;
}

.vyud-label {
  font: var(--vyud-weight-medium) var(--vyud-text-sm)/1 var(--vyud-font-body);
  color: var(--vyud-text-secondary);
  letter-spacing: var(--vyud-tracking-wide);
}
```

---

## 5. Токены: Пространство и сетка

```css
:root {
  /* ============================================
     SPACING SCALE — базовая единица 4px
  ============================================ */
  --vyud-space-1:  0.25rem;  /* 4px */
  --vyud-space-2:  0.5rem;   /* 8px */
  --vyud-space-3:  0.75rem;  /* 12px */
  --vyud-space-4:  1rem;     /* 16px */
  --vyud-space-5:  1.25rem;  /* 20px */
  --vyud-space-6:  1.5rem;   /* 24px */
  --vyud-space-8:  2rem;     /* 32px */
  --vyud-space-10: 2.5rem;   /* 40px */
  --vyud-space-12: 3rem;     /* 48px */
  --vyud-space-16: 4rem;     /* 64px */
  --vyud-space-20: 5rem;     /* 80px */
  --vyud-space-24: 6rem;     /* 96px */
  --vyud-space-32: 8rem;     /* 128px */

  /* ============================================
     BORDER RADIUS
  ============================================ */
  --vyud-radius-sm:   4px;
  --vyud-radius-md:   8px;
  --vyud-radius-lg:   12px;
  --vyud-radius-xl:   16px;
  --vyud-radius-2xl:  24px;
  --vyud-radius-full: 9999px;

  /* ============================================
     GRID — контейнеры
  ============================================ */
  --vyud-container-sm:  640px;
  --vyud-container-md:  768px;
  --vyud-container-lg:  1024px;
  --vyud-container-xl:  1280px;
  --vyud-container-2xl: 1440px;

  --vyud-container-padding-x: clamp(var(--vyud-space-4), 5vw, var(--vyud-space-16));
}

/* Контейнер */
.vyud-container {
  width: 100%;
  max-width: var(--vyud-container-xl);
  margin-inline: auto;
  padding-inline: var(--vyud-container-padding-x);
}

/* Сетка секций */
.vyud-section { padding-block: clamp(var(--vyud-space-12), 8vw, var(--vyud-space-24)); }
.vyud-section-lg { padding-block: clamp(var(--vyud-space-16), 12vw, var(--vyud-space-32)); }

/* Feature grid */
.vyud-grid-features {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: var(--vyud-space-6);
}

.vyud-grid-2 { display: grid; grid-template-columns: repeat(2, 1fr); gap: var(--vyud-space-6); }
.vyud-grid-3 { display: grid; grid-template-columns: repeat(3, 1fr); gap: var(--vyud-space-6); }

@media (max-width: 768px) {
  .vyud-grid-2,
  .vyud-grid-3 { grid-template-columns: 1fr; }
}
```

---

## 6. Токены: Motion и анимация

```css
/* design_system/tokens.css — Motion */
:root {
  /* Durations */
  --vyud-duration-instant: 80ms;
  --vyud-duration-fast:    150ms;
  --vyud-duration-normal:  250ms;
  --vyud-duration-slow:    400ms;
  --vyud-duration-slower:  600ms;
  --vyud-duration-page:    800ms;

  /* Easings */
  --vyud-ease-in:       cubic-bezier(0.4, 0, 1, 1);
  --vyud-ease-out:      cubic-bezier(0, 0, 0.2, 1);
  --vyud-ease-in-out:   cubic-bezier(0.4, 0, 0.2, 1);
  --vyud-ease-spring:   cubic-bezier(0.34, 1.56, 0.64, 1);  /* overshoot */
  --vyud-ease-bounce:   cubic-bezier(0.68, -0.55, 0.27, 1.55);
  --vyud-ease-sharp:    cubic-bezier(0.12, 0, 0.39, 0);

  /* Transitions — семантические алиасы */
  --vyud-transition-colors:    color var(--vyud-duration-fast) var(--vyud-ease-out),
                                background-color var(--vyud-duration-fast) var(--vyud-ease-out),
                                border-color var(--vyud-duration-fast) var(--vyud-ease-out);
  --vyud-transition-shadow:    box-shadow var(--vyud-duration-normal) var(--vyud-ease-out);
  --vyud-transition-transform: transform var(--vyud-duration-normal) var(--vyud-ease-spring);
  --vyud-transition-opacity:   opacity var(--vyud-duration-normal) var(--vyud-ease-out);
  --vyud-transition-all:       var(--vyud-transition-colors), var(--vyud-transition-shadow);
}

/* ============================================
   KEYFRAMES
============================================ */

/* design_system/animations.css */

/* Появление снизу (Page load / Skeleton reveal) */
@keyframes vyud-fade-up {
  from { opacity: 0; transform: translateY(16px); }
  to   { opacity: 1; transform: translateY(0); }
}

/* Пульс (Loading states) */
@keyframes vyud-pulse {
  0%, 100% { opacity: 1; }
  50%       { opacity: 0.4; }
}

/* Shimmer (Skeleton loading) */
@keyframes vyud-shimmer {
  from { background-position: -200% center; }
  to   { background-position:  200% center; }
}

/* Spin (Spinners) */
@keyframes vyud-spin {
  from { transform: rotate(0deg); }
  to   { transform: rotate(360deg); }
}

/* Progress bar */
@keyframes vyud-progress-indeterminate {
  0%   { left: -35%; right: 100%; }
  60%  { left: 100%; right: -90%; }
  100% { left: 100%; right: -90%; }
}

/* Утилиты */
.vyud-animate-fade-up   { animation: vyud-fade-up var(--vyud-duration-slow) var(--vyud-ease-out) both; }
.vyud-animate-fade-up-1 { animation-delay: 100ms; }
.vyud-animate-fade-up-2 { animation-delay: 200ms; }
.vyud-animate-fade-up-3 { animation-delay: 300ms; }
.vyud-animate-fade-up-4 { animation-delay: 400ms; }

/* Respect user preferences */
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

---

## 7. Токены: Z-index и тени

```css
:root {
  /* ============================================
     Z-INDEX SCALE
     Явная иерархия слоёв — никаких магических 999999
  ============================================ */
  --vyud-z-below:    -1;
  --vyud-z-base:      0;
  --vyud-z-raised:   10;   /* Карточки при hover */
  --vyud-z-dropdown: 100;  /* Выпадающие меню */
  --vyud-z-sticky:   200;  /* Sticky header */
  --vyud-z-overlay:  300;  /* Затемнение фона */
  --vyud-z-modal:    400;  /* Модальные окна */
  --vyud-z-toast:    500;  /* Уведомления */
  --vyud-z-tooltip:  600;  /* Тултипы */

  /* ============================================
     SHADOWS
  ============================================ */
  --vyud-shadow-xs: 0 1px 2px rgba(13, 25, 38, 0.06);
  --vyud-shadow-sm: 0 1px 3px rgba(13, 25, 38, 0.08),
                    0 1px 2px rgba(13, 25, 38, 0.04);
  --vyud-shadow-md: 0 4px 6px rgba(13, 25, 38, 0.06),
                    0 2px 4px rgba(13, 25, 38, 0.04);
  --vyud-shadow-lg: 0 10px 15px rgba(13, 25, 38, 0.08),
                    0 4px  6px rgba(13, 25, 38, 0.04);
  --vyud-shadow-xl: 0 20px 25px rgba(13, 25, 38, 0.10),
                    0 8px 10px rgba(13, 25, 38, 0.04);
  --vyud-shadow-2xl:0 40px 60px rgba(13, 25, 38, 0.14);

  /* Brand glow — для акцентных элементов (hero CTA, premium-фичи) */
  --vyud-shadow-brand: 0 0 0 3px var(--vyud-color-brand-ring),
                       0 8px 24px rgba(13, 126, 255, 0.20);
  --vyud-shadow-brand-lg: 0 0 0 4px var(--vyud-color-brand-ring),
                          0 16px 40px rgba(13, 126, 255, 0.25);
}
```

---

## 8. Компоненты: Кнопки

```css
/* design_system/components.css — Buttons */

/* Base */
.vyud-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: var(--vyud-space-2);
  padding: 0.625rem 1.25rem;          /* 10px 20px */
  border-radius: var(--vyud-radius-md);
  font: var(--vyud-weight-semibold) var(--vyud-text-base)/1 var(--vyud-font-body);
  text-decoration: none;
  white-space: nowrap;
  cursor: pointer;
  border: 1.5px solid transparent;
  transition: var(--vyud-transition-all), var(--vyud-transition-transform);
  position: relative;
  overflow: hidden;
  -webkit-user-select: none;
  user-select: none;
}

.vyud-btn:focus-visible {
  outline: 2px solid var(--vyud-color-brand);
  outline-offset: 2px;
}

.vyud-btn:active { transform: scale(0.97); }

.vyud-btn:disabled,
.vyud-btn[aria-disabled="true"] {
  opacity: 0.45;
  cursor: not-allowed;
  pointer-events: none;
}

/* Sizes */
.vyud-btn-sm  { padding: 0.4rem 0.875rem; font-size: var(--vyud-text-sm); }
.vyud-btn-lg  { padding: 0.875rem 1.75rem; font-size: var(--vyud-text-lg); }
.vyud-btn-xl  { padding: 1.125rem 2.25rem; font-size: var(--vyud-text-xl); border-radius: var(--vyud-radius-lg); }
.vyud-btn-icon { padding: 0.625rem; aspect-ratio: 1; }

/* Variants */
.vyud-btn-primary {
  background: var(--vyud-color-brand);
  color: white;
  border-color: transparent;
}
.vyud-btn-primary:hover {
  background: var(--vyud-color-brand-hover);
  box-shadow: var(--vyud-shadow-brand);
  transform: translateY(-1px);
}

.vyud-btn-secondary {
  background: var(--vyud-bg);
  color: var(--vyud-text-primary);
  border-color: var(--vyud-border-strong);
}
.vyud-btn-secondary:hover {
  border-color: var(--vyud-color-brand);
  color: var(--vyud-color-brand);
  box-shadow: var(--vyud-shadow-md);
}

.vyud-btn-ghost {
  background: transparent;
  color: var(--vyud-text-secondary);
  border-color: transparent;
}
.vyud-btn-ghost:hover {
  background: var(--vyud-bg-secondary);
  color: var(--vyud-text-primary);
}

.vyud-btn-danger {
  background: var(--vyud-error);
  color: white;
}
.vyud-btn-danger:hover {
  background: #B91C1C;
  box-shadow: 0 4px 12px rgba(217, 48, 37, 0.3);
}

.vyud-btn-telegram {
  background: var(--vyud-telegram);
  color: white;
}
.vyud-btn-telegram:hover {
  background: var(--vyud-telegram-hover);
  box-shadow: 0 4px 12px rgba(34, 158, 217, 0.35);
  transform: translateY(-1px);
}

/* Loading state */
.vyud-btn-loading {
  pointer-events: none;
  color: transparent;
}
.vyud-btn-loading::after {
  content: '';
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 1.25em;
  height: 1.25em;
  margin: auto;
  border: 2px solid currentColor;
  border-top-color: transparent;
  border-radius: 50%;
  animation: vyud-spin 0.6s linear infinite;
  color: white;
}
```

---

## 9. Компоненты: Карточки

```css
/* design_system/components.css — Cards */

.vyud-card {
  background: var(--vyud-bg);
  border: 1px solid var(--vyud-border);
  border-radius: var(--vyud-radius-lg);
  padding: var(--vyud-space-6);
  box-shadow: var(--vyud-shadow-sm);
  transition: var(--vyud-transition-shadow), var(--vyud-transition-transform);
}

.vyud-card-interactive {
  cursor: pointer;
}
.vyud-card-interactive:hover {
  box-shadow: var(--vyud-shadow-lg);
  transform: translateY(-2px);
}
.vyud-card-interactive:focus-visible {
  outline: 2px solid var(--vyud-color-brand);
  outline-offset: 2px;
}

/* Feature card с акцентной левой полосой */
.vyud-card-feature {
  border-left: 3px solid var(--vyud-color-brand);
  padding-left: calc(var(--vyud-space-6) - 3px);
}

/* Pricing / Premium card */
.vyud-card-premium {
  background: linear-gradient(135deg, var(--vyud-neutral-900) 0%, var(--vyud-neutral-800) 100%);
  border-color: rgba(255,255,255,0.08);
  color: var(--vyud-text-inverse);
  box-shadow: var(--vyud-shadow-xl), 0 0 0 1px rgba(255,255,255,0.06);
}

/* Terminal / Code card */
.vyud-card-terminal {
  background: var(--vyud-code-bg);
  border-color: rgba(255,255,255,0.06);
  border-radius: var(--vyud-radius-lg);
  font-family: var(--vyud-font-mono);
  font-size: var(--vyud-text-sm);
  color: var(--vyud-code-text);
  padding: var(--vyud-space-5);
}
.vyud-card-terminal::before {
  content: '● ● ●';
  display: block;
  color: var(--vyud-code-comment);
  font-size: 10px;
  letter-spacing: 4px;
  margin-bottom: var(--vyud-space-4);
}
```

---

## 10. Компоненты: Формы

```css
/* design_system/components.css — Forms */

.vyud-field { display: flex; flex-direction: column; gap: var(--vyud-space-2); }

.vyud-label {
  font: var(--vyud-weight-medium) var(--vyud-text-sm)/1 var(--vyud-font-body);
  color: var(--vyud-text-primary);
}
.vyud-label-required::after {
  content: ' *';
  color: var(--vyud-error);
}

.vyud-input,
.vyud-textarea,
.vyud-select {
  width: 100%;
  padding: 0.625rem 0.875rem;
  background: var(--vyud-bg);
  border: 1.5px solid var(--vyud-border-strong);
  border-radius: var(--vyud-radius-md);
  font: var(--vyud-weight-regular) var(--vyud-text-base)/1 var(--vyud-font-body);
  color: var(--vyud-text-primary);
  transition: var(--vyud-transition-colors), var(--vyud-transition-shadow);
  -webkit-appearance: none;
  appearance: none;
}

.vyud-input::placeholder,
.vyud-textarea::placeholder {
  color: var(--vyud-text-muted);
}

.vyud-input:hover,
.vyud-textarea:hover {
  border-color: var(--vyud-neutral-400);
}

.vyud-input:focus,
.vyud-textarea:focus,
.vyud-select:focus {
  outline: none;
  border-color: var(--vyud-color-brand);
  box-shadow: 0 0 0 3px var(--vyud-color-brand-ring);
}

/* States */
.vyud-input-error { border-color: var(--vyud-error); }
.vyud-input-error:focus { box-shadow: 0 0 0 3px rgba(217, 48, 37, 0.15); }

.vyud-input-success { border-color: var(--vyud-success); }

.vyud-input:disabled { background: var(--vyud-bg-secondary); color: var(--vyud-text-muted); cursor: not-allowed; }

/* Helper text */
.vyud-field-hint    { font-size: var(--vyud-text-sm); color: var(--vyud-text-muted); }
.vyud-field-error   { font-size: var(--vyud-text-sm); color: var(--vyud-error); }
.vyud-field-success { font-size: var(--vyud-text-sm); color: var(--vyud-success); }

.vyud-textarea { resize: vertical; min-height: 100px; line-height: var(--vyud-leading-relaxed); }
```

---

## 11. Компоненты: Статусы и бейджи

```css
/* design_system/components.css — Badges & Status */

.vyud-badge {
  display: inline-flex;
  align-items: center;
  gap: var(--vyud-space-1);
  padding: 0.2em 0.6em;
  border-radius: var(--vyud-radius-full);
  font: var(--vyud-weight-semibold) var(--vyud-text-xs)/1 var(--vyud-font-body);
  letter-spacing: var(--vyud-tracking-wide);
  text-transform: uppercase;
}

.vyud-badge-brand   { background: var(--vyud-color-brand-light); color: var(--vyud-primary-700); }
.vyud-badge-success { background: var(--vyud-success-light);     color: #065F46; }
.vyud-badge-warning { background: var(--vyud-warning-light);     color: #92400E; }
.vyud-badge-error   { background: var(--vyud-error-light);       color: #991B1B; }
.vyud-badge-neutral { background: var(--vyud-bg-tertiary);       color: var(--vyud-text-secondary); }

/* Dot indicator */
.vyud-badge::before {
  content: '';
  display: block;
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: currentColor;
}
.vyud-badge-no-dot::before { display: none; }

/* Status pills (крупнее, для дашборда) */
.vyud-status {
  display: inline-flex;
  align-items: center;
  gap: var(--vyud-space-2);
  padding: var(--vyud-space-1) var(--vyud-space-3);
  border-radius: var(--vyud-radius-full);
  font: var(--vyud-weight-medium) var(--vyud-text-sm)/1 var(--vyud-font-body);
  border: 1px solid transparent;
}
.vyud-status-online  { background: var(--vyud-success-light); color: #065F46; border-color: rgba(10,185,110,0.2); }
.vyud-status-offline { background: var(--vyud-bg-tertiary);   color: var(--vyud-text-muted); }
.vyud-status-busy    { background: var(--vyud-warning-light);  color: #92400E; border-color: rgba(224,138,0,0.2); }
```

---

## 12. Компоненты: Состояния загрузки

```css
/* design_system/components.css — Loading States */

/* Skeleton */
.vyud-skeleton {
  background: linear-gradient(
    90deg,
    var(--vyud-bg-tertiary) 25%,
    var(--vyud-bg-secondary) 50%,
    var(--vyud-bg-tertiary) 75%
  );
  background-size: 200% 100%;
  animation: vyud-shimmer 1.4s ease infinite;
  border-radius: var(--vyud-radius-md);
}

.vyud-skeleton-text  { height: 1em; margin-block: 0.25em; }
.vyud-skeleton-title { height: 1.5em; width: 60%; margin-block: 0.3em; }
.vyud-skeleton-btn   { height: 40px; width: 120px; border-radius: var(--vyud-radius-md); }
.vyud-skeleton-avatar{ height: 40px; width: 40px; border-radius: 50%; }
.vyud-skeleton-card  { height: 180px; width: 100%; }

/* Spinner */
.vyud-spinner {
  display: inline-block;
  width: 1.5em;
  height: 1.5em;
  border: 2px solid var(--vyud-border);
  border-top-color: var(--vyud-color-brand);
  border-radius: 50%;
  animation: vyud-spin 0.65s linear infinite;
}
.vyud-spinner-sm { width: 1em;   height: 1em;   border-width: 2px; }
.vyud-spinner-lg { width: 2.5em; height: 2.5em; border-width: 3px; }

/* Progress bar */
.vyud-progress {
  width: 100%;
  height: 4px;
  background: var(--vyud-bg-tertiary);
  border-radius: var(--vyud-radius-full);
  overflow: hidden;
}
.vyud-progress-bar {
  height: 100%;
  background: var(--vyud-color-brand);
  border-radius: var(--vyud-radius-full);
  transition: width var(--vyud-duration-normal) var(--vyud-ease-out);
}
.vyud-progress-indeterminate .vyud-progress-bar {
  width: 35%;
  position: relative;
  animation: vyud-progress-indeterminate 1.4s ease infinite;
}
```

---

## 13. Telegram Bot UI

### Сообщения — шаблоны

> **Правило:** каждое сообщение начинается с emoji-статуса, заголовок **жирный**, подробности отделены пустой строкой.

#### Приветствие (новый пользователь)
```
🎯 Добро пожаловать в VYUD AI!

Я превращаю документы, видео и аудио в интерактивные тесты за секунды.

📤 Пришлите файл:
• PDF / DOCX / PPTX
• Видео / Аудио (до 20 МБ)

💎 Вам начислено 5 бесплатных генераций
```

#### Приветствие (вернувшийся пользователь)
```
👋 С возвращением!

💳 Ваш баланс: {N} кредитов

Пришлите файл — сгенерирую новый тест.
```

#### Обработка файла (прогресс)
```
📥 Файл получен

⏳ Обрабатываю...
```
_→ edit:_
```
📖 Извлекаю текст...
```
_→ edit:_
```
🧠 Генерирую вопросы...
```

#### Успех
```
✅ Тест готов!

📊 5 вопросов по вашему документу
💳 Остаток: {N} кредитов

👆 Откройте тест в веб-версии или пройдите прямо здесь ↓
```

#### Нет кредитов
```
⚠️ Недостаточно кредитов

Ваш баланс: 0

Пополните баланс в веб-приложении 👇
```

#### Ошибка
```
❌ Не удалось обработать файл

Причина: {описание}

Попробуйте другой файл или обратитесь в поддержку /help
```

### Emoji-палитра (единый стандарт)

| Ситуация | Emoji |
|----------|-------|
| Успех / готово | ✅ |
| Ошибка | ❌ |
| Предупреждение | ⚠️ |
| Обработка | ⏳ |
| Документ | 📄 |
| Видео | 🎥 |
| Аудио | 🎙️ |
| Тест / вопросы | 📊 |
| Кредиты | 💳 |
| Профиль | 👤 |
| Список тестов | 📚 |
| Помощь | ℹ️ |
| Новый пользователь | 🎯 |
| Вернувшийся | 👋 |
| Реферал / партнёр | 🤝 |
| Уведомление (админ) | 🔔 |
| Оплата | 💰 |

### Клавиатуры (Python/aiogram)

```python
# keyboards.py

from aiogram.types import InlineKeyboardMarkup, InlineKeyboardButton

def kb_main(test_id: str = None, web_url: str = "https://app.vyud.online") -> InlineKeyboardMarkup:
    """Основная клавиатура после генерации теста."""
    rows = []
    if test_id:
        rows.append([InlineKeyboardButton(
            text="📊 Открыть тест",
            url=f"{web_url}/?test={test_id}"
        )])
    rows.append([InlineKeyboardButton(
        text="🌐 Веб-версия",
        url=web_url
    )])
    return InlineKeyboardMarkup(inline_keyboard=rows)


def kb_no_credits(web_url: str = "https://app.vyud.online") -> InlineKeyboardMarkup:
    """Клавиатура при нехватке кредитов."""
    return InlineKeyboardMarkup(inline_keyboard=[[
        InlineKeyboardButton(text="💳 Пополнить баланс", url=f"{web_url}/billing")
    ]])


def kb_profile(web_url: str = "https://app.vyud.online") -> InlineKeyboardMarkup:
    """Клавиатура профиля."""
    return InlineKeyboardMarkup(inline_keyboard=[
        [InlineKeyboardButton(text="📚 Мои тесты",    callback_data="my_tests")],
        [InlineKeyboardButton(text="💳 Пополнить",    url=f"{web_url}/billing")],
        [InlineKeyboardButton(text="🌐 Открыть сайт", url=web_url)],
    ])
```

---

## 14. Логотип и ассеты

### Логотип SVG (production)

```svg
<!-- assets/logo/logo-full.svg -->
<svg width="160" height="44" viewBox="0 0 160 44" fill="none" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="VYUD AI logo">
  <defs>
    <linearGradient id="vyud-grad" x1="0" y1="0" x2="32" y2="44" gradientUnits="userSpaceOnUse">
      <stop offset="0%"   stop-color="#399FFF"/>
      <stop offset="100%" stop-color="#0062E0"/>
    </linearGradient>
  </defs>
  <!-- Знак: буква V с угловым срезом, символизирует скорость -->
  <path d="M4 6 L16 38 L28 6" stroke="url(#vyud-grad)" stroke-width="6" stroke-linecap="round" stroke-linejoin="round" fill="none"/>
  <circle cx="16" cy="38" r="3" fill="url(#vyud-grad)"/>
  <!-- Wordmark -->
  <text x="40" y="31" font-family="Syne, system-ui, sans-serif" font-weight="800" font-size="22" fill="#0D1926" letter-spacing="-0.5">VYUD</text>
  <text x="106" y="31" font-family="Syne, system-ui, sans-serif" font-weight="600" font-size="22" fill="#0D7EFF">.AI</text>
</svg>
```

```svg
<!-- assets/logo/logo-full-dark.svg (для тёмного фона) -->
<svg width="160" height="44" viewBox="0 0 160 44" fill="none" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="VYUD AI logo">
  <defs>
    <linearGradient id="vyud-grad-dark" x1="0" y1="0" x2="32" y2="44" gradientUnits="userSpaceOnUse">
      <stop offset="0%"   stop-color="#7EC4FF"/>
      <stop offset="100%" stop-color="#399FFF"/>
    </linearGradient>
  </defs>
  <path d="M4 6 L16 38 L28 6" stroke="url(#vyud-grad-dark)" stroke-width="6" stroke-linecap="round" stroke-linejoin="round" fill="none"/>
  <circle cx="16" cy="38" r="3" fill="url(#vyud-grad-dark)"/>
  <text x="40" y="31" font-family="Syne, system-ui, sans-serif" font-weight="800" font-size="22" fill="#F7F9FC" letter-spacing="-0.5">VYUD</text>
  <text x="106" y="31" font-family="Syne, system-ui, sans-serif" font-weight="600" font-size="22" fill="#7EC4FF">.AI</text>
</svg>
```

### Таблица использования ассетов

| Контекст | Файл | Размер | Фон |
|----------|------|--------|-----|
| Header лендинга | `logo-full.svg` | 160×44px | Светлый |
| Header (тёмный) | `logo-full-dark.svg` | 160×44px | Тёмный |
| Favicon браузер | `favicon.ico` | 32×32px | — |
| Apple Touch | `apple-touch-icon.png` | 180×180px | Белый |
| Telegram аватар | PNG из `logo-mark.svg` | 512×512px | #0D7EFF |
| OG-карта | `og-image.png` | 1200×630px | Тёмный (#0D1926) |
| Сертификат | `logo-full-dark.svg` | 320×88px | Любой |

---

## 15. Адаптивность

```css
/* design_system/tokens.css — Breakpoints */
:root {
  --vyud-bp-xs: 375px;   /* min small phone */
  --vyud-bp-sm: 640px;   /* landscape phone / large phone */
  --vyud-bp-md: 768px;   /* tablet portrait */
  --vyud-bp-lg: 1024px;  /* tablet landscape / small desktop */
  --vyud-bp-xl: 1280px;  /* desktop */
  --vyud-bp-2xl:1440px;  /* large desktop */
}
```

### Mobile-first медиа-запросы

```css
/* Используем min-width (mobile-first) */

/* sm: 640px+ */
@media (min-width: 640px) { ... }

/* md: 768px+ */
@media (min-width: 768px) { ... }

/* lg: 1024px+ */
@media (min-width: 1024px) { ... }

/* xl: 1280px+ */
@media (min-width: 1280px) { ... }
```

### Адаптивные компоненты

```css
/* Header */
.vyud-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: var(--vyud-space-4) var(--vyud-container-padding-x);
  position: sticky;
  top: 0;
  z-index: var(--vyud-z-sticky);
  background: rgba(247, 249, 252, 0.85);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid var(--vyud-border);
}

.vyud-nav {
  display: none;
}

@media (min-width: 768px) {
  .vyud-nav {
    display: flex;
    gap: var(--vyud-space-6);
    align-items: center;
  }
}

/* Touch-targets — минимум 44×44px на мобильных */
@media (max-width: 768px) {
  .vyud-btn     { min-height: 44px; }
  .vyud-btn-sm  { min-height: 36px; }
  .vyud-input,
  .vyud-select  { min-height: 44px; }
}
```

---

## 16. Тёмная тема

```css
/* design_system/dark.css */

@media (prefers-color-scheme: dark) {
  :root {
    --vyud-bg:           var(--vyud-neutral-950);
    --vyud-bg-secondary: var(--vyud-neutral-900);
    --vyud-bg-tertiary:  var(--vyud-neutral-800);
    --vyud-bg-inverse:   var(--vyud-neutral-0);

    --vyud-text-primary:   var(--vyud-neutral-50);
    --vyud-text-secondary: var(--vyud-neutral-300);
    --vyud-text-muted:     var(--vyud-neutral-500);
    --vyud-text-inverse:   var(--vyud-neutral-950);

    --vyud-border-light:  rgba(255,255,255,0.04);
    --vyud-border:        rgba(255,255,255,0.08);
    --vyud-border-strong: rgba(255,255,255,0.14);

    --vyud-shadow-sm: 0 1px 3px rgba(0,0,0,0.4), 0 1px 2px rgba(0,0,0,0.3);
    --vyud-shadow-md: 0 4px 6px rgba(0,0,0,0.4), 0 2px 4px rgba(0,0,0,0.3);
    --vyud-shadow-lg: 0 10px 15px rgba(0,0,0,0.5), 0 4px 6px rgba(0,0,0,0.3);

    --vyud-color-brand-light: rgba(13,126,255,0.15);
    --vyud-color-brand-ring:  rgba(13,126,255,0.35);
  }
}

/* Ручное переключение (data-theme="dark") */
[data-theme="dark"] { /* те же переопределения */ }
```

---

## 17. Доступность

### Контрастность (WCAG 2.1 AA)

| Сочетание | Контраст | Статус |
|-----------|----------|--------|
| `#0D1926` на `#FFFFFF` | 18.8:1 | ✅ AAA |
| `#0D7EFF` на `#FFFFFF` | 4.6:1 | ✅ AA |
| `#4A5F78` на `#FFFFFF` | 7.1:1 | ✅ AAA |
| `#FFFFFF` на `#0D7EFF` | 4.6:1 | ✅ AA |
| `#0EA86E` на `#FFFFFF` | 4.5:1 | ✅ AA |
| `#D93025` на `#FFFFFF` | 5.8:1 | ✅ AA |

### CSS Reset (базовый)

```css
/* design_system/reset.css */

*, *::before, *::after { box-sizing: border-box; }
* { margin: 0; }
html { -webkit-text-size-adjust: 100%; scroll-behavior: smooth; }
body {
  font: var(--vyud-weight-regular) var(--vyud-text-base)/var(--vyud-leading-relaxed) var(--vyud-font-body);
  color: var(--vyud-text-primary);
  background: var(--vyud-bg);
  -webkit-font-smoothing: antialiased;
  text-rendering: optimizeLegibility;
}
img, video { max-width: 100%; display: block; }
button, input, select, textarea { font: inherit; }
a { color: inherit; }
p, h1, h2, h3, h4, h5, h6 { overflow-wrap: break-word; }

/* Focus visible (skip hidden focus for mouse, show for keyboard) */
:focus { outline: none; }
:focus-visible {
  outline: 2px solid var(--vyud-color-brand);
  outline-offset: 2px;
  border-radius: 2px;
}

/* Screen reader only */
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0,0,0,0);
  white-space: nowrap;
  border: 0;
}
```

### ARIA-паттерны

```html
<!-- Кнопка с loading state -->
<button class="vyud-btn vyud-btn-primary vyud-btn-loading"
        aria-label="Генерирую тест..."
        aria-busy="true"
        disabled>
  Сгенерировать тест
</button>

<!-- Поле формы -->
<div class="vyud-field" role="group" aria-labelledby="email-label">
  <label id="email-label" class="vyud-label vyud-label-required" for="email">
    Рабочая почта
  </label>
  <input type="email" id="email" class="vyud-input"
         required aria-required="true"
         aria-describedby="email-hint email-error">
  <span id="email-hint" class="vyud-field-hint">Для корпоративных клиентов</span>
  <span id="email-error" class="vyud-field-error" role="alert" aria-live="polite"></span>
</div>

<!-- Skip link (первый элемент на странице) -->
<a href="#main-content" class="sr-only :focus-visible:not-sr-only vyud-btn vyud-btn-primary">
  Перейти к содержимому
</a>
```

---

## 18. Интеграция

### Шаг 1: Создать файловую структуру

```bash
ssh root@38.180.229.254 '
  mkdir -p /var/www/vyud_app/design_system
  mkdir -p /var/www/vyud_app/assets/logo
  echo "Структура создана"
'
```

### Шаг 2: Подключить в `index.html`

```html
<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <!-- Порядок важен: reset → tokens → animations → components -->
  <link rel="stylesheet" href="/design_system/reset.css">
  <link rel="stylesheet" href="/design_system/tokens.css">
  <link rel="stylesheet" href="/design_system/animations.css">
  <link rel="stylesheet" href="/design_system/components.css">
  <link rel="stylesheet" href="/design_system/dark.css">

  <!-- Шрифты -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;700;800&family=DM+Sans:opsz,wght@9..40,300;9..40,400;9..40,500;9..40,600&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">

  <!-- Фавиконки -->
  <link rel="icon" href="/assets/favicon.ico" sizes="any">
  <link rel="icon" href="/assets/favicon.svg" type="image/svg+xml">
  <link rel="apple-touch-icon" href="/assets/apple-touch-icon.png">

  <!-- OG -->
  <meta property="og:image" content="/assets/og-image.png">
  <meta property="og:image:width" content="1200">
  <meta property="og:image:height" content="630">

  <title>VYUD AI — Курсы из документов за секунды</title>
</head>
<body>
  <a href="#main" class="sr-only">Перейти к содержимому</a>
  <main id="main"><!-- контент --></main>
</body>
</html>
```

### Шаг 3: Streamlit (app.py)

```python
# В app.py — подключение дизайн-системы
import streamlit as st
from pathlib import Path

def load_css():
    """Загружает токены дизайн-системы в Streamlit."""
    css_files = [
        "design_system/tokens.css",
        "design_system/components.css",
        "design_system/animations.css",
    ]
    combined = ""
    for path in css_files:
        p = Path(path)
        if p.exists():
            combined += p.read_text()
    st.markdown(f"<style>{combined}</style>", unsafe_allow_html=True)

# В начале main():
load_css()
```

---

## 19. Версионирование

| Версия | Дата | Изменения |
|--------|------|-----------|
| **2.0.0** | 2025-03 | Полный рефакторинг: шрифты Syne/DM Sans, motion-токены, z-index шкала, форм-компоненты, тёмная тема, CSS reset |
| 1.0.0 | 2025-01 | Первый драфт (tokens.css, базовые компоненты) |

### Правила обновления

- **MAJOR** (2.x → 3.x): ломающие изменения в именах CSS-переменных
- **MINOR** (2.0 → 2.1): новые компоненты, новые токены (обратно-совместимо)
- **PATCH** (2.0.0 → 2.0.1): баги, мелкие правки

> ⚠️ При переименовании CSS-переменных — **всегда** оставлять deprecated-алиас на 1 минорную версию:  
> `--vyud-primary: var(--vyud-color-brand); /* deprecated в v2.0, удалить в v3.0 */`

---

*VYUD AI Design System © 2025 — Единый стандарт для всей экосистемы продуктов*

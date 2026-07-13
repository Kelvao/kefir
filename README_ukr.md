# 🥛 Kefir

<div align="center">
  <img src="logo.png" alt="Logo" width="400">
  <br><br>
  <a href="https://github.com/rashevskyv/kefir/releases"><img src="https://img.shields.io/github/downloads/rashevskyv/kefir/total.svg" alt="Github latest downloads"></a>
  <a href="https://github.com/rashevskyv/kefir/releases/latest"><img src="https://img.shields.io/github/v/release/rashevskyv/kefir" alt="Latest release"></a>
  <a href="https://github.com/rashevskyv/kefir/stargazers"><img src="https://img.shields.io/github/stars/rashevskyv/kefir" alt="Stars"></a>
  <br>
  <a href="README.md"><img src="https://img.shields.io/badge/Language-English-blue" alt="README English"></a>
</div>

## Що таке Kefir

Kefir — це готовий до використання пакет, створений на базі модифікованого Atmosphère, hekate та мінімального рекомендованого набору homebrew і модулів, які попередньо налаштовані для спільної роботи. Він існує для того, щоб спростити встановлення та обслуговування програмного забезпечення на зламаній Nintendo Switch.

**Kefir не є прошивкою!** Це збірка, яка об'єднує Atmosphère з додатковими інструментами.

Основні відмінності від оригінального Atmosphère:

- Версіонування Kefir відповідає версіонуванню системи, тому ви можете дізнатися, що саме встановлено, просто за номерами версій.
- Драйвер карток пам'яті exFAT встановлюється за замовчуванням під час оновлення системи.
- Патчі сигнатур (через [sys-patch](https://github.com/borntohonk/sys-patch)) для запуску непідписаних homebrew/ігор.
- Автоматичний дамп ключів під час завантаження: Kefir перевіряє версії sysNAND/emuNAND і автоматично та непомітно витягує ключі з найновішої.
- Системне логування вимкнено, що дозволяє уникнути засмічення картки пам'яті та зайвих записів.
- Опціональне переспрямування збережень із внутрішньої пам'яті на картку пам'яті під час використання emuNAND, що знижує ризик втрати збережень у разі збою emuNAND.

## Навіщо потрібен Kefir?

Мета — спростити життя користувачеві: з рекомендованою версією системи + останньою версією Kefir усе має просто працювати — це контрольоване середовище, яке легко відтворити. Знаючи версію системи та версію Kefir, цього достатньо, щоб приблизно розуміти, що встановлено на консолі.

## Сумісність

Повна підтримка прошивок до **22.1.0** включно.

> ⚠️ Старий патч для підтримки застарілих homebrew більше не працює. Якщо старий homebrew перестав працювати, пропатчте його наново через [hbpatcher.alula.me](https://hbpatcher.alula.me/).
>
> Старий форвардер HBMenu також запускатиметься з помилкою. Перевстановіть його через DBI як "гру", використовуючи файл `games/Homebrew menu [03DB12780BD84000][v0].nsp`. Альтернатива без форвардера: запустіть програму **Album**, утримуючи кнопку **R**, поки не завантажиться HBMenu. Деталі: [switch.customfw.xyz/hbl](https://switch.customfw.xyz/hbl).

## Склад Kefir

1. **[Kefirosphere](https://github.com/rashevskyv/Kefirosphere)** — форк [Atmosphère](https://github.com/Atmosphere-NX/Atmosphere).
2. **[sys-patch](https://github.com/borntohonk/sys-patch)** — патчі сигнатур, що дозволяють запускати непідписані (читай: піратські) програми та ігри.
3. **Завантажувач [hekate](https://github.com/CTCaer/hekate)** — boot-меню, бекап/відновлення NAND, створення EmuNAND, монтування картки до ПК без виймання з консолі, перерозмітка та інше.
4. **Встановлені пейлоади**:
   - [Lockpick_RCM](https://codeberg.org/rashevskyv/Locktrick/) — робить дамп ключів консолі.
   - [TegraExplorer](https://github.com/rashevskyv/TegraExplorer/) — файловий менеджер у вигляді пейлоаду (в стилі GodMode9, для Switch).
5. **Встановлені homebrew**:
   - [DBI](https://github.com/rashevskyv/dbi) — встановлення ігор через USB або з картки пам'яті.
   - [Tinfoil](http://tinfoil.io) — завантаження ігор безпосередньо через мережу.
   - [Kefir Updater](https://github.com/rashevskyv/kefir-updater) — оновлення Kefir через інтернет.
   - [Sphaira](https://github.com/ITotalJustice/sphaira/releases/) — середовище для запуску homebrew, завантаження тем/додатків, файловий менеджер.
   - [Daybreak](https://github.com/Atmosphere-NX/Atmosphere/tree/0.14.1/troposphere/daybreak) — безпечне оновлення прошивки системи.
   - [NXThemes Installer](https://github.com/exelix11/SwitchThemeInjector) — менеджер кастомних тем.
   - [Linkalho](https://github.com/rdmrocha/linkalho) — прив'язка акаунтів.
6. **Встановлені модулі** (не підтримуються на SX OS):
   - [sys-con](https://github.com/o0Zz/sys-con) — підключення Xbox-сумісних/звичайних контролерів через USB.
   - [Mission Control](https://github.com/ndeadly/MissionControl) — підключення контролерів через Bluetooth.
   - **[Ultrahand-Overlay](https://github.com/ppkantorski/Ultrahand-Overlay)** — системний оверлей із підтримкою кастомних скриптів/модулів (замінив старий Uberhand: швидший і гнучкіший). Активація: **(L) + хрестовина вниз + (R3)**.
     - Скрипти: помічник з мови/оновлення **DBI**, **Translate Interface**, **Semi-stock**, **Reboot and Shutdown**.
     - Модулі: [nx-ovlloader](https://github.com/ppkantorski/nx-ovlloader) (оновлений форк, запускає `.ovl`/`.nro` через Tesla Menu), [ovlEdiZon](https://github.com/proferabg/EdiZon-Overlay/releases) (чити), [ovlSysmodules](https://github.com/WerWolv/ovl-sysmodules/) (увімкнення/вимкнення встановлених sys-модулів, наприклад, розгін, emuiibo).

## Встановлення / Оновлення

### Перше встановлення або чиста картка пам'яті

1. Скопіюйте **вміст** архіву `kefir.zip` (зі сторінки [релізів](https://github.com/rashevskyv/kefir/releases)) у корінь картки пам'яті.
2. Вставте картку у Switch.
3. Запустіть (inject) `payload.bin` (є в архіві) за допомогою вашого улюбленого методу злому (наприклад, Fusée Gelée).

### Оновлення Kefir або перехід з іншої збірки

#### Встановлення вручну (будь-яка ОС)

**Підключення картки пам'яті до ПК:**

- Користувачі macOS: дотримуйтесь рекомендованих кроків, щоб уникнути проблем із карткою.
- Консоль вимкнена: вставте картку безпосередньо в ПК.
- Консоль увімкнена:
  1. Перезавантажтеся через меню, яке викликається утриманням кнопки **POWER**.
  2. На екрані заставки Kefir утримуйте **кнопку зменшення гучності (VOL-)**, щоб перейти в hekate.
  3. Вийміть картку з консолі та вставте її в ПК.

> Виймання картки в меню hekate не вимагає повторного запуску пейлоаду — просто вставте картку назад і завантажтеся через **Launch**.

**Встановлення Kefir:**

1. Скопіюйте **вміст** архіву `kefir.zip` у корінь картки.
2. Вставте картку назад у Switch.
3. В **hekate**: **More configs → Update Kefir**.
4. Після завершення консоль завантажиться безпосередньо у прошивку.

> Альтернатива: вимкніть консоль, замініть файли на витягнутій картці, вставте її назад і увімкніть консоль — скрипт оновлення запуститься автоматично.

#### Оновлення безпосередньо на консолі (Kefir 529+)

1. Запустіть HBL.
2. Виберіть **Kefir Updater** (потрібен інтернет).
3. **Update Kefir → Kefir [версія] → Download**.
4. Дочекайтеся завантаження/розпакування, натисніть **Continue**. Консоль перезавантажиться в пейлоад і виконає встановлення.
5. Після завершення натисніть будь-яку кнопку для завантаження прошивки.

#### Чисте встановлення (рекомендується у разі виникнення помилок)

1. Видаліть усе на картці, окрім папок `Nintendo` та `emummc`, якщо вони є.
2. Встановіть будь-яким із методів вище.

#### Debug-встановлення (якщо чисте встановлення не допомогло)

1. Скопіюйте `Nintendo` та `emummc` на ПК.
2. Відформатуйте картку у FAT32 і скопіюйте папки назад.
3. Виконайте звичайне встановлення.

### Вирішення проблем

Помилка `[NOFAT]` або `kefir-updater` не працює? Використовуйте `install.bat`:

1. Розпакуйте `kefir.zip` будь-де **на ПК** (ніколи не робіть цього на картці консолі).
2. Вставте картку в ПК.
3. Запустіть `install.bat` з розпакованої папки та вкажіть букву диска вашої картки.
4. Дочекайтеся завершення копіювання.
5. Вставте картку в консоль і завантажтеся.

> Помилка "**Is BEK missing**"? Вимкніть консоль і увімкніть її знову.

## Запуск Atmosphère

Консоль не бачить картку / просить оновити прошивку / зависає на чорному екрані після логотипу? Відсутні драйвери exFAT — відформатуйте картку у FAT32.

Автозавантаження увімкнено за замовчуванням у hekate, тому меню hekate не з'являтиметься; прошивка запускається одразу. Утримуйте **VOL-** під час екрану заставки, щоб потрапити в меню hekate.

**Важливо:**

- Перезавантаження в hekate здійснюється безпосередньо зі звичайного меню перезавантаження прошивки — просто утримуйте **VOL-** під час заставки Kefir.
- Отримати доступ до картки без її виймання з консолі можна через MTP (**DBI → Run MTP Responder**) або через hekate (працює не в усіх надійно; **ви не можете оновити Kefir через MTP**).
- Встановлення та оновлення Kefir використовують один і той самий процес.
- Помилка "**Is BEK missing**"? Вимкніть консоль і увімкніть її знову.

## Додаткова інформація

- Для налаштування модулів ([sys-con](https://github.com/o0Zz/sys-con), [Mission Control](https://github.com/ndeadly/MissionControl) тощо) використовуйте **Ultrahand-Overlay**: **(L) + хрестовина вниз + (R3)**.
- Переспрямування збережень (emuNAND → картка): увімкніть в **Ultrahand → Settings → Advanced**. Збереження тепер знаходяться безпосередньо в папці вашого emuNAND (більше не в `atmosphere/saves`). Експериментальна функція.
- Дамп ключів тепер автоматичний при кожному завантаженні — ручні дії не потрібні.
- Semi-stock:
  - З самої прошивки: Ultrahand → вправо → `Semi-stock`.
  - Під час завантаження: hekate → `More configs` → `Semi-stock (blackscreen fix)`.
  - Запуск через прошивку вимикає встановлену тему (уникає помилок через розбіжність версій системи/emuNAND).
- Оновлення здійснюються за допомогою утиліти **Kefir Updater**.

### Розгін (Оверклокінг)

- **Увімкнути**: Ultrahand → вправо → `Settings` → `Use overclock`.
- **Вимкнути**: Ultrahand → вправо → `Settings` → `Disable overclock`.

### Режим підтримки 8 ГБ пам'яті

- **Увімкнути**: Ultrahand → вправо → `Settings` → `Enable 8GB support`.
- **Вимкнути**: перевстановіть Kefir.

---

## Підтримати розробника Kefir
### Paypal
[![PayPal](https://github.com/rashevskyv/kefir/assets/18294541/5e8a41b1-a15e-4e2c-a1fc-9230379ca1fa)](https://www.paypal.com/donate/?hosted_button_id=S5BLF972J8G92)

### Банка monobank
[![mono](https://github.com/user-attachments/assets/adc1d908-c511-4e03-8d63-f0370a7752bd)](https://send.monobank.ua/jar/9PwYEXHYbs)

## Пожертвувати на підтримку України
### 🇺🇦 УКРАЇНА ПОТРЕБУЄ ВАШОЇ ДОПОМОГИ ЗАРАЗ!
>
> Я творець цього проєкту, і я українець.
>
> **Моя країна, Україна, [зазнає вторгнення з боку Російської Федерації прямо зараз](https://www.bbc.com/news/world-europe-60504334)**. Я втік з Івано-Франківська і зараз перебуваю в безпеці зі своєю сім'єю в західній частині України. Принаймні поки що.
> Росія завдає ударів балістичними ракетами по цілях по всій моїй країні.
>
> **Будь ласка, врятуйте мене і допоможіть врятувати мою країну!**
>
> Національний банк України відкрив [рахунок для збору коштів на потреби Збройних Сил України](https://bank.gov.ua/en/news/all/natsionalniy-bank-vidkriv-spetsrahunok-dlya-zboru-koshtiv-na-potrebi-armiyi):
>
> ```
> SWIFT Code NBU: NBUA UA UX
> JP MORGAN CHASE BANK, New York
> SWIFT Code: CHASUS33
> Account: 400807238
> 383 Madison Avenue, New York, NY 10179, USA
> IBAN: UA843000010000000047330992708
> ```
> 
> [Фонд "Повернись живим" (savelife.in.ua)](https://savelife.in.ua/)
> 
> ```
> BITCOIN
> bc1qkd5az2ml7dk5j5h672yhxmhmxe9tuf97j39fm6
> 
> ETHEREUM (eth, usdt, usdc)
> 0xa1b1bbB8070Df2450810b8eB2425D543cfCeF79b
> 0x93Bda139023d582C19D70F55561f232D3CA6a54c
> 
> TRC20 (tether)
> TX9aNri16bSxVYi6oMnKDj5RMKAMBXWzon
> 
> Solana (sol)
> 8icxpGYCoR8SRKqLYsSarcAjBjBPuXAuHkeJjJx5ju7a
> ```
>
> Ви також можете зробити пожертву [благодійним організаціям, які підтримують українську армію](https://savelife.in.ua/en/donate/).
>
> **ДЯКУЮ!**
---
создал заметку: 2025-01-27
tags:
  - UEFI_Shell
  - work
  - RDW
  - flash
  - команды
ссылка: https://github.com/tianocore/edk2
---

### 1. **Подготовка файлов для UEFI Shell**

1. **Скачивание UEFI Shell**:
    
    - Перейдите на официальный репозиторий Tianocore: [UEFI Shell](https://github.com/tianocore/edk2).
    - Найдите и скачайте соответствующий файл:
        - Для 64-разрядной системы: `Shell.efi` (обычно в разделе `x64`).
        - Для 32-разрядной системы: `Shell.efi` (обычно в разделе `x86`).
2. **Переименование файла**:
    
    - Переименуйте файл `Shell.efi`:
        - Для 64-bit архитектуры: **BOOTX64.EFI**.
        - Для 32-bit архитектуры: **BOOTIA32.EFI**.


### 2. **Подготовка флешки**

1. **Форматирование флешки**:
    
    - Вставьте флешку в компьютер.
    - Откройте «Управление дисками» (Windows):
        1. Нажмите `Win + R`, введите `diskmgmt.msc` и нажмите Enter.
        2. Найдите флешку, щёлкните по ней правой кнопкой мыши и выберите «Форматировать».
        3. Выберите файловую систему **FAT32** (UEFI поддерживает только FAT32) и нажмите «ОК».
    
    **Или через командную строку**:
    
    1. Откройте командную строку (`cmd`) от имени администратора.
    2. Выполните следующие команды:
```cmd
diskpart
list disk
select disk X  (где X — номер вашей флешки)
clean
create partition primary
format fs=fat32 quick
assign
exit
```

        
2. **Создание структуры директорий**:
    
    - В корне флешки создайте папки:
        `EFI\BOOT`
        
        Например:
        - Если флешка имеет букву `E:`, создайте директорию `E:\EFI\BOOT`.

### 3. **Копирование файла UEFI Shell**

1. Скопируйте файл **BOOTX64.EFI** или **BOOTIA32.EFI** (в зависимости от архитектуры) в папку `EFI\BOOT`.
2. Структура на флешке должна выглядеть так:
```
E:\
├── EFI\
    └── BOOT\
        └── BOOTX64.EFI (или BOOTIA32.EFI)
```


### 4. Загрузиться в флеш через bootmenu, etc

Для навигации:
- Введите команду `map -r`, чтобы увидеть список доступных файловых систем (например, `fs0`, `fs1` и т.д.).
- Перейдите в нужный раздел (обычно флешка — это `fs0`):
- Проверьте содержимое директории: `ls` or `dir`
#### Команды:
- `edit` - изменить/просмотреть файл
- `fs0:` - Выбрать директорию (например, флеш)
- `help` - help

#### Работа с переменными (`перепроверить!`):
- `set MyVar=<name>` - создать переменную
- `echo %MyVar%` - вывести
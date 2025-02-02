---
создал заметку: 2025-01-27
tags:
  - UEFI_Shell
  - RDW_A520
  - fields
  - поля
  - прошивка_полей
  - amideefix64_efi
---
## Директория:
![[Pasted image 20250127174233.png]]
## Что нужно сделать:
1) Загрузиться с нужной флешки в UEFI Shell
2) Выбрать нужную флешку (`map` в помощь):
```uefi
fs0:
```
3) Создать переменную `a`:
- Написать:
```uefi
set a=
```
- Пикнуть или ввести серийный номер готовой продукции RDW
4) Запустить скрипт `flash.nsh`:
```uefi
flash.nsh
```
1) __Смотреть и ждать. Потом проверить BIOS__


## Опционально:
- Скрипт flash.nsh:
```nsh
@echo -off
echo "Serial Number:"
set a

amideefix64.efi /SS %a%

amideefix64.efi /BP "RDW A520"
amideefix64.efi /SM "RDW Computers"
amideefix64.efi /SP "RDW Kama-06"
amideefix64.efi /CT "0D"

echo "Done"

pause
```

> [!WARNING]
> Перед запуском, нужно сменить поля в этом файле на нужные!
> Где, `/CT` - тип устройства (mini PC, All in One, Desctop Case, Notepad)

`TODO: сопоставить типу - 0х код`
>
---
создал заметку: 2025-01-27
tags:
  - UEFI_Shell
  - nsh
  - startup_nsh
  - AfuEfix64_efi
  - amideefix64_efi
  - скрипты
ссылка: obsidian://open?vault=obsidian_base&file=RDW%20Work%2FUEFI%20Shell%2FUEFI%20Shell
---
## [[UEFI Shell]] .nsh

#### _Директория_:
![[Pasted image 20250127172448.png]]
#### ___f.nsh____:
- запускает скрипт, который взаимодействует с полями материнской платы:
```uefi
AfuEfix64.efi 752D3020007_RDW.bin /p /b /n /x /l /k
```

#### ___startup.nsh___:
- Скрипт автостарта (будет запускаться сразу при запуске)
- Дает 5 секунд на отмену автозапуска (нажать любую клавишу для отмены автостарта)
- Скрипт startup.nsh в данном примере запускает `f.nsh`
```uefi
fs0:
\f.nsh
```


#### AfuEfix64.efi
- Программа для прошивки BIOS

#### 752D3020007_RDW.bin
- BIOS для материнской платы RDW A520

#### amideefix64.efi
- Программа для прошивки полей BIOS


#### Прошивка полей BIOS
###### Разбор на случае прошивки полей RDW A520
```uefi
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
> Обязательно!
> Перед запуском __flash.nsh__ [нужно инициализировать переменную __`<a>`__ вручную в UEFI Shell!](obsidian://open?vault=obsidian_base&file=RDW%20Work%2FUEFI%20Shell%2F%D0%9F%D1%80%D0%BE%D1%88%D0%B8%D0%B2%D0%BA%D0%B0%20%D0%BF%D0%BE%D0%BB%D0%B5%D0%B9%20RDW%20A520%20UEFI%20Shell)
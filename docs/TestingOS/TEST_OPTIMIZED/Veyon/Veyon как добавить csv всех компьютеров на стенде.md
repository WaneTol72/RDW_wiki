---
создал заметку: 2025-01-27
tags:
  - RDW
  - work
  - Veyon
  - ip
  - csv
  - import
  - export
  - cmd
ссылка: https://docs.veyon.io/ru/latest/admin/cli.html#network-object-directory
---
## Как добавить csv файл со всеми ip
1) Добавить в PATH папку с Veyon
2) Открыть cmd от админа
3) Ввести: 
```cmd
veyon-cli networkobjects import C:\Users\Test\PycharmProjects\Veyon\Create_csv_file_with_ip\ip_for_stend_3.csv location "Stend_3" format "%type%;%name%;%host%;"
```
`Где`:
- _Stend_3_ - Имя группы адресов
- _%type%;%name%;%host%;_ - Формат `csv` файла
- _Путь: "C:\Users\Test\PycharmProjects\Veyon\Create_csv_file_with_ip\ip_for_stend_3.csv"_ - Путь к csv файлу

## Export csv файла
```cmd
veyon-cli networkobjects export computers.csv location workstend3 format "%type%;%name%;%host%;%mac%"
```
`Где`:
- _location_ - Имя группы адресов
- _export_ `<path>` - Куда сохраняем файл
- _%type%;%name%;%host%;_ - Формат `csv` файла


> [!Примечание]
> Если добавлять csv файл через .bat - нужно в PATH ставить вместо '%' -> '%%'
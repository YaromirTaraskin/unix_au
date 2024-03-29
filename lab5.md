# Лабораторная работа №5. 
## Разграничение прав доступа в ОС UNIX. Списки контроля доступа.

### Основные понятия:

+ запись списка контроля доступа

### Используемые команды:

+ `getfacl`	- Просмотр списка контроля доступа для файла или каталога
+ `setfacl`	- Установка списка контроля доступа для файла или каталога

### Задание.

> 1.Создайте подкаталог shared в вашем домашнем каталоге. Узнайте имя пользователя вашего одногруппника, сидящего за соседним компьютером.

```bash
mkdir -v shared
```

> 2.Создайте файл doc1.txt в новом каталоге. Проверьте стандартные права доступа к файлу. Используя списки контроля доступа, дайте вашему соседу права на чтение созданного файла.

```bash
touch ~/shared/doc1.txt
```

> 3.Проверьте, что сосед может получить доступ к созданному файлу. В чем может быть причина, если ему не удалось открыть файл?

```bash
getfacl ~/shared/doc1.txt
```

> 4.Договоритесь с соседним пользователем о создании общего каталога. Настройте списки контроля доступа по умолчанию для каталога shared так, чтобы ваш сосед мог создавать новые файлы в нем и иметь права на их чтение и запись.

```bash
setfacl -m default:u:neigbor:rw ~/shared
```

> 5.Попросите соседа создать файл file1.txt и записать в него строку «This text is created by user1». Откройте созданный им файл и допишите в него вторую строку «This text is added by user2».

Сосед внутри моей папки ~/shared/
```bash
echo "This text is created by user1" > file1.txt
```

затем я:
```bash
echo "This text is added by user2" >> ~/shared/file1.txt
```


